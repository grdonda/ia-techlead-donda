---
name: revisar-dominios
description: Compara a estrutura real de dominios/ com a estrutura canônica. Somente leitura.
argument-hint: "[projeto ou tudo]"
agent: agent
tools: [read, search]
---

Compare a árvore real de `dominios/` com a estrutura de [dominios](../instructions/dominios.instructions.md). Não altere arquivos.

Escopo: ${input:escopo:projeto ou tudo}

Reporte:

1. Pastas esperadas que não existem.
2. Pastas ou arquivos fora da estrutura (ignore `.gitkeep` e o conteúdo dos repositórios clonados).
3. Pastas `analises/` dentro de repositórios clonados.
4. Datas fora do formato `AAAA-MM-DD`.
5. Artefatos em pasta de tipo errado.
6. Arquivos esperados que não existem.
7. Arquivos fora da estrutura ou com nome incompatível com o artefato esperado.

Saída: tabela com Tipo, Caminho e Observação. Se não houver divergência, diga isso.
