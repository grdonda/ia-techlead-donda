# Análise DEV de Sistema

Objetivo: analisar tecnicamente o SRV ou as libs mencionados na história, cobrindo as-is e to-be, com profundidade suficiente para explicar o contexto ao dev ou ao gerente, questionar riscos e entender impactos.

1. Confirme projeto, história, task ou serviço, repositório autorizado e autorização de leitura.
2. Leia a história e os artefatos mais recentes dentro de `dominios/<projeto>/historias/<JIRA-ID>/`.
3. Leia `dominios/<projeto>/contexto/` somente quando a análise exigir informação do projeto e avise o usuário antes.
4. Use o `dev-analista` para levantar o as-is do repositório autorizado, cobrindo: versões e configurações; contrato de entrada e retorno ao usuário; quem chama o serviço e quem ele chama; controllers, clients, services e repositories; fluxo de processamento com validações, verificações e classificações; comunicação com Redis e Kafka quando houver; riscos e observabilidade.
5. Extraia da história o to-be ao confrontar com o as-is: alteracoes tecnicas necessarias; impactos nos componentes; mudancas de contrato (campo novo, removido, tipo alterado, versionamento, retrocompatibilidade e quem mais e afetado); validacoes adicionais exigidas nos fluxos; mensageria e observabilidade necessarias quando a historia exigir; riscos de uso de bibliotecas (ex.: conversao de datas/timestamp do Jackson).
6. Entregue os achados ao `dev-operador` para registrar o asset [analise.md](../assets/analise.md) em `dominios/<projeto>/historias/<JIRA-ID>/contexto/<JIRA-ID>_analise-dev.md`.
7. Marque o artefato como `concluído`, `aguardando usuário` ou `bloqueado`, atualize a data e pare.

## Saida

Informe o caminho do artefato persistido e as pendencias remanescentes.
