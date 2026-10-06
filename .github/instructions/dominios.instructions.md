---
name: Dominios
description: Estrutura canônica de pastas de dominios. Vale para todos os papéis ao ler ou gravar artefatos.
applyTo: "dominios/**"
---

# Estrutura de dominios

```text
dominios
├── <projetos>
│   ├── contexto
│   │   └── db
│   ├── historias
│   │   └── <jira-id>
│   │       ├── <jira-id>.md
│   │       ├── contexto
│   │       │   └── db
│   │       ├── refinamento
│   │       │   ├── <jira-id>_refinamento.md
│   │       │   └── <jira-id>_csd.md
│   │       ├── tech-review
│   │       │   └── <jira-id>_tech-review.md
│   │       ├── tasks
│   │       │   ├── dev
│   │       │   │   └── TASK00N - DEV - <titulo>.md
│   │       │   └── jira
│   │       │       └── TASK00N - <titulo>.md
│   │       └── testes
│   │           ├── cenarios
│   │           │   ├── cts
│   │           │   │   └── <assuntos>
│   │           │   │       └── CT00N - <titulo>.md
│   │           │   └── db
│   │           │       └── <assuntos>
│   │           │           └── CT00N - DB - <titulo>.md
│   │           └── jmeter
│   │               └── <srv-nome>-<jira-id>.jmx
│   └── srvs
│       ├── <srv-nome>
│       └── analises
│           ├── debug
│           │   └── <srv-nome>
│           │       ├── problema-<data>.md
│           │       └── report-<data>.md
│           ├── fluxo
│           │   └── <srv-nome>
│           │       └── <metodo>-<endpoint-slug>.md
│           └── review
│               └── <srv-nome>
│                   └── review-<data>.md
├── contexto
│   └── db
├── refinamentos
│   └── <assuntos>
│       ├── problema.md
│       ├── historia.md
│       ├── refinamento.md
│       └── csd.md
├── srvs
│   ├── <srv-nome>
│   └── analises
│       ├── debug
│       │   └── <srv-nome>
│       │       ├── problema-<data>.md
│       │       └── report-<data>.md
│       └── fluxo
│           └── <srv-nome>
│               └── <metodo>-<endpoint-slug>.md
└── srvs-shared
    ├── <lib-nome>
    └── analises
        ├── debug
        │   └── <srv-nome>
        │       ├── problema-<data>.md
        │       └── report-<data>.md
        └── fluxo
            └── <lib-nome>
                └── <operacao-slug>.md
```

## Regras

- `<projetos>`: estrutura de um projeto de um dominio.
- `<jira-id>`: identificador de uma história dentro de um projeto.
- `<assuntos>`: tópicos ou áreas específicas para categorias ou grupos pós analise.
- `<srv-nome>` e `<lib-nome>`: repositórios clonados de microsserviço e de biblioteca. Em `debug`, `<srv-nome>` é o serviço da causa raiz.
- `<db-nome>`: banco de dados analisado.
- `<data>`: formato `AAAA-MM-DD`.
- `CT00N`: N sequencial por assunto, iniciando em 1.
- `analises/` fica ao lado dos repositórios de serviço, nunca dentro do repositório clonado.
- Os destinos canônicos dos mapeamentos de fluxo são os caminhos mostrados nas ramificações `analises/fluxo/` da árvore acima. Todos os papéis devem consultar esta árvore para escolher o destino; não criar caminhos alternativos.