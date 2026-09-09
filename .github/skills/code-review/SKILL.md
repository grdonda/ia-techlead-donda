---
name: code-review
description: "Use ao revisar uma implementação Java/Spring em uma feature branch em relação à sua task, história e branch base quanto a defeitos funcionais e técnicos, regressões, contratos, testes, logs e observabilidade."
argument-hint: "Projeto, SRV, feature branch, branch base e task ou JIRA-ID"
---

# Code Review

Revise uma implementação disponível em relação ao seu escopo confirmado sem modificar código, salvo solicitação explícita.

## Procedimento

1. Confirme a feature branch, branch base, task ou história relacionada, código acessível e autorização.
2. Siga o [workflow de revisão](./workflows/realizar-code-review.md).
3. Registre os achados P0-P3, status da discussão, validações concluídas e itens não verificáveis com [code-review.md](./assets/code-review.md).

## Limites

- Não aprove requisitos ambíguos nem substitua a validação funcional de QA.
- Não altere código sem uma solicitação explícita de correção.