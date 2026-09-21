# Criar Task DEV para o Jira

Objetivo: separar o as-is e o to-be já levantados na análise DEV em tarefas de implementação para os devs, unificadas ou não, como etapas pós-análise. Este workflow não reanalisa o repositório.

1. Confirme o projeto, a historia de origem, o SRV ou LIB, o repositorio autorizado e a solicitacao do usuario.
2. Leia a historia local e, quando existirem, o refinamento, a CSD, os contratos, os estudos, o contexto e as tasks Jira relacionadas.
3. Exija a analise DEV existente ([analise.md](../assets/analise.md)) com as-is e to-be levantados; se estiver ausente ou desatualizada, marque `bloqueado` e solicite a execucao do workflow de analise antes de prosseguir.
4. Separe as alteracoes tecnicas necessarias (to-be) da analise em tarefas de implementacao, unificadas ou divididas por componente ou etapa, preservando o conteudo tecnico ja levantado.
5. Se houver duvida ou lacuna que impeça uma task DEV consistente, marque o artefato como `bloqueado` ou `aguardando usuário` e solicite a informacao necessária.
6. Entregue as tarefas ao `dev-operador` para criar ou atualizar a task DEV em `dominios/<projeto>/historias/<JIRA-ID>/tasks/Task 00N - DEV - <TITULO>.md`.
7. Prepare o conteúdo técnico para o Jira dentro da task DEV, sem criar história derivada ou task Jira do TechLead.
8. Atualize status, data, responsavel, evidencias e pendencias; marque `concluído` e pare.

## Regras

- O workflow e assincrono e independente do workflow do TechLead; ambos dependem da história para análise.
- A task DEV deve iniciar em `Task 001 - DEV - <TITULO>.md` e seguir `N + 1`.
- Refinamento, CSD e estudos complementares reforcam o contexto, mas nao sao bloqueios quando a historia estiver clara.
- Se existir dependencia entre skills, informe o usuario e pergunte se deve prosseguir ou aguardar.
- Nao publique no Jira nem execute operacoes externas sem autorizacao explicita.
