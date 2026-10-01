# Workflow: DBA

Análise, manipulação e exploração de bancos de dados relacionais e não relacionais

## Objetivo

Conhecer as tabelas de banco de dados, relações, consultas e manipulação de dados, priorizando a fonte de verdade já existente no repositório do serviço e, quando ela não existir, coletando o contexto de schema necessário diretamente com o usuário.

## Entradas

- Pedido do usuário com o banco de dados, o escopo (avulso, projeto ou história) e o objetivo (entender estrutura, localizar dados, gerar massa, manipular dados).
- Repositório do serviço associado, quando existir, para localizar migration ou DDL versionado:
  - `dominios/<projeto>/srvs/<srv-nome>/src/main/resources/db/migration` (ou caminho equivalente de migration/schema no repositório).
- Pasta de contexto conforme o escopo, quando não houver fonte no repositório:
  - avulso: `dominios/contexto/db/<db-nome>/`;
  - projeto: `dominios/<projeto>/contexto/db/<db-nome>/`;
  - história: `dominios/<projeto>/historias/<jira-id>/contexto/db/<db-nome>/`.

## Artefatos

- `dominios/.../contexto/db/<db-nome>/analise-<data>.md`, a partir do asset [dba.md](../assets/dba.md).
- `dominios/.../contexto/db/<db-nome>/estrutura-<data>.sql` ou `.json`, trazido pelo usuário a partir do comando de extração gerado.
- `dominios/.../contexto/db/<db-nome>/notebook-<data>.ipynb`, somente para SQL Server, quando aplicável.
- `<data>` é a data da investigação no formato `AAAA-MM-DD`, usada para diferenciar investigações do mesmo banco de dados.

## Etapas

1. Identificar o banco de dados envolvido e o escopo (avulso, projeto ou história) a partir do pedido.
2. Verificar se existe um serviço associado no workspace com migration ou DDL versionado; se existir e for suficiente, usar como fonte de verdade sem solicitar informação ao usuário.
3. Quando não existir fonte no repositório (base avulsa, apoio direto ao usuário, ou apoio à QA para massa de teste), perguntar ao Donda um item por vez, até ter informação suficiente para o pedido ou para os cenários que a QA está gerando.
4. Identificar ou perguntar o engine do banco de dados (MySQL, MariaDB, SQL Server, MongoDB ou outro).
5. Gerar o comando de extração adequado ao engine: DDL completo em `.sql` para bancos relacionais; amostra ou schema em `.json` para Mongo ou outro NoSQL.
6. Solicitar ao usuário que execute o comando e traga o arquivo gerado para a pasta de contexto correspondente ao escopo.
7. Analisar a migration ou o arquivo de contexto e registrar tabelas, coleções, relações e papéis no asset.
8. Propor as consultas ou manipulações necessárias para atender o pedido, tratando dado sensível com máscara e ambiente não produtivo.
9. Quando o banco for SQL Server e o pedido se beneficiar de um notebook para outros desenvolvedores, gerar o `.ipynb` com células organizadas e não executadas, sem conectar a uma base real.
10. Encaminhar ao `operador` o resultado consolidado a partir do asset [dba.md](../assets/dba.md), preservando títulos e estrutura, junto dos arquivos de contexto e do notebook quando aplicável.
11. Aguardar a confirmação do `operador` com os caminhos e o status persistido; então retornar o resultado ao Donda.

## Regras

- Priorizar a migration ou o DDL do repositório do serviço como fonte de verdade quando existir e for suficiente; não duplicar o schema manualmente nesse caso.
- Quando não houver fonte no repositório, solicitar apenas um item de cada vez, até ter informação suficiente para o pedido do usuário ou para os cenários que a QA está gerando.
- O agente nunca se conecta diretamente a uma base de dados real; toda extração é feita pelo usuário, que executa o comando gerado e traz o resultado.
- Tratar dado de banco como sensível: usar ambiente não produtivo, placeholders ou máscara, e scripts idempotentes quando possível.
- Gerar notebook `.ipynb` somente para SQL Server, por enquanto; células prontas para execução manual, nunca executadas pelo agente.
- Não inventar tabelas, colunas, relações, tipos ou dados não confirmados pela migration ou pelo arquivo de contexto fornecido.
- Diferenciar fato, hipótese e informação não confirmada.
- A integração direta entre QA e DBA para gerar massa de teste a partir de cenários será definida em um momento posterior; não implementar esse fluxo agora.
- O `dba-analista` analisa e propõe; não persiste artefatos.
- O `operador` persiste o artefato e os arquivos de contexto usando o asset; não complementa nem altera a análise recebida.
