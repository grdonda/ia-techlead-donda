# Solicitar CSV

Gere uma solicitacao objetiva de dados para exportacao de contexto.

## Etapas

1. Leia o inventario de contexto e a estrutura confirmada.
2. Leia a solicitacao mais recente e marque `status: em andamento`.
3. Defina tabela, schema, colunas, relacionamentos e filtro.
4. Proponha um `SELECT` consistente, sem credenciais e sem dados alem do necessario.
5. Informe a quantidade e o tipo de registros esperados.
6. Marque `aguardando usuário`, salve a solicitacao e aguarde o CSV no `contexto/db/`.

## Regra

Nao invente tabela ou coluna. Quando a estrutura nao estiver confirmada, solicite primeiro o DDL, contrato ou exemplo de arquivo.
