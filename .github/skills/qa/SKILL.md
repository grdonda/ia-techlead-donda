---
name: qa
description: "Habilidade para atuar como QA"
argument-hint: "Cenários de teste"
user-invocable: false
disable-model-invocation: false
---

# QA

## Objetivo

Orientar o Donda a selecionar e executar o workflow QA adequado ao pedido, sem substituir a análise do subagente responsável.

## Workflows disponíveis

- [cts](./workflows/cts.md): usar para gerar cenários de teste a partir de uma história.

## Critérios de seleção

- Único workflow disponível nesta skill; selecionar sempre que o pedido for gerar cenários de teste.
- Comparar a intenção e as entradas disponíveis com o objetivo do workflow antes de confirmar a seleção.

## Pré-requisitos de roteamento

- Identificar a história de origem (`dominios/<projeto>/historias/<jira-id>/<jira-id>.md`).
- Se a história não existir ou faltar informação exigida pelo workflow, retornar ao Donda o bloqueio e o dado necessário; não presumir nem solicitar dados diretamente ao usuário.

## Plano para autorização

- Antes da autorização, devolver ao Donda a intenção, o workflow escolhido, o objetivo, agentes definidos pelo workflow, entradas, asset, artefato de saída, etapas resumidas e pendências/bloqueios.
- O Donda apresenta o plano ao usuário e aguarda autorização explícita.

## Após autorização

- Após a autorização, orientar o Donda a seguir o workflow selecionado e encaminhar as entradas e o asset aos agentes nele definidos.
- O analista realiza a análise; o Operador persiste artefatos somente quando o workflow determinar.
- Não comunicar diretamente com o usuário durante o roteamento ou a execução.

## Status e continuidade

- Ler o artefato mais recente antes de iniciar ou retomar uma etapa, conforme o workflow.
- Usar o contrato global de status definido pelo Operador; não criar nem alterar estados.
- Não alterar artefatos durante o roteamento.

## Subagentes

- [qa-analista](../../agents/qa.analista.agent.md) -> Analista especializado em qualidade de software.
- [operador](../../agents/operador.agent.md) -> Responsável por gerar os artefatos necessários.