# GET /api/auth/verify-email

## Evidence
- [dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthController.java](dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthController.java#L66-L69)
- [dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthService.java](dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthService.java#L127-L138)

## Steps
1. AuthController recebe o token por query parameter.
2. AuthService busca o usuário pelo token de verificação.
3. Valida expiração, marca o e-mail como verificado e limpa o token.
4. Retorna MessageResponse com 'Email verified'.

## Errors
- **Token inexistente ou expirado** — HTTP 401 — [dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthService.java](dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthService.java#L129-L134)

## Dependencies
- UserRepository
- Banco de dados relacional

## Config
- `app.base-url`: usado na geração do link enviado por e-mail
- `app.auth.verification-token-ttl`: não existe como configuração; TTL fixo de 24 horas no código

## Participants
- AuthController
- AuthService
- UserRepository

## Unknowns
- {}
