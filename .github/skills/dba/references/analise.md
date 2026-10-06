# Processo: analise

Análise, manipulação e exploração de bancos de dados relacionais e não relacionais.

Estrutura de pastas: [dominios](../../../instructions/dominios.instructions.md).

## Entradas

- Pedido com o banco, o escopo (avulso, projeto ou história) e o objetivo (entender estrutura, localizar dados, gerar massa, manipular dados).
- Migration ou DDL do serviço associado, quando existir: `dominios/<projetos>/srvs/<srv-nome>/src/main/resources/db/migration` (ou caminho equivalente).
- Pasta de contexto, quando não houver fonte no repositório:
  - avulso: `dominios/contexto/db/<db-nome>/`;
  - projeto: `dominios/<projetos>/contexto/db/<db-nome>/`;
  - história: `dominios/<projetos>/historias/<jira-id>/contexto/db/<db-nome>/`.

## Etapas

1. Identificar o banco e o escopo.
2. Se houver serviço associado com migration ou DDL suficiente, usá-lo como fonte de verdade.
3. Sem fonte no repositório (base avulsa, apoio ao usuário ou à QA para massa de teste), pedir ao Donda um item por vez até ter informação suficiente.
4. Identificar o engine (MySQL, MariaDB, SQL Server, MongoDB ou outro).
5. Gerar o comando de extração: DDL `.sql` para relacionais; amostra ou schema `.json` para NoSQL.
6. Pedir ao usuário que execute o comando e traga o arquivo para a pasta de contexto.
7. Analisar a migration ou o contexto e registrar tabelas, coleções, relações e papéis no asset.
8. Propor consultas ou manipulações para o pedido, com dados mascarados e ambiente não produtivo.
9. Se for SQL Server e o pedido se beneficiar, gerar o notebook `.ipynb` com células organizadas e não executadas.

## Regras

- A integração direta entre QA e DBA para gerar massa de teste será definida depois; não implementar agora.
