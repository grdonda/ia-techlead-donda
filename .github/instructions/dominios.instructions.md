---
name: Dominios
description: Regras comuns e estrutura canônica de pastas de dominios para todos os papéis ao analisar ou gerar artefatos.
applyTo: "dominios/**"
---

# Regras comuns

As travas globais (autorização, não inventar, escopo) estão em [copilot-instructions.md](../copilot-instructions.md).

## Evidência

- Baseie conclusões na fonte localizada e cite arquivo e linha, ou o trecho original.
- Diferencie fato, hipótese e informação não confirmada.
- Sem evidência, registre pendência com o marcador do papel e, se necessário, uma pergunta objetiva.
- Não transforme hipótese em requisito, contrato, regra ou critério de aceite.
- Não declare como executada uma validação que não foi executada.

## Atuação do analista (subagente)

1. Leia somente a referência e o asset recebidos do Donda.
2. Se faltar entrada essencial, devolva ao Donda apenas o item ausente.
3. Execute as etapas da referência dentro do escopo autorizado.
4. Devolva o resultado estruturado conforme o asset: conteúdo, pendências, bloqueios e riscos.
5. Informe arquivos alterados e validações executadas, quando houver.

## Responsabilidades

- Analista: analisa e devolve o resultado; não grava artefatos de análise e não se comunica com o usuário.
- Operador: único a persistir artefatos de análise. Assets são templates imutáveis: copie a estrutura e preencha somente a cópia.
- Arquivos fornecidos pelo usuário (relato, história, `problema.md`) nunca são alterados.
- Reanálise: leia a fonte atual e o artefato anterior, preserve histórico e pendências e substitua somente os artefatos autorizados.
- Status de artefato seguem o contrato global do `operador`.

## Dados sensíveis

- Trate dado de banco, credencial e informação pessoal como sensível: ambiente não produtivo, máscara ou placeholder.

## Estrutura de dominios

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