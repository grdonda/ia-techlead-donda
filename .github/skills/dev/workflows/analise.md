# Análise DEV de Sistema

1. Confirme projeto, história, task ou serviço, repositório autorizado e autorização de leitura.
2. Leia a história e os artefatos mais recentes dentro de `dominios/<projeto>/historias/<JIRA-ID>/`.
3. Leia `dominios/<projeto>/contexto/` somente quando a análise exigir informação do projeto e avise o usuário antes.
4. Use o `dev-analista` para analisar apenas o repositório autorizado: versões, configurações, controllers, clients, services, repositories, fluxo de dados, riscos e observabilidade.
5. Entregue os achados ao `dev-operador` para registrar o asset [analise.md](../assets/analise.md) em `dominios/<projeto>/historias/<JIRA-ID>/contexto/<JIRA-ID>_analise-dev.md`.
6. Marque o artefato como `concluído`, `aguardando usuário` ou `bloqueado`, atualize a data e pare.

## Saida

Informe o caminho do artefato persistido e as pendencias remanescentes.
