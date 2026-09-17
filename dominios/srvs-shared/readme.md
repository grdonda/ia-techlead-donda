# SRVS Shared Domain

Aqui ficam as bibliotecas compartilhadas internas usadas pelos demais microsservicos.

## Estrutura canonica

- `analises/`: analises tecnicas das bibliotecas.
- `estudos/`: estudos consolidados das bibliotecas.
- `<LIB-NAME>/`: repositorio interno da biblioteca, obtido do GitHub com autorizacao explicita.

```markdown
c:\workspace\java\workspace\
└── dominios/
    ├── srvs-shared/
    │   ├── analises/
    │   │   └── <LIB-NAME>_analise.md
    │   ├── estudos/
    │   │   └── <LIB-NAME>_estudo.md
    │   └── <LIB-NAME>/
    │       └── repositorio interno da biblioteca
```
