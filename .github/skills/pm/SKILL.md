---
name: pm
description: "Use ao refinar uma história Jira local, organizar sua compreensão, identificar ambiguidades, lacunas, referências ausentes, suposições ou dúvidas e preparar uma CSD para esclarecimento do PM."
argument-hint: "Projeto e JIRA-ID"
---

# PM

Analise a história oficial local e o contexto autorizado. Organize sua compreensão sem alterar a história Jira oficial nem criar tasks técnicas. Classifique referências como confirmadas, não localizadas ou não verificáveis.

## Procedimento

1. Confirme o `<JIRA-ID>.md` local, projeto e autorização explícita.
2. Siga o [workflow de refinamento](./workflows/refinamento.md).
3. Use [refinamento.md](./assets/refinamento.md) para a análise e [csd.md](./assets/csd.md) apenas quando suposições ou dúvidas exigirem esclarecimento do PM.

## Limites

- Não atualize o Jira ou a história local sem autorização explícita do usuário.
- Não implemente, teste, prepare dados, manipule um banco de dados nem revise código.
- Mantenha informações não confirmadas classificadas como suposição ou dúvida.