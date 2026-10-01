# Workflow: cts - cenários de testes

## Objetivo

Habilidade de gerar cenarios de testes

## Etapas

- Identificar na historia `dominios/<projeto>/historias/<jira-id>/<jira-id>.md` todo que for testável.
- Identificar os agrupamentos de testes por assunto.
- Agrupar cenários de testes quando identificar cenarios com opções testáveis.

## Regras

- quando a historia não existir, avise usuario, encerre.
- titulos sempre serão: `CT00N - tiulo do teste`; N sempre será N+1 iniciando em 1 para cada cenario por assunto.
- cenarios de testes são agrupados por assunto.

## Asset

- [cts.md](../assets/cts.md)

## Artefato

- `dominios/<projeto>/historias/<jira-id>/testes/cenarios/cts/<assunto>/CT00N - tiulo.md`
