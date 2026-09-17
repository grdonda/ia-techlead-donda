---
projeto: <projeto>
jira: <JIRA-ID>
etapa: solicitacao-csv
status: pendente
data-criacao: <AAAA-MM-DD HH:mm>
data-atualizacao: <AAAA-MM-DD HH:mm>
responsavel: dba
---

# `<JIRA-ID>` - Solicitacao de CSV

## Motivo

## Tabela e Estrutura Necessaria

- Banco/schema: `<confirmar>`
- Tabela: `<confirmar>`
- Colunas obrigatorias: `<confirmar>`
- Chaves ou relacionamentos: `<confirmar>`

## Consulta SELECT Proposta

```sql
-- Executar somente no ambiente autorizado e apos revisar o filtro.
SELECT
    <colunas_confirmadas>
FROM <schema>.<tabela>
WHERE <filtro_confirmado>;
```

## Filtros de Massa

- Telefone: `<mascarado ou placeholder>`
- CPF/CNPJ: `<mascarado ou placeholder>`
- Segmento: `<MEI, SME ou outro>`
- Tipo de cliente: `<PF/PJ>`

## Formato de Entrega

- CSV sem credenciais ou senhas.
- Dados sensiveis mascarados quando nao forem indispensaveis.
- Informar quantidade de registros e data da extracao.
