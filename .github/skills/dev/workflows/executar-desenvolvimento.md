# Desenvolvimento de Task DEV

## Objetivo

Implementar somente a Task DEV autorizada, dentro do escopo definido pela história e pela análise.

## Processo

1. Confirme projeto, história, Task DEV, repositório, ambiente e autorização explícita.
2. Leia a história, refinamento, estudos necessários e Task DEV.
3. Leia `dominios/<projeto>/contexto/` somente quando exigido e avise o usuário antes.
4. Use o `dev-analista` para levantar arquivos, impactos, contratos, riscos e critérios de validação.
5. Se o fluxo necessário não estiver conhecido, execute `executar-mapeamento-fluxo.md` e retorne ao desenvolvimento.
6. Use o `dev-operador` para implementar o escopo autorizado.
7. Use o `dev-operador` para registrar o resultado em:

`dominios/<projeto>/historias/<JIRA-ID>/contexto/<JIRA-ID>_desenvolvimento.md`

## Regras

* Não implemente sem Task DEV e autorização explícita.
* Não altere comportamento, contrato ou arquivos fora do escopo necessário.
* Não invente requisitos ou dependências.
* Registre somente testes, observabilidade, riscos e evidências confirmados.

## Saída

Atualize a Task DEV e o artefato com:

* implementação;
* testes;
* observabilidade;
* riscos;
* pendências;
* `status`;
* `data-atualizacao`;
* `responsavel`.

Status:

* `concluído`
* `aguardando usuário`
* `bloqueado`
