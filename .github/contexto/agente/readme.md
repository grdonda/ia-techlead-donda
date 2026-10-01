# Agente Donda

O Donda interpreta a solicitação, identifica a skill e o workflow aplicável e aguarda a confirmação do usuário antes de executar.

## Fluxo Geral

```text
Usuário -> Donda -> Skill -> Workflow -> Agentes especializados
-> Artefato no workspace -> Usuário coordena a próxima etapa
```

O fluxo é assíncrono. Uma skill não aciona automaticamente outra skill. O usuário analisa o artefato gerado e solicita a próxima etapa.

## Comandos de Exemplo

As solicitações abaixo são exemplos de linguagem natural para o Donda. Informe sempre o projeto e, quando aplicável, a história.

### PM

```text
Avalie os anexos do projeto <projeto> e da história <JIRA-ID>.
Faça o refinamento da história <JIRA-ID> do projeto <projeto>.
Gere a CSD da história <JIRA-ID> do projeto <projeto>.
```

### TechLead

```text
Crie o projeto <projeto>.
Crie a história <JIRA-ID> no projeto <projeto>.
Verifique o status da história <JIRA-ID> do projeto <projeto>.
Mapeie as dependências técnicas da história <JIRA-ID> do projeto <projeto>.
Estude o SRV <SRV-NAME> para a história <JIRA-ID> do projeto <projeto>.
Atualize o estudo do SRV <SRV-NAME> após a implementação da história <JIRA-ID>.
Crie as tasks técnicas da história <JIRA-ID> do projeto <projeto>.
```

### DEV

```text
Analise tecnicamente o SRV ou a biblioteca <DEPENDENCIA> para a implementação da história <JIRA-ID> do projeto <projeto>.
Crie a task DEV da história <JIRA-ID> do projeto <projeto>.
Implemente a task DEV <TASK-ID> da história <JIRA-ID> do projeto <projeto>.
Registre as evidências da implementação da task <TASK-ID>.
Faça o code review da task <TASK-ID> da história <JIRA-ID> do projeto <projeto>.
```

### QA

```text
Analise a testabilidade da história <JIRA-ID> do projeto <projeto>.
Crie os cenários funcionais da história <JIRA-ID> do projeto <projeto>.
Crie a matriz de cobertura da história <JIRA-ID> do projeto <projeto>.
Crie o plano de carga da história <JIRA-ID> do projeto <projeto>.
Solicite a preparação da massa do CT <CT-ID> da história <JIRA-ID> do projeto <projeto>.
Crie o CT-DB do CT <CT-ID> da história <JIRA-ID> do projeto <projeto>.
Valide os testes da história <JIRA-ID> do projeto <projeto>.
```

### DBA

```text
Avalie o contexto de banco da história <JIRA-ID> do projeto <projeto>.
Solicite os CSVs necessários para a história <JIRA-ID> do projeto <projeto>.
Faça a pré-análise de massa da história <JIRA-ID> do projeto <projeto>.
Prepare a massa do CT <CT-ID> e CT-DB <CT-DB-ID> da história <JIRA-ID> do projeto <projeto>.
Valide e limpe a massa do CT-DB <CT-DB-ID> da história <JIRA-ID> do projeto <projeto>.
```

O Donda identifica a skill e o workflow, informa o contexto que será consultado e aguarda confirmação. Somente após a confirmação, carrega a skill e executa a etapa autorizada.

## Como Solicitar

Informe sempre o projeto e, quando aplicável, a história, task, SRV ou CT relacionado.

O Donda deve:

1. Identificar a skill e o workflow aplicáveis.
2. Informar os artefatos e o contexto que serão consultados.
3. Aguardar confirmação explícita antes de criar ou alterar arquivos.
4. Encaminhar a execução ao analista e ao operador da skill.
5. Salvar o artefato no caminho definido e aguardar a próxima solicitação.

Uma skill não aciona outra automaticamente. O usuário coordena a próxima etapa após revisar o artefato gerado.

## Mapa das Skills

- PM: refinamento, CSD, dúvidas, lacunas e suposições da história.
- TechLead: estrutura, dependências, estudos de SRVs, bibliotecas e tasks.
- DEV: análise técnica para criação ou implementação de task DEV, evidências e code review.
- QA: testabilidade, cenários funcionais, CT-DB, validação de testes, matriz de cobertura e carga.
- DBA: contexto de banco, CSVs e massa SQL Server para CT/CT-DB autorizados.

Os artefatos persistidos são a fonte de continuidade do processo; a conversa não substitui os arquivos do workspace.

## Início

1. Solicite ao TechLead a criação do projeto ou da história.
2. O TechLead cria a estrutura canônica.
   - Estado do projeto: `dominios/<projeto>/contexto/projeto.md`.
   - Estado da história: frontmatter em `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md`.
