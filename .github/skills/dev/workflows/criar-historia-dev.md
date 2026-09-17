# Criar Historia DEV para o Jira

1. Confirme o projeto, a historia de origem, o SRV ou LIB, o repositorio autorizado e a solicitacao do usuario.
2. Leia a historia local e, quando existirem, o refinamento, a CSD, os contratos, os estudos, o contexto e as tasks Jira relacionadas.
3. Considere a analise DEV existente; se estiver ausente ou desatualizada, use o `dev-analista` para realizar a analise tecnica profunda.
4. Verifique arquitetura, fluxo, contratos, impactos, testes, observabilidade, riscos, resiliencia, consistencia e eficiencia.
5. Se houver duvida ou lacuna que impeça uma historia tecnica consistente, marque o artefato como `bloqueado` ou `aguardando usuário` e solicite a informacao necessária.
6. Entregue os achados ao `dev-operador` para registrar [historia-dev.md](../assets/historia-dev.md) em `dominios/<projeto>/historias/<JIRA-ID>/contexto/<JIRA-ID>_historia-dev.md`.
7. Prepare no campo `Conteudo para o Jira` a historia tecnica DEV, sem criar ou alterar tasks do TechLead.
8. Atualize status, data, responsavel, evidencias e pendencias; marque `concluído` e pare.

## Regras

- O workflow e assincrono e nao depende da criacao de task pelo TechLead.
- Refinamento, CSD e estudos complementares reforcam o contexto, mas nao sao bloqueios quando a historia estiver clara.
- Se existir dependencia entre skills, informe o usuario e pergunte se deve prosseguir ou aguardar.
- Nao publique no Jira nem execute operacoes externas sem autorizacao explicita.
