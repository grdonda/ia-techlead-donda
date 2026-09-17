---
tipo: referencia-estrutura-canonica
responsavel: techlead
---

# Estrutura Canonica de Dominio e Historia

Este arquivo e a referencia usada pelo TechLead para comparar projetos existentes. A comparacao valida a estrutura real de `dominios/` contra os caminhos usados pelos workflows.

## Projeto

```text
dominios/<PROJETO>/
|-- contexto/
|   |-- projeto.md
|   |-- contratos/
|   |-- db/
|   `-- figma/
|-- srvs/
|   `-- estudos/
`-- historias/
```

`dominios/srvs-shared/` e um dominio compartilhado e nao deve ser tratado como historia de um projeto.

## Bibliotecas compartilhadas

```text
dominios/srvs-shared/
|-- analises/
|   `-- <LIB-NAME>_analise.md
|-- estudos/
|   `-- <LIB-NAME>_estudo.md
`-- <LIB-NAME>/
    `-- repositorio interno da biblioteca obtido do GitHub
```

Cada diretorio `<LIB-NAME>/` representa uma biblioteca compartilhada interna que pode ser usada pelos demais microsservicos. O TechLead valida sua presenca, nome, origem GitHub registrada e correspondencia com analises e estudos. Download, clone ou alteracao do repositorio dependem de autorizacao explicita.

Quando uma historia for informada, `dominios/<PROJETO>/historias/<JIRA-ID>/` e a raiz de leitura. `dominios/<PROJETO>/contexto/` e a excecao permitida quando o workflow exigir informacoes do projeto; o acesso deve ser informado ao usuario.

## Historia

```text
dominios/<PROJETO>/historias/<JIRA-ID>/
|-- <JIRA-ID>.md
|-- contexto/
|   |-- anexos/
|   |-- db/
|   `-- srvs-contratos/
|-- refinamento/
|-- tasks/
|-- testes/
|   |-- <assunto>/
|   |   |-- cts/
|   |   `-- dbs/
|   `-- jmeter/
`-- code-review/
```

Os subdiretorios de `testes/` e seus artefatos sao responsabilidade das skills especializadas. O TechLead deve verificar se existem e apontar ausencias, sem criar cenarios ou massa.

## Artefatos derivados previstos

- Mapeamento tecnico: `contexto/<JIRA-ID>_mapeamento-tecnico.md`.
- Estudos de SRV: `dominios/<PROJETO>/srvs/estudos/`.
- Estudos de biblioteca compartilhada: `dominios/srvs-shared/estudos/`.
- Analises de biblioteca compartilhada: `dominios/srvs-shared/analises/`.
- Repositorios internos de bibliotecas compartilhadas: `dominios/srvs-shared/<LIB-NAME>/`.
- Tasks: `tasks/` dentro da historia.
- Cenarios de teste: `testes/<assunto>/cts/` dentro da historia.
- Cenarios de banco: `testes/<assunto>/dbs/` dentro da historia.
- Testes de carga: `testes/jmeter/` dentro da historia.
- Code review: `code-review/` dentro da historia.

## Regra de comparacao

Classifique cada caminho como `presente`, `ausente`, `fora de contexto` ou `nao aplicavel`. A ausencia de um caminho nao e erro; um caminho existente fora desta estrutura e divergencia. Nao presuma que um arquivo presente e valido: confira caminho, nome, frontmatter e referencias dos workflows.

Se workflows ou a estrutura real indicarem caminhos conflitantes, registre a divergencia e nao escolha silenciosamente um deles. O workflow de carga do QA deve usar `dominios/<PROJETO>/historias/<JIRA-ID>/testes/jmeter/`, conforme a estrutura canonica.
