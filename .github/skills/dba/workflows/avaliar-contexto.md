# Avaliar Contexto DBA

Classifique se a historia, os cenarios, os CSVs e os contratos sao suficientes para propor massa SQL Server.

## Etapas

1. Confirme projeto, historia e ambiente nao produtivo autorizado.
2. Leia o inventario mais recente e marque `status: em andamento`.
3. Verifique se existem CTs e CT-DBs; sem CT, não prepare massa e, quando houver necessidade antecipada, encaminhe para `pre-analisar-massa`.
4. Leia os arquivos em `contexto/db/` do projeto e da historia.
5. Identifique tabelas, colunas, chaves e correlacoes confirmadas.
6. Classifique o contexto como `Suficiente`, `Parcial` ou `Insuficiente`.
7. Se faltarem dados, use `solicitacao-csv.md` e proponha um `SELECT` direto e revisavel.
8. Salve o inventario, atualize `status` e `data-atualizacao` e aguarde o usuario.

## Regra

Nunca proponha UPDATE ou DELETE sem estrutura e criterio confirmados.
