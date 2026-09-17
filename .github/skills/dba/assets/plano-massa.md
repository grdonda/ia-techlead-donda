---
projeto: <projeto>
jira: <JIRA-ID>
ct: CT00N
etapa: plano-massa
status: pendente
data-criacao: <AAAA-MM-DD HH:mm>
data-atualizacao: <AAAA-MM-DD HH:mm>
responsavel: dba
---

# CT00N - DB - `<Titulo>`

## Pre-requisitos Confirmados

## Contexto e Correlacoes

## Tabelas e Registros Alvo

|Tabela|Chave de localizacao|Criterio|Acao|Quantidade|
|---|---|---|---|---|
|N/A|N/A|N/A|SELECT / INSERT / UPDATE|N/A|

## Massa Necessaria

- PF:
- PJ:
- PJ MEI:
- PJ SME:
- Outros:

## Scripts SQL

```sql
SET XACT_ABORT ON;
BEGIN TRANSACTION;

-- SELECT de validacao antes da alteracao

-- INSERT/UPDATE autorizado

-- SELECT de validacao depois da alteracao

-- COMMIT ou ROLLBACK somente apos conferencia
COMMIT TRANSACTION;
-- ROLLBACK TRANSACTION;
```

## Validacao

## Limpeza e Restauracao

## Riscos e Pendencias