3. Salve os anexos do projeto em `dominios/<projeto>/contexto/`.
4. Salve os anexos da história em `dominios/<projeto>/historias/<JIRA-ID>/contexto/`.
5. Copie a história integralmente para `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md`.
6. Registre na história se há necessidade de arquivos ou dados de massa para testes.
7. Solicite ao Donda o refinamento ou a CSD.

## Skill PM

Use para organizar ou desambiguar uma história.

### Refinamento

```text
Donda -> PM -> pm-analista -> pm-operador -> refinamento
```

1. O `pm-analista` analisa a história e os anexos.
2. O `pm-operador` preenche e salva o artefato de refinamento.
3. Solicite ao TechLead o estudo dos SRVs e bibliotecas identificados.
4. Após os estudos, solicite novo refinamento quando necessário.

### CSD

```text
Donda -> PM -> pm-analista -> pm-operador -> CSD
```

1. O `pm-analista` identifica certezas, suposições, dúvidas e lacunas.
2. O `pm-operador` preenche e salva a matriz CSD.
3. Esclareça os itens pendentes com o PM.
4. Solicite novo CSD quando houver respostas.

Refinamento e CSD devem consultar o inventário de anexos da história e não reclassificar os mesmos arquivos.

## Skill TechLead

Use para preparar o workspace, estudar dependências e criar tasks.

1. Criar novo projeto.
2. Criar nova história ou evolução.
3. Verificar o status dos artefatos persistidos.
4. Mapear dependências técnicas antes dos estudos individuais.
5. Estudar SRVs do projeto em `dominios/<projeto>/srvs/estudos/`.
6. Estudar bibliotecas compartilhadas em `dominios/srvs-shared/estudos/`.
7. Criar tasks após o PM concluir o refinamento sem dúvidas bloqueantes.
8. Atualizar os estudos após a implementação.

## Skill DEV

1. Leia a história, o refinamento, os estudos e a task DEV.
2. Analise ou implemente somente a task autorizada.
3. Registre evidências, testes e observabilidade.
4. Solicite QA após a implementação.

## Skill QA

1. Leia a história, o refinamento, os contratos e a implementação.
2. Crie os cenários funcionais ou de carga.
3. Solicite DBA quando houver necessidade de massa de banco.
4. Execute ou solicite a execução dos testes após a preparação dos dados.

## Skill DBA

O DBA atua sobre SQL Server e somente prepara massa quando existe CT e CT-DB prontos. A exceção é a pré-análise antecipada da história, sem execução de comandos.

1. Leia a história, o refinamento/CSD, os cenários e os arquivos em `dominios/<projeto>/contexto/db/` e `dominios/<projeto>/historias/<JIRA-ID>/contexto/db/`.
2. Classifique o contexto como suficiente, parcial ou insuficiente.
3. Quando faltarem dados, solicite explicitamente o CSV necessário e proponha um `SELECT` filtrado pela estrutura confirmada.
4. Correlacione referências confirmadas, como telefone, CPF, CNPJ, segmento e tipo de cliente PF/PJ, MEI/SME.
5. Prepare comandos para `SELECT`, `INSERT` e `UPDATE` somente com tabela, coluna, chave e filtro confirmados.
6. Registre `SET XACT_ABORT ON`, transação, validação antes/depois, `COMMIT`, `ROLLBACK` e limpeza seletiva.
7. Use dados mascarados ou placeholders; nunca registre senha ou credencial em texto puro.
8. Salve o artefato em `dominios/<projeto>/historias/<JIRA-ID>/testes/<assunto>/dbs/`.
9. Entregue ao QA para execução do cenário e aguarde a próxima solicitação.

Fluxo normal: `QA -> DBA -> QA`.

Fluxo de exceção: `História -> DBA (pre-analisar-massa) -> QA cria CT/CT-DB -> DBA prepara massa`.

### Arquivos de Contexto

- Projeto: `dominios/<projeto>/contexto/db/`.
- História: `dominios/<projeto>/historias/<JIRA-ID>/contexto/db/`.
- Cenário de banco: `dominios/<projeto>/historias/<JIRA-ID>/testes/<assunto>/dbs/`.

## Status dos Artefatos

Todo artefato deve registrar `status`, `data-criacao`, `data-atualizacao`, `responsavel`, `projeto` e `jira` quando aplicável.

Status permitidos: `pendente`, `em andamento`, `aguardando usuário`, `concluído`, `bloqueado` e `desatualizado`.

Transições esperadas: `pendente -> em andamento -> concluído`; use `aguardando usuário` quando faltar informação ou autorização, `bloqueado` quando houver impedimento e `desatualizado` quando uma entrada mudar.

Ao retomar uma etapa, leia o artefato mais recente. Corrija somente o status pendente ou bloqueado, atualize `data-atualizacao`, preserve o histórico e aguarde nova solicitação ao finalizar.

Antes de iniciar uma etapa, leia os artefatos existentes e use o mais recente como entrada. O processo não depende da memória da conversa.

Para criação de projeto e história, os arquivos de estado acima são a fonte primária; a existência das pastas confirma a estrutura, mas não substitui `status`, datas, responsável e pendências.
