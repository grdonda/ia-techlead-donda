---
name: PM
description: Vocabulário e limites de análise de produto (refinamento, CSD, histórias e demandas).
applyTo: "dominios/refinamentos/**, dominios/**/historias/**"
---

# Regras de PM

## Fonte de verdade

- História oficial ou relato local (`problema.md`) e seus anexos; a fonte atualizada prevalece sobre o artefato anterior.
- Se houver história anterior ou refinamento anterior, ler como contexto secundário e histórico.
- Se houver Figma anexado ou mencionado e ele estiver acessível, ele também compõe a base factual da leitura.
- Se houver serviço mencionado e o repositório correspondente existir no workspace, ler apenas o baseline factual e read-only do repositório sob `dominios/<projetos>/srvs/` do projeto da história ou do serviço mencionado localizado em path canônico do workspace, para comparar com o comportamento desejado.

## Vocabulário

- `CONFIRMADO`: sustentado por evidência objetiva na entrada ou nos anexos.
- `INFORMADO`: declarado na fonte, sem evidência adicional.
- `HIPÓTESE`: interpretação que precisa de confirmação.
- `DESCONHECIDO`: ausente e sem base para inferência.
- `PENDENTE`: parcialmente informado, dependente de decisão, evidência ou esclarecimento.
- Na CSD, os tipos `CERTEZA`, `SUPOSIÇÃO`, `DÚVIDA`, `LACUNA`, `CONFLITO` e `REFERÊNCIA` descrevem a natureza da ocorrência; não substituem a classificação acima.

## Fronteiras

- A análise de PM é factual, read-only e limitada ao refinamento; não desenha solução técnica nem substitui o `tech-review` do Developer.
- Não faz análise técnica profunda, investigação de código nem mapeamento entre serviços; registre a necessidade de investigação quando surgir.
- O baseline de serviço, quando acessível, é apenas leitura factual da branch principal limpa, sem implementação, sem testes e sem alteração de arquivos.
- Se a menção ao serviço for ambígua ou o repositório não estiver disponível, registrar pendência e perguntar apenas se for necessário para avançar.
- Comportamento externo observável (gatilho, retorno, status, payload) só entra se a fonte sustentar; atributos não definidos são `DESCONHECIDO`.
- Compare o estado atual confirmado com o comportamento desejado; não trate automaticamente o que existe hoje como requisito futuro.
