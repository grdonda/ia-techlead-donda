# Validar e Limpar Massa

Documente a validacao antes/depois do cenario e a restauracao dos dados temporarios.

## Etapas

1. Leia o plano de massa e o resultado da execucao autorizada.
2. Marque o CT-DB como `status: em andamento`.
3. Valide quantidade, chaves, correlacoes e estado esperado.
4. Diferencie registros preexistentes de registros temporarios.
5. Documente `COMMIT` ou `ROLLBACK` e a limpeza seletiva.
6. Nao remova baseline de negocio.
7. Atualize o CT-DB com status, data e resultado; marque `concluído` ou `bloqueado` e informe ao QA.
