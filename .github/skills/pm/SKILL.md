---
name: pm
description: "Habilidade para atuar como Product Manager, organizar a execução de workflows e gerenciar pedidos de negócio"
argument-hint: "Refinamento, Matriz CSD, análise de historias"
user-invocable: false
disable-model-invocation: false
---

# PM

## Objetivo

Orientar o Donda a selecionar e executar o workflow PM adequado ao pedido, sem substituir a análise do subagente responsável.

## Workflows disponíveis

- [csd](./workflows/executar-csd.md): usar para registrar e rastrear certezas, suposições, dúvidas, lacunas, conflitos e referências de um conteúdo já encaminhado por outro workflow.
- [refinamento](./workflows/executar-refinamento.md): usar para transformar um relato ou história em User Story e refinamento estruturado.

## Critérios de seleção

- Se o pedido é validar o entendimento de um conteúdo já existente, identificando incertezas rastreáveis, selecionar `csd`.
- Se o pedido é produzir ou atualizar a User Story e o refinamento a partir de um relato ou história, selecionar `refinamento`.
- CSD não substitui refinamento, análise técnica, mapeamento de fluxo ou definição de solução; comparar a intenção e as entradas disponíveis antes de confirmar a seleção.
- Se mais de um workflow parecer necessário, delimitar a sequência no plano. Não iniciar etapas fora do escopo autorizado.

## Pré-requisitos de roteamento

- Para `csd`, confirmar a fonte ou conteúdo a ser analisado e localizar o artefato CSD anterior, quando existir.
- Para `refinamento`, identificar se a entrada é um relato local (`problema.md`) ou uma história com JIRA-ID, e localizar a fonte e o artefato anterior correspondente.
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

- [pm-analista](../../agents/pm.analista.agent.md) -> Analista especializado em Product Management.
- [operador](../../agents/operador.agent.md) -> Responsável por gerar os artefatos necessários.