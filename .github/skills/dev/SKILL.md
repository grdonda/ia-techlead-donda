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

## Workflows

Orienta o agente como executar o pedido do usuario.

- [fluxo](./workflows/fluxo.md): usar para mapear a entrada, o processamento, as comunicações e as respostas de um endpoint, operação ou serviço.
- [erros](./workflows/erros.md): usar quando o pedido relata uma falha e busca localizar sua ruptura e causa.

- Após a autorização, orientar o Donda a seguir o workflow selecionado e encaminhar as entradas e o asset aos agentes nele definidos.

## Subagentes

- [dev-analista](../../agents/dev.analista.agent.md) -> Analista especializado em desenvolvimento de software.
