# POST /api/auth/logout

## Evidence
- [dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthController.java](dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthController.java#L57-L63)
- [dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthService.java](dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthService.java#L119-L124)
- [dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/config/SecurityConfig.java](dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/config/SecurityConfig.java#L47-L50)

## Steps
1. SecurityFilterChain exige autenticação.
2. AuthController obtém o JWT das credenciais autenticadas.
3. AuthService adiciona o identificador do JWT à blacklist pelo tempo restante e revoga os refresh tokens do usuário.
4. Retorna MessageResponse com 'Logged out'.

## Errors
- **Autenticação ausente ou token inválido** — HTTP 401 — [dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/config/SecurityConfig.java](dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/config/SecurityConfig.java#L68-L71)

## Dependencies
- JwtAuthenticationFilter
- TokenBlacklistService
- Redis
- RefreshTokenRepository
- Banco de dados relacional

## Config
- `app.jwt.secret`: configurado externamente; valor omitido
- `spring.data.redis.host`: host do Redis
- `spring.data.redis.port`: porta do Redis

## Participants
- SecurityFilterChain
- JwtAuthenticationFilter
- AuthController
- AuthService
- TokenBlacklistService
- RefreshTokenRepository

## Unknowns
- {}
# Fluxo — POST /api/auth/logout

## Objetivo

Revogar os refresh tokens do usuário autenticado e registrar o access token na blacklist.

## Entrada

* `POST /api/auth/logout`
* Authorization: `Bearer <access_token>`

## Flowchart

```mermaid
flowchart TD
    SecurityFilterChain["SecurityFilterChain"] --> JwtAuthenticationFilter["JwtAuthenticationFilter"]
    JwtAuthenticationFilter --> JwtService["JwtService"]
    JwtAuthenticationFilter --> TokenBlacklistService["TokenBlacklistService"]
    JwtAuthenticationFilter --> AuthController["AuthController"]
    AuthController --> AuthService["AuthService"]
    AuthService --> TokenBlacklistService["TokenBlacklistService"]
    AuthService --> RefreshTokenRepository["RefreshTokenRepository"]
    AuthController --> MessageResponse["MessageResponse"]
    JwtAuthenticationFilter --> AuthenticationEntryPoint["AuthenticationEntryPoint"]
    AuthService --> GlobalExceptionHandler["GlobalExceptionHandler"]
```

## Sequence

```mermaid
sequenceDiagram
    participant SecurityFilterChain as SecurityFilterChain
    participant JwtAuthenticationFilter as JwtAuthenticationFilter
    participant JwtService as JwtService
    participant TokenBlacklistService as TokenBlacklistService
    participant AuthController as AuthController
    participant AuthService as AuthService
    participant RefreshTokenRepository as RefreshTokenRepository
    participant MessageResponse as MessageResponse
    participant AuthenticationEntryPoint as AuthenticationEntryPoint
    participant GlobalExceptionHandler as GlobalExceptionHandler

    SecurityFilterChain->>JwtAuthenticationFilter: POST /api/auth/logout
    JwtAuthenticationFilter->>JwtService: decode(bearer token)
    JwtAuthenticationFilter->>TokenBlacklistService: isBlacklisted(token)
    JwtAuthenticationFilter->>AuthController: authentication com Jwt como credencial
    AuthController->>AuthService: logout(jwt)
    AuthService->>TokenBlacklistService: blacklist(jti)
    AuthService->>RefreshTokenRepository: revokeAllByUserId(subject)
    AuthController->>MessageResponse: retorna Logged out

    alt Autenticação ausente, token inválido, expirado ou em blacklist
        JwtAuthenticationFilter-->>AuthenticationEntryPoint: Unauthorized
    else Exceção não tratada
        AuthService-->>GlobalExceptionHandler: Internal Server Error
    end
```

## Dependências

* Redis via StringRedisTemplate para blacklist
* PostgreSQL via RefreshTokenRepository

## Saída

* `MessageResponse`
* `HTTP 401 Unauthorized`
* `HTTP 500 Internal Server Error`

## Pontos desconhecidos

* `authentication_credentials_runtime`: A criação completa do Authentication depende da decodificação bem-sucedida do JWT e dos claims recebidos.
* `database_runtime_values`: A conexão PostgreSQL efetiva depende de configuração externa.
