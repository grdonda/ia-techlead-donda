# Processo: code-review

Revisão técnica de código, arquitetura ou de uma mudança proposta.

Estrutura de pastas: [dominios](../../../instructions/dominios.instructions.md).

## Entradas

- Alvo: serviço, diff ou arquivos; objetivo da revisão.

## Saída

`dominios/<projetos>/srvs/analises/review/<srv-nome>/review-<data>.md`, a partir do asset [code-review](../assets/code-review.md). Este processo cobre serviços de projeto; a árvore global e `srvs-shared` não possuem pasta de `review`.

## Etapas

1. Delimitar o escopo e identificar a stack pelo repositório.
2. Ler o código, os contratos e os testes relacionados.
3. Avaliar correção, contratos, resiliência, segurança, desempenho, observabilidade e testes.
4. Apontar code smells com evidência e a técnica de refatoração indicada.
5. Classificar cada achado por severidade.
6. Devolver o review estruturado.
