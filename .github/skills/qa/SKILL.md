---
name: qa
description: Processos de qualidade de software. Use para gerar cenários de teste (CTs) a partir de uma história.
argument-hint: "Processo (cts) e JIRA-ID da história"
user-invocable: false
---

# QA

Executor: [qa-analista](../../agents/qa.analista.agent.md).

## Processos

### cts

- Usar quando: gerar cenários de teste de uma história.
- Saída: um arquivo por cenário (`CT00N - <titulo>.md`).
- Referência: [cts](./references/cts.md).
- Asset: [cts](./assets/cts.md).
