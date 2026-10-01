---
name: dev
description: "Habilidade para atuar como especialista em desenvolvimento de software, engenharia de software e arquitetura de software, troubleshooting e resolução de problemas complexos."
argument-hint: "Pedido, historia, analise, troubleshooting, resolução de problemas complexos"
user-invocable: false
disable-model-invocation: false
---

# DEV

## Objetivo

Orientar o Donda a selecionar e executar o workflow DEV adequado ao pedido, sem substituir a análise do subagente responsável.

## Workflows disponíveis

- [fluxo](./workflows/fluxo.md): usar para mapear a entrada, o processamento, as comunicações e as respostas de um endpoint, operação ou serviço.
- [erros](./workflows/erros.md): usar quando o pedido relata uma falha e busca localizar sua ruptura e causa.

## Critérios de seleção

- Se o objetivo é entender como uma operação percorre o sistema, selecionar `fluxo`.
- Se o objetivo é investigar um erro reportado, selecionar `erros`.
- Comparar a intenção e as entradas disponíveis com o objetivo do workflow; não escolher somente por palavras-chave.
- Se mais de um workflow parecer necessário, delimitar a sequência no plano. Não iniciar etapas fora do escopo autorizado.

## Pré-requisitos de roteamento

- Para `fluxo`, confirmar serviço ou biblioteca, repositório e endpoint/operação ou pedido explícito para mapear todas as entradas da aplicação.
- Para `erros`, identificar o serviço onde o erro foi percebido, o relato e as evidências disponíveis.
- Se faltar informação exigida pelo workflow, retornar ao Donda o bloqueio e o dado necessário; não presumir nem solicitar dados diretamente ao usuário.

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

- [dev-analista](../../agents/dev.analista.agent.md) -> Analista especializado em desenvolvimento de software.
- [operador](../../agents/operador.agent.md) -> Responsável por gerar os artefatos necessários.