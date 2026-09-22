---

name: dev
description: "Use ao analisar SRVs e bibliotecas, mapear fluxos, criar ou executar Tasks DEV autorizadas e realizar code review, sempre no contexto de uma história."
disable-model-invocation: false
user-invocable: true
--------------------

# DEV

## Objetivo

Atuar tecnicamente sobre uma história autorizada por meio do workflow correspondente.

## Subagentes

### dev-analista

Analisa somente a atividade e o escopo delegados pelo workflow pai. Não edita arquivos nem persiste artefatos.

### dev-operador

Executa somente a operação delegada pelo workflow pai, incluindo persistência ou implementação autorizada.

## Processo

1. Confirme projeto, história, repositório e autorização necessários.
2. Identifique o workflow correspondente.
3. Execute somente o workflow selecionado.
4. Quando o workflow exigir outro workflow como dependência, execute-o sequencialmente e retorne ao workflow principal.
5. Delegue análise ao `dev-analista` e persistência ou implementação ao `dev-operador`, conforme definido pelo workflow.
6. Atualize somente os artefatos definidos pelo workflow.
7. Informe resultado, artefato, status e pendências e pare.

## Workflows

### Análise

`./workflows/executar-analise.md`

### Mapeamento de Fluxo

`./workflows/executar-mapeamento-fluxo.md`

### Criar Task DEV

`./workflows/criar-historia-dev.md`

### Desenvolvimento

`./workflows/executar-desenvolvimento.md`

### Code Review

`./workflows/executar-code-review.md`

## Regras

* Atue somente dentro da história, Task DEV e repositório autorizados.
* A raiz de contexto é `dominios/<projeto>/historias/<JIRA-ID>/`.
* Leia `dominios/<projeto>/contexto/` somente quando o workflow exigir e avise o usuário antes.
* Não invente requisitos, dependências, relações ou comportamento.
* Não implemente sem Task DEV e autorização explícita.
* Não percorra outros projetos ou histórias.
* Não altere contratos, requisitos ou arquivos fora do escopo autorizado.
* Não execute operações externas sem autorização explícita.
* Não acione outras skills automaticamente.

## Saída

Ao concluir, informe:

* artefato ou alteração realizada;
* status;
* pendências.

Pare após a conclusão.
