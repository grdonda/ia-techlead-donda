# Criar Tasks Jira

1. Confirme a autorização explícita e que a história permite compreender as atividades.
2. Leia a task mais recente e marque `status: em andamento`.
3. Leia a história local, o refinamento ou CSD quando existirem e o contexto autorizado.
4. Aplique a regra de distribuição da Sprint: com uma história em desenvolvimento, crie pelo menos quatro tasks paralelas de implementação; com múltiplas histórias, crie uma task de implementação por história.
5. Crie somente tasks Jira para o Jira, usando [task-jira.md](../assets/task-jira.md). Não crie tasks DEV nem histórias derivadas.
6. Nomeie cada arquivo no formato `Task 00N - <TITULO>.md`, iniciando obrigatoriamente em `Task 001 - <TITULO>.md` e incrementando `N + 1` sequencialmente, sem reiniciar ou repetir números.
7. Salve as tasks no diretório `tasks/`, atualize `status`, `data-atualizacao`, `responsavel` e pendências e marque `aguardando usuário`.
8. Se houver dúvida ou lacuna impeditiva, marque `bloqueado` ou `aguardando usuário`, registre a pendência e solicite refinamento ao PM.
9. Pare e aguarde a próxima solicitação; a criação de task DEV é independente e pertence ao fluxo DEV.
