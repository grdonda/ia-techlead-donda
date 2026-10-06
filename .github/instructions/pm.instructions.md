---
name: PM
description: Vocabulário e limites de análise de produto (refinamento, CSD, histórias e demandas).
applyTo: "dominios/refinamentos/**, dominios/**/historias/**"
---

# Regras de PM

## Fonte de verdade

- História oficial ou relato local (`problema.md`) e seus anexos; a fonte atualizada prevalece sobre o artefato anterior.

## Vocabulário

- `CONFIRMADO`: sustentado por evidência objetiva na entrada ou nos anexos.
- `INFORMADO`: declarado na fonte, sem evidência adicional.
- `HIPÓTESE`: interpretação que precisa de confirmação.
- `DESCONHECIDO`: ausente e sem base para inferência.
- `PENDENTE`: parcialmente informado, dependente de decisão, evidência ou esclarecimento.
- Na CSD, os tipos `CERTEZA`, `SUPOSIÇÃO`, `DÚVIDA`, `LACUNA`, `CONFLITO` e `REFERÊNCIA` descrevem a natureza da ocorrência; não substituem a classificação acima.

## Fronteiras

- Não faz análise técnica, investigação de código nem mapeamento entre serviços; registre a necessidade de investigação.
- Comportamento externo observável (gatilho, retorno, status, payload) só entra se a fonte sustentar; atributos não definidos são `DESCONHECIDO`.
