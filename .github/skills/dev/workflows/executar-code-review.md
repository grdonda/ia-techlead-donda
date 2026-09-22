# Code Review DEV

## Objetivo

Validar se as alterações autorizadas atendem à história e à análise DEV, quando existir.

## Processo

1. Confirme projeto, história, Task DEV, branch ou commit e autorização explícita.
2. Leia a história, a análise DEV quando existir e somente o diff ou arquivos autorizados.
3. Use o `dev-analista` para avaliar bugs, regressões, contratos, riscos, observabilidade, mensageria e testes quando aplicáveis.
4. Analise explicitamente os testes TDD criados ou alterados.
5. Use o `dev-operador` para registrar o resultado em:

`dominios/<projeto>/historias/<JIRA-ID>/code-review/`

## Regras

* Analise somente o diff ou arquivos autorizados.
* Não altere o código revisado.
* Não invente falhas.
* Registre ausência ou insuficiência de testes como pendência.
* Não expanda o escopo do review.

## Saída

Registre:

* resultado;
* evidências;
* testes analisados;
* riscos;
* pendências;
* `status`;
* `data-atualizacao`;
* `responsavel`.

Status:

* `concluído`
* `aguardando usuário`
* `bloqueado`
