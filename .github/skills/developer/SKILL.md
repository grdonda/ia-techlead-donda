---
name: developer
description: Processos de produto e desenvolvimento de software. Use para refinamento, CSD, tech-review de história, code-review, implementação, testes, mapeamento de fluxo e debug.
argument-hint: "Processo (refinamento, csd, tech-review, code-review, desenvolvimento, testes, fluxo ou debug) e alvo"
user-invocable: false
---

# Developer

Executor: [developer](../../agents/developer.agent.md).

## Processos

### refinamento

- Usar quando: transformar relato ou história em User Story e refinamento.
- Saída: `historia.md` e `refinamento.md` no cenário de relato, ou `<jira-id>_refinamento.md` no cenário de história.
- Referência: [refinamento-referencia](./references/refinamento-referencia.md).
- Assets: [historia](./assets/historia.md), [refinamento-asset](./assets/refinamento-asset.md).
- O fluxo pode ler Figma e baseline observável de serviço quando isso estiver anexado, mencionado e acessível, e pode depender da sincronização da branch `main` do serviço relevante antes da leitura read-only do baseline.
- Os nomes canônicos do fluxo são [refinamento-referencia](./references/refinamento-referencia.md) e [refinamento-asset](./assets/refinamento-asset.md).

### csd

- Usar quando: registrar certezas, suposições, dúvidas, lacunas, conflitos e referências de um conteúdo já existente.
- Saída: matriz CSD (`dominios/<projetos>/historias/<jira-id>/refinamento/<jira-id>_csd.md` para história ou `dominios/refinamentos/<assuntos>/csd.md` para demanda ad-hoc).
- Referência: [csd](./references/csd.md).
- Asset: [csd](./assets/csd.md).

### tech-review

- Usar quando: validar tecnicamente uma história (serviços envolvidos, contratos, dependências, riscos e impactos).
- Saída: tech-review da história (`<jira-id>_tech-review.md`).
- Referência: [tech-review](./references/tech-review.md).
- Asset: [tech-review](./assets/tech-review.md).

### code-review

- Usar quando: avaliar código, arquitetura ou mudança.
- Saída: review do serviço (`review-<data>.md`).
- Referência: [code-review](./references/code-review.md).
- Asset: [code-review](./assets/code-review.md).

### desenvolvimento

- Usar quando: implementar uma mudança já definida.
- Saída: alterações no repositório e resumo.
- Referência: [desenvolvimento](./references/desenvolvimento.md).

### testes

- Usar quando: criar, ajustar ou analisar testes automatizados.
- Saída: testes no repositório e resumo.
- Referência: [testes](./references/testes.md).

### fluxo

- Usar quando: mapear entrada, processamento, comunicações e retornos de endpoints ou operações.
- Saída: um mapeamento por endpoint (`<metodo>-<endpoint-slug>.md`).
- Referência de processo: [fluxo-referencia](./references/fluxo-referencia.md).
- Asset de pesquisa e análise: [fluxo-asset](./assets/fluxo-asset.md).

### debug

- Usar quando: investigar erro reportado até a causa raiz e a correção.
- Saída: report do erro (`report-<data>.md`).
- Referência: [debug](./references/debug.md).
- Asset: [report](./assets/report.md).
