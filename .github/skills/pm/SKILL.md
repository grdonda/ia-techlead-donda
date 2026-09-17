---
name: pm
description: "Use ao refinar uma história Jira local, organizar sua compreensão, identificar ambiguidades, lacunas, referências ausentes, suposições ou dúvidas e preparar uma CSD para esclarecimento do PM."
argument-hint: "Projeto e JIRA-ID"
user-invocable: true
disable-model-invocation: false
---

# PM

- Refine a história `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md` local.
- Gere a matriz CSD quando houver suposições ou dúvidas.
- Avalie e inventarie os anexos antes do refinamento ou da CSD quando ainda não houver inventário concluído.
- Aguarde instruções para refazer o processo se necessário

## Subagentes

- `pm-analista`: responsável por analisar a história e organizar a informação, identificar suposições, dúvidas.
- `pm-operador`: responsável por garantir que todas as informações analisadas sejam corretamente documentadas.

## Procedimento

1. Confirme o arquivo `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md`; se o projeto ou a história não forem informados, solicite-os antes de prosseguir.
2. Interprete a solicitação:
   - `avaliar anexos`: execute o workflow de avaliação de anexos.
   - `refinamento`: execute o workflow de refinamento.
   - `analisar` ou `CSD`: execute o workflow de CSD.
3. Para `refinamento` ou `CSD`, reutilize o inventário de anexos concluído; se ele não existir, solicite a execução de `avaliar anexos` antes de continuar.
4. No workflow selecionado, acione o `pm-analista` para analisar a história.
5. Entregue a análise do `pm-analista` ao `pm-operador` para preencher e salvar o artefato.
6. Valide a existência do artefato no diretório correspondente e informe ao usuário o término.


## Regras e Limites

- A história `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md` deve existir, é imutável, e não deve ser alterada.
- Mantenha informações não confirmadas classificadas como suposição ou dúvida.
- Siga rigorosamente os formatos e procedimentos definidos nos workflows de refinamento e CSD.
- Não altere o conteúdo da história original `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md`.

## Status e Continuidade

- Leia o artefato mais recente antes de iniciar ou retomar uma etapa.
- Ao iniciar, marque `status: em andamento`; ao depender do usuário, use `aguardando usuário`.
- Use `bloqueado` para pré-requisito ausente e `desatualizado` quando a entrada tiver mudado.
- Ao concluir, marque `concluído`, atualize `data-atualizacao` e registre pendências remanescentes.
- Salve o artefato e pare. Não acione TechLead, DBA ou outra skill automaticamente.