---
name: pm
description: Processos de Product Management. Use para refinar um relato ou história (User Story e refinamento) e para montar a matriz CSD de certezas, suposições e dúvidas.
argument-hint: "Processo (refinamento, csd) e fonte (relato local ou JIRA-ID)"
user-invocable: false
---

# PM

Executor: [pm-analista](../../agents/pm.analista.agent.md).

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
