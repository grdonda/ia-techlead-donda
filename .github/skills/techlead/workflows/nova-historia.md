# Nova Historia

1. Confirme o projeto, `<JIRA-ID>` e autorização explícita.
2. Leia `dominios/<PROJETO>/historias/<JIRA-ID>/<JIRA-ID>.md` quando existir e marque `status: em andamento`.
3. Crie `dominios/<PROJETO>/historias/<JIRA-ID>/<JIRA-ID>.md` e os diretórios necessários de contexto, task, teste e code-review.
4. Pergunte se o usuário deseja criar a estrutura canônica: `contexto/anexos/`, `contexto/db/`, `contexto/srvs-contratos/`, `tasks/`, `testes/` e `code-review/`.
5. Crie a estrutura canônica confirmada, marque `aguardando usuário` e registre a data.
6. Pare e aguarde o usuário adicionar o conteúdo da história oficial.

O arquivo da história deve iniciar com:

```yaml
---
projeto: <PROJETO>
jira: <JIRA-ID>
etapa: nova-historia
status: aguardando usuário
data-criacao: <AAAA-MM-DD HH:mm>
data-atualizacao: <AAAA-MM-DD HH:mm>
responsavel: techlead
---
```

## Status

O artefato permanece `aguardando usuário` até a história oficial ser adicionada.
