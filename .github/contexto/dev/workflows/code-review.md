# Contexto para gerar workflow do code review para skill dev

## code review

1. este workflow deve ser acionado quando usuario pedir um code-review de uma feature branch `feature/alguma-coisa` de um `<microserviço>`;
2. deve ter uma historia relacionada para gerar um `code-review` em `dominios/<projeto>/historias/<jira-id>/<jira-id>.md`;
3. o agente deve ler a historia;
4. o analista do agente deve comparar a branch `main` com a `feature/branch` especificada para saber o que foi desenvolvido;
5. de posse da analise do que foi desenvolvido, confrontar com a historia `dominios/<projeto>/historias/<jira-id>/<jira-id>.md` para validar os critérios de aceite e definções de pronto;
6. Estando de acordo, com informação suficiente, analise concluída, o agente encerra notificando o usuario que o code-review foi realizado com sucesso e que atende a historia;
7. Em caso de divergencia, o agente chama o analista para apontar as pendencias de desenvolvimento, testes unitários; demais implementações necessárias para atender a historia;
