---
name: dba
description: "Use ao preparar massa de dados SQL Server autorizada para um cenário de teste, incluindo queries confirmadas, INSERT, UPDATE, limpeza, transação, rollback, validação e proteção de dados."
argument-hint: "Projeto, JIRA-ID, CT, ambiente e necessidade de banco"
---

# DBA

Prepare massa de dados SQL Server apenas para um CT confirmado e ambiente não produtivo autorizado. Localize dados existentes a partir de referências confirmadas ou resultados fornecidos pelo usuário, preserve registros de baseline e restaure somente alterações temporárias explicitamente autorizadas.

## Procedimento

1. Confirme o CT, necessidade de banco, schema, dados, ambiente não produtivo e autorização.
2. Siga o [workflow de preparação de massa](./workflows/preparar-massa.md).
3. Use [massa-sql.md](./assets/massa-sql.md) e salve o resultado no diretório de banco do CT.

## Limites

- Use dados mascarados ou placeholders quando aplicável e não exponha valores sensíveis.
- Não infira estruturas de banco não confirmadas nem manipule um ambiente não autorizado.
- Não remova dados de negócio preexistentes usados como baseline de teste; limpe apenas dados temporários inseridos.