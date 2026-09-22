# Mapeamento de Fluxo

## Objetivo

Mapear os fluxos funcionais principais das portas de entrada solicitadas e gerar um artefato individual por fluxo.

O resultado deve explicar:

```text
o que entra
→ por onde entra
→ quem recebe
→ quem orquestra
→ quem é chamado
→ o que retorna
→ o que sai
```

O fluxo funcional e os aspectos transversais devem permanecer separados.

## Execução Fechada

Este workflow é uma operação fechada.

Ao ser explicitamente executado pelo usuário:

1. analisar;
2. gerar Modelo Factual;
3. persistir artefato;
4. validar;
5. reportar;
6. encerrar.

Não criar:

- TODOs;
- tarefas;
- arquivos de evidência;
- arquivos auxiliares;
- próximas atividades.

Não perguntar:

- se deve persistir;
- se deve extrair evidências;
- se deve continuar;
- se deve criar outro arquivo;
- se deve executar uma etapa posterior.

Não apresentar “próximo passo”.

Somente interromper por bloqueio real.

## Autorização

A execução explícita deste workflow autoriza:

- leitura do SRV autorizado;
- análise dos fluxos;
- criação/atualização dos artefatos de estudo;
- validação dos artefatos.

Não autoriza:

- alteração de código;
- criação de Tasks DEV;
- geração de contratos;
- geração de CURL;
- E2E;
- remoção destrutiva de artefatos.

## Processo

1. Confirme o SRV autorizado.
2. Identifique as portas de entrada dentro do escopo.
3. Para cada porta:
   1. identifique a identidade canônica;
   2. identifique o grupo funcional;
   3. identifique o caminho canônico;
   4. delegue a análise ao `dev-analista`;
   5. receba um único Modelo Factual;
   6. aplique reconciliação;
   7. delegue persistência ao `dev-operador`;
   8. confirme o arquivo criado/atualizado;
   9. valide o resultado.
4. Conclua todos os fluxos possíveis dentro do escopo.
5. Produza um resumo consolidado.
6. Pare.

## Portas de Entrada

Para microserviço:

- endpoint HTTP;
- consumer;
- listener;
- evento;
- job.

Para biblioteca Java/Spring Boot:

- método público;
- interface pública;
- API pública;
- bean funcional;
- integração pública;
- callback/handler público;
- outro ponto de entrada efetivamente utilizável pela aplicação consumidora.

Não assumir que todo projeto possui Controller.

## Identidade Canônica

### HTTP

`<método HTTP> <rota normalizada>`

Exemplo:

```text
POST /api/auth/login
```

### Consumer / Listener

Usar combinação de:

- tópico/fila;
- evento;
- grupo;
- handler.

### Evento

Usar:

- tipo;
- consumidor/handler.

### Job

Usar:

- identificador;
- trigger.

### Biblioteca

Usar:

- classe/interface pública;
- método público;
- operação funcional.

A identidade deve representar a porta de entrada real.

## Organização

Formato:

```text
estudos/
└── <srv-ou-biblioteca>/
    ├── <grupo-funcional>/
    │   └── <fluxo>.md
    └── _transversal/
```

### Microserviço

Exemplo:

```text
estudos/microservice_auth_java/auth/login.md
estudos/microservice_auth_java/auth/refresh.md
estudos/microservice_auth_java/auth/logout.md
estudos/microservice_auth_java/users/me.md
```

### Grupo Funcional

Para HTTP, derivar preferencialmente da rota.

Exemplo:

```text
/api/auth/login
→ auth

/api/users/me
→ users
```

Não usar o nome da classe como agrupamento quando a rota fornecer contexto funcional mais preciso.

Não inventar grupo.

## Nome do Artefato

Preferir:

```text
login.md
refresh.md
logout.md
register.md
verify-email.md
forgot-password.md
reset-password.md
me.md
```

Não usar prefixos numéricos como requisito.

## Descoberta

Mapear apenas portas de entrada.

Não criar fluxos para:

- Service;
- Use Case;
- Repository;
- Component;
- Filter;
- Interceptor;
- Rate Limit;
- Auditoria;
- Migration;
- Configuration;
- Bean de infraestrutura;
- SecurityConfig;
- RedisConfig;
- Actuator;
- Swagger;
- OpenAPI.

Esses elementos podem aparecer no contexto transversal quando relevantes.

## Core Funcional

Priorizar:

```text
Client
→ porta de entrada
→ Controller/Handler/API pública
→ Service/Use Case
→ colaboradores necessários
→ persistência/integração necessária
→ retornos
→ porta de saída
→ Client
```

Não exigir que toda implementação siga exatamente esse desenho.

## Retornos

Toda chamada síncrona relevante deve ter seu retorno mapeado quando confirmado.

Exemplo:

```text
AuthService
→ UserRepository
← User

AuthService
→ JwtService
← AccessToken

AuthService
→ RefreshTokenRepository
← persistência confirmada

AuthService
→ AuthController
← TokenResponse

AuthController
→ Client
← HTTP 200
```

