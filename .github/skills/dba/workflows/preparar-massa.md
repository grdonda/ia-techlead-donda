# Preparar Massa

Crie comandos documentados para o CT-DB autorizado.

## Etapas

1. Exija CT e CT-DB prontos, ou use a excecao de pre-analise sem executar comandos.
2. Leia o plano de massa mais recente e marque `status: em andamento`.
3. Leia historia, CT, CT-DB, inventario, CSVs e contratos.
4. Confirme ambiente, tabela, registros-alvo e finalidade.
5. Use `plano-massa.md` para registrar SELECT, INSERT, UPDATE, validacao, limpeza e restauracao.
6. Envolva alteracoes em transacao com `SET XACT_ABORT ON`.
7. Gere SQL para execucao manual autorizada, nunca contra producao.
8. Marque `concluído` ou `bloqueado`, atualize a data, entregue ao QA e aguarde a proxima etapa.
