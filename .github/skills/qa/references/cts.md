# Processo: cts

Geração de cenários de teste a partir de uma história.

Estrutura de pastas: [dominios](../../../instructions/dominios.instructions.md).

## Entradas

- História: `dominios/<projetos>/historias/<jira-id>/<jira-id>.md`. Se não existir, avisar o usuário e encerrar.

## Saída

`dominios/<projetos>/historias/<jira-id>/testes/cenarios/cts/<assuntos>/CT00N - <titulo>.md`, a partir do asset [cts](../assets/cts.md).

## Etapas

1. Identificar na história tudo que é testável.
2. Agrupar os testes por assunto.
3. Agrupar cenários que tenham opções testáveis.
4. Titular cada cenário como `CT00N - <titulo>`, com N sequencial por assunto, iniciando em 1.
5. Preencher o asset para cada cenário, registrando os requisitos da história atendidos.