O `sequence` deve refletir essas idas e voltas.

## DTOs e Entidades

Não são participantes do sequence por padrão.

Podem aparecer como:

- payload;
- argumento;
- resultado;
- resposta.

## Aspectos Transversais

Registrar separadamente quando relevantes.

Exemplos:

- Filter;
- SecurityFilterChain;
- RateLimit;
- GlobalExceptionHandler;
- Configuration;
- Bean;
- observabilidade;
- tracing;
- métricas.

Não colocar automaticamente antes do Controller.

## Erros

Separar:

### Fluxo principal

```text
entrada
→ processamento
→ retorno
→ saída
```

### Caminho de erro

```text
operação
→ erro/exceção confirmado
→ tratamento/propagação confirmado
→ resposta
```

Não simular chamadas inexistentes entre Service e ExceptionHandler.

## Evidência

A evidência deve ser coletada durante a análise.

Não criar:

```text
evidencias/
```

por iniciativa própria.

Não criar arquivo separado para trechos de método.

Cada fato relevante deve possuir referência no Modelo Factual.

O artefato final usa essas referências sem criar uma segunda etapa.

## Configuração

Configuração pode complementar evidência.

Configuração isolada não prova execução.

Exemplo:

```text
application.yml
→ configura Redis
```

não prova:

```text
fluxo login → Redis
```

O uso deve ser confirmado pelo código.

## Segredos

Nunca reproduzir valores de:

- secrets;
- passwords;
- tokens;
- JWT secrets;
- API keys;
- private keys;
- credenciais;
- connection strings sensíveis.

Registrar somente:

```text
configuração existente em <arquivo>; valor omitido por segurança.
```

## Reconciliação

### Caminho Canônico

O caminho canônico tem prioridade.

Exemplo:

```text
estudos/microservice_auth_java/auth/login.md
```

### Atualizar

Atualizar integralmente quando:

- existir exatamente um artefato correspondente;
- a identidade canônica for igual.

### Legado

Se existir:

```text
estudos/microservice_auth_java/02-post-api-auth-login.md
```

e o canônico for:

```text
estudos/microservice_auth_java/auth/login.md
```

então:

1. não usar o legado como fonte factual;
2. gerar/atualizar o canônico;
3. preservar o legado;
4. registrar `artefato legado não removido`.

### Conflito

Quando houver:

- múltiplos candidatos;
- identidade incompatível;
- ambiguidade;

não escolher automaticamente.

Retornar:

`aguardando decisão`.

### Remoção

Não remover artefatos automaticamente.

Remoção exige autorização explícita.

## Persistência

Para cada fluxo:

1. determinar identidade;
2. determinar grupo;
3. determinar caminho;
4. aplicar reconciliação;
5. receber Modelo Factual;
6. delegar ao `dev-operador`;
7. confirmar existência do arquivo;
8. validar o arquivo;
9. registrar resultado.

O Operador não pode decidir outro caminho.

## Critério de Conclusão

O fluxo individual só está concluído quando:

- Modelo Factual recebido;
- artefato persistido;
- arquivo confirmado no caminho esperado;
- estrutura validada;
- flowchart válido;
- sequence válido;
- retornos confirmados presentes;
- core separado de transversal;
- nenhuma informação sensível exposta.

O workflow inteiro só está concluído quando todos os fluxos possíveis do escopo forem processados ou explicitamente bloqueados.

## Bloqueios

Bloquear somente por:

- contexto insuficiente;
- porta de entrada não determinável;
- conflito de artefatos;
- caminho impossível de determinar;
- requisito estrutural não atendido;
- parser Mermaid real indisponível;
- falha de persistência;
- outro impedimento efetivo.

Não transformar qualquer incerteza em nova tarefa.

## Execução em Massa

Quando vários fluxos forem encontrados:

- cada fluxo é independente;
- cada fluxo possui seu próprio Modelo Factual;
- cada fluxo possui seu próprio artefato;
- um bloqueio não invalida os demais;
- preservar ordem das portas identificadas;
- não misturar informações entre fluxos.

## Regras

- mapear portas de entrada;
- priorizar core funcional;
- separar transversal;
- preservar retornos;
- não inventar;
- não alterar código;
- não criar arquivos auxiliares;
- não criar TODOs;
- não criar atividades futuras;
- não perguntar para continuar;
- não gerar contratos;
- não gerar CURL;
- não gerar E2E;
- não remover artefatos sem autorização;
- não expor segredos;
- não usar artefato antigo como fonte factual.

## Saída

### Individual

```text
Fluxo: <identidade>
Grupo: <grupo>
Operação: criado | atualizado | bloqueado | aguardando usuário
Arquivo: <caminho>
Status: concluído | bloqueado
Pendências: <somente quando existirem>
```

### Massa

```text
SRV: <srv>
Entradas analisadas: <n>
Criados: <n>
Atualizados: <n>
Bloqueados: <n>
Conflitos: <n>
Legados identificados: <n>
Status: concluído | bloqueado
Pendências: <somente quando existirem>
```

Não incluir “próximo passo”.
