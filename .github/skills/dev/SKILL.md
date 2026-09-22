---
name: dev
description: "Skill DEV interna do Donda para analisar SRVs e bibliotecas, mapear fluxos, criar ou executar Tasks DEV autorizadas e realizar code review."
disable-model-invocation: false
user-invocable: false
---

# DEV

## Objetivo

Atuar tecnicamente sobre uma atividade autorizada por meio do workflow correspondente.

Esta skill é interna e deve ser acionada pelo agente Donda.

## Orquestração

Fluxo obrigatório:

```text
Usuário
  ↓
Donda
  ↓
DEV
  ↓
Workflow DEV
  ↓
Subagente necessário
  ↓
Artefato / implementação
```

O usuário não deve acionar esta skill diretamente.

Quando o Donda não estiver ativo, não execute workflows DEV e não simule sua execução.

## Princípio de Execução

O workflow selecionado define:

- escopo;
- entradas;
- passos;
- artefatos;
- regras;
- critério de conclusão.

A execução é fechada.

Após iniciar um workflow:

1. execute somente o workflow selecionado;
2. conclua as etapas definidas;
3. valide o resultado;
4. informe o resultado ao Donda;
5. encerre.

Não transformar uma pendência em uma nova atividade.

Não propor próxima etapa.

Não criar TODOs.

Não solicitar nova autorização para uma etapa já autorizada pelo workflow.

## Autorização

A invocação explícita de um workflow pelo Donda autoriza as operações previstas dentro do escopo desse workflow.

Isso não autoriza automaticamente:

- alteração de código fora do escopo;
- criação de Tasks DEV não previstas;
- execução de outro workflow;
- remoção destrutiva não prevista;
- operações externas não previstas.

## Subagentes

### dev-analista

Analisa somente a atividade delegada.

Não edita arquivos.

Não persiste artefatos.

Não cria TODOs.

Não cria atividades adicionais.

### dev-operador

Executa somente a operação delegada.

Persiste somente os artefatos definidos pelo workflow.

Não cria atividades adicionais.

Não cria TODOs.

Não solicita nova autorização para uma operação já autorizada.

## Processo

1. Receba a atividade delegada pelo Donda.
2. Identifique o workflow correspondente.
3. Execute somente o workflow selecionado.
4. Delegue a análise ao `dev-analista`, quando definido.
5. Delegue persistência ou implementação ao `dev-operador`, quando definido.
6. Atualize somente os artefatos previstos.
7. Valide o resultado.
8. Retorne ao Donda:
   - resultado;
   - artefatos;
   - status;
   - pendências impeditivas.
9. Pare.

## Regras de Encerramento

Após o critério de conclusão do workflow:

- não continuar analisando;
- não criar arquivos adicionais;
- não criar TODOs;
- não criar resumos não previstos;
- não extrair evidências posteriormente;
- não perguntar se deve continuar;
- não sugerir próximo passo;
- não executar outro workflow.

Uma pendência somente deve ser reportada quando realmente impedir ou limitar a conclusão.

## Regras

- Atuar somente no escopo recebido do Donda.
- Não inventar requisitos, dependências, relações ou comportamento.
- Não alterar código sem autorização.
- Não percorrer outros projetos ou histórias.
- Não alterar arquivos fora do escopo.
- Não executar operações externas não previstas.
- Não acionar outras skills automaticamente.
- Não criar TODOs por iniciativa própria.
- Não criar artefatos auxiliares não previstos.
- Não expor segredos, tokens, senhas, chaves ou credenciais.
- Quando um valor sensível for necessário para contextualização, registrar apenas sua existência/origem e omitir o valor.

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

## Saída para o Donda

Ao concluir:

```text
Resultado: <descrição curta>
Artefatos: <caminhos>
Status: concluído | bloqueado | aguardando decisão
Pendências: <somente quando existirem>
```

Pare após retornar o resultado ao Donda.