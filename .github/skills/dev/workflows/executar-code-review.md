
# Code Review DEV

Objetivo: validar se o que mudou tecnicamente no código atende à história e ao to-be da análise DEV, quando existir, incluindo observabilidade e mensageria quando houver, e exigir a análise dos testes TDD.

1. Confirme projeto, história, task, branch ou commit e autorização explícita.
2. Leia a história, a análise DEV (as-is/to-be) quando existir, e somente o diff autorizado ou os arquivos especificados no pedido.
3. Use o `dev-analista` para confrontar o diff com a história e com o to-be da análise: identificar bugs, regressões, riscos, divergências de contrato, aderência de observabilidade e mensageria, e lacunas de testes.
4. Exija a análise explícita dos testes TDD implementados; registre ausência ou insuficiência como pendência.
5. Use o `dev-operador` para registrar o resultado no asset [code-review.md](../assets/code-review.md), dentro de `dominios/<projeto>/historias/<JIRA-ID>/code-review/`.
6. Marque o artefato com status, data, responsável e pendências; não altere o código revisado e pare.
