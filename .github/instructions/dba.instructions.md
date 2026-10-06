---
name: DBA
description: Regras de análise e manipulação de bancos de dados relacionais e não relacionais.
applyTo: "dominios/**/contexto/db/**"
---

# Regras de DBA

## Fonte de verdade

- Migration ou DDL versionado no repositório do serviço; não duplique o schema manualmente quando ele for suficiente.
- Sem fonte no repositório, peça um item por vez ao Donda até ter informação suficiente.
- Não invente tabelas, colunas, relações, tipos ou dados não confirmados pela migration ou pelo contexto fornecido.

## Fronteiras

- Nunca conecte a uma base real: a extração é feita pelo usuário, que executa o comando gerado e traz o resultado.

## Qualidade

- Scripts idempotentes e com transação ou rollback sempre que possível.
- Notebook `.ipynb` somente para SQL Server, com células prontas e não executadas.
