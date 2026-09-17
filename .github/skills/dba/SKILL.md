---
name: dba
description: "Use ao avaliar contexto de banco, solicitar CSVs, preparar massa SQL Server autorizada para cenários de teste, validar dados, executar transações documentadas, realizar rollback e limpar massa temporária."
argument-hint: "Projeto, JIRA-ID, CT, ambiente e necessidade de banco"
---

# DBA

Prepare massa de dados SQL Server somente para cenários de teste e ambiente não produtivo autorizado. Avalie primeiro se a história, os CTs, os CSVs e os contratos fornecem contexto suficiente para propor consultas e alterações consistentes.

O fluxo normal exige CT e CT-DB prontos. A exceção `pre-analisar-massa` permite levantar previamente a massa provável a partir da história, sem executar comandos, quando ainda não houver cenários.

Considere correlações confirmadas entre telefone, CPF, CNPJ, segmento, tipo de cliente e demais referências de negócio. Senhas e credenciais nunca devem ser armazenadas em texto puro.

## Subagentes

- `dba-analista`: lê e classifica a suficiência do contexto; não edita nem executa SQL.
- `dba-operador`: registra os artefatos e scripts autorizados; não executa SQL contra banco.

## Procedimento

1. Confirme projeto, história, CT, necessidade de banco, schema, dados, ambiente não produtivo e autorização.
2. Leia os arquivos CSV, SQL, contratos e demais referências em `dominios/<projeto>/contexto/db/` ou `dominios/<projeto>/historias/<JIRA-ID>/contexto/db/`.
3. Verifique se existe cenário de teste e CT-DB em `dominios/<projeto>/historias/<JIRA-ID>/testes/<assunto>/dbs/`.
4. Siga [avaliar-contexto](./workflows/avaliar-contexto.md). Se faltarem dados, use [solicitar-csv](./workflows/solicitar-csv.md).
5. Se não houver cenário pronto, use somente [pre-analisar-massa](./workflows/pre-analisar-massa.md).
6. Para cenário pronto, siga [preparar-massa](./workflows/preparar-massa.md).
7. Após a execução autorizada, siga [validar-limpar-massa](./workflows/validar-limpar-massa.md).
8. Use [plano-massa.md](./assets/plano-massa.md) e salve o resultado em `testes/<assunto>/dbs/`.

## Limites

- Use dados mascarados ou placeholders quando aplicável e não exponha valores sensíveis.
- Não infira estruturas de banco não confirmadas nem manipule um ambiente não autorizado.
- Não remova dados de negócio preexistentes usados como baseline de teste; limpe apenas dados temporários inseridos.
- Proponha `SELECT` direto e revisável para exportação de CSV antes de solicitar massa adicional.
- Não proponha `UPDATE` ou `DELETE` sem tabela, coluna, chave, filtro e finalidade confirmados.
- Use `SET XACT_ABORT ON`, transação, validação antes/depois e registre explicitamente `COMMIT` ou `ROLLBACK`.
- A execução dos comandos depende de autorização explícita; a skill pode gerar e revisar scripts sem executá-los.
- Entregue o artefato ao QA e aguarde a próxima solicitação; não acione outra skill automaticamente.

## Status e Continuidade

- Leia o CT-DB ou a pré-análise mais recente antes de iniciar ou retomar uma etapa.
- Ao iniciar, marque `status: em andamento`; ao aguardar CSV, contrato ou autorização, use `aguardando usuário`.
- Use `bloqueado` para ausência de CT, estrutura ou ambiente autorizado e `desatualizado` quando o contexto mudar.
- Ao concluir, marque `concluído`, atualize `data-atualizacao` e registre o resultado de validação, `COMMIT` ou `ROLLBACK`.
- Salve o artefato e pare. Não acione QA ou outra skill automaticamente.