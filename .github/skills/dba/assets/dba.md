# Análise de banco de dados

Análise, manipulação e exploração de um banco de dados relacional ou não relacional

## Escopo

- Projeto: `<projeto ou Nao aplicavel>`
- História: `<jira-id ou Nao aplicavel>`
- Banco de dados: `<nome>`
- Engine: `<MySQL, MariaDB, SQL Server, MongoDB ou outro>`
- Ambiente: `<nao produtivo ou produção somente leitura>`

## Pedido do usuário

- `<descrição objetiva do que precisa ser entendido, localizado ou manipulado>`

## Fonte utilizada

- Origem: `<migration/DDL no repositório do serviço ou contexto fornecido pelo usuário>`
- Repositório e caminho da migration, quando aplicável: `<caminho>`
- Branch: `<git branch analisada ou NAO VERIFICADO>`

## Itens solicitados ao usuário

Preencher somente quando não houver migration/DDL suficiente no repositório. Um item por vez, até haver informação suficiente para o pedido.

|Item solicitado|Motivo|Resposta do usuário|
|---------------|------|-------------------|
|               |      |                   |

## Comando de extração gerado

Gerado conforme o engine identificado ou informado pelo usuário. O usuário executa manualmente e traz o arquivo de volta.

```text
<comando sugerido para gerar DDL (.sql) ou amostra/schema (.json) ou Nao aplicavel>
```

## Arquivos de contexto

- Estrutura: `<caminho do .sql ou .json gerado>`
- Amostra de dados mascarada, quando aplicável: `<caminho ou Nao aplicavel>`

## Estrutura identificada

- Tabelas/coleções e papel no domínio: `<descrição>`
- Relações (chaves primárias, estrangeiras ou referências entre coleções): `<descrição>`

## Consultas e manipulações propostas

|Consulta ou manipulação|Objetivo|Status|
|-----------------------|--------|------|
|                       |        |      |

## Notebook

Gerar somente quando o banco for SQL Server e o pedido se beneficiar de um notebook para outros desenvolvedores. Células prontas para execução manual; o agente não executa nem se conecta a uma base real.

- Caminho: `<contexto/db/<db-nome>/notebook-<data>.ipynb ou Nao aplicavel>`

## Pendências e limites

- Informação não confirmada: `<informação e motivo>`
- Próximo item necessário: `<item ou Nao aplicavel>`
