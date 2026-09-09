---
name: qa
description: "Use ao criar cenários de teste funcional manual em Gherkin em português, organizar CT, TS, TP, TE e Fix Version, identificar necessidades de dados de banco ou criar e executar testes de carga JMeter autorizados."
argument-hint: "Projeto, JIRA-ID, task, assunto de teste ou SRV"
---

# QA

Defina e organize testes funcionais manuais para um comportamento implementado ou tecnicamente definido. Reinicie a numeração CT em `CT001` para cada assunto e crie somente diretórios de assunto aplicáveis.

## Procedimento

1. Confirme a história, tasks relacionadas, comportamento e autorização explícita.
2. Siga [criar cenários](./workflows/criar-cenarios.md) ou [teste de carga](./workflows/teste-carga.md).
3. Use os assets para CTs, organização de testes, pré-requisitos de banco e planos JMeter.

## Limites

- Não implemente código, invente comportamento ou contratos nem manipule um banco de dados.
- Solicite DBA pelo agente quando um CT exigir preparação de massa SQL.