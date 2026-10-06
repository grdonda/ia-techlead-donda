---
name: developer
description: Processos de desenvolvimento de software. Use para tech-review de história, code-review, implementar mudanças, criar ou ajustar testes, mapear o fluxo de endpoints ou bibliotecas e fazer debug de erros reportados até a causa raiz.
argument-hint: "Processo e serviço ou biblioteca alvo"
user-invocable: false
---

# Developer

Executor: [developer](../../agents/developer.agent.md).

## Processos

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
