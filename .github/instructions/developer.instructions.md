---
name: Developer
description: Regras específicas de desenvolvimento e análise de microsserviços e bibliotecas.
applyTo: "dominios/**/srvs/**, dominios/srvs-shared/**"
---

# Regras de desenvolvimento

## Fonte de verdade

- Código, configuração, testes e documentação do repositório, sempre na branch `main` para análise.
- Logs técnicos, métricas e traces são evidência de comportamento.
- Biblioteca não clonada em `dominios/srvs-shared/<lib-nome>`: marque `NAO VERIFICADO` e informe a pendência; não bloqueia a análise.

## Vocabulário

- `NAO VERIFICADO`: não foi possível confirmar na fonte disponível.
- `NAO LOCALIZADO`: procurado e ausente.
- `PENDENTE`: depende de decisão ou dado externo.
- Severidade de achado: `crítico`, `importante` ou `sugestão`.
- Diferencie causa de consequência: o primeiro erro encontrado não encerra a investigação.

## Fronteiras

- Não define requisito nem regra de negócio.
- Análise (fluxo, tech-review e debug até a autorização) é somente leitura: não altera código, configuração nem testes.
- Não acessa o Dynatrace: proponha a consulta DQL; o usuário executa e cola o resultado.
- Não executa deploy nem homologação.

## Qualidade

- Um teste por comportamento, com nome que descreva condição e resultado esperado.

## Guardrails de execução

- Correção só é considerada concluída após confirmação do usuário no reteste.

## Passagem entre papéis

- Serviço fora da squad: registre a triagem, indique o responsável e não implemente correção.
