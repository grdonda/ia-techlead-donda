# Workflow — User Story

## Objetivo

Analisar contexto de negócio e técnico e preencher o template `assets/user-story.md`, gerando um artefato pronto para o Jira.

## Quando usar

- Criar uma nova história de usuário.
- Validar tecnicamente uma história existente.
- Estruturar épico, história e tarefas a partir de um contexto bruto.

## Entradas esperadas

- ID do Jira ou título da demanda.
- Contexto do pedido (texto, imagem, link).
- Links de apoio (Figma, Confluence, repositório, documentação).
- Serviço ou biblioteca alvo, quando aplicável.
- Restrições ou regras já conhecidas.

## Saídas esperadas

- Artefato `output/<jira-id>_user-story.md`.
- Lista de campos `[preencher]`.
- Status global do artefato.

## Executor

- Análise: `developer` (modo user-story).
- Persistência: `operador`.

---

## Passo a passo

### 1. Receber o plano autorizado do Donda

O Donda envia:

- caminho da referência (este arquivo)
- caminho do asset (`skills/developer/assets/user-story.md`)
- alvo (`<jira-id>` e/ou nome da demanda)
- autorização de execução

### 2. Carregar o asset

Ler `skills/developer/assets/user-story.md` e manter a estrutura intacta.

### 3. Delegar para o `developer` (modo user-story)

Prompt para o subagente:

    Processo: user-story
    ID: <jira-id>
    Título: <título>
    Contexto: <contexto fornecido>
    Links de apoio: <links>
    Serviço alvo: <caminho ou repositório>
    Asset: skills/developer/assets/user-story.md

    Se o serviço alvo for informado, leia o serviço antes de preencher a história.
    Procure apenas: ponto de entrada, classes envolvidas, dependências externas, testes existentes e configurações relevantes.
    Não leia o repositório inteiro.

    Retorne JSON estruturado com todos os campos do asset.
    Marque [preencher] onde não houver informação.
    Marque [não aplicável] no campo Feature Toggle se não fizer sentido.
    Liste ao final os campos que ficaram pendentes.

### 4. Receber o JSON do `developer`

Validar se os campos obrigatórios estão presentes:

- ID do Jira
- Título
- Identificação (Eu como / Quero / Para)
- Pelo menos 1 regra de negócio
- Pelo menos 1 critério de aceite
- Pelo menos 1 regra técnica
- Pelo menos 1 risco ou dependência

Se algum campo obrigatório estiver vazio, sinalizar ao Donda antes de persistir.

### 5. Delegar para o `operador`

Prompt para o subagente:

    Autorização: concedida pelo Donda.
    Referência: skills/developer/references/user-story.md
    Asset: skills/developer/assets/user-story.md
    Artefato de saída: output/<jira-id>_user-story.md
    Status inicial sugerido: pendente

    Conteúdo analítico (JSON):
    { ... }

    Regras:
    - Trate o asset como template canônico e imutável. Copie a estrutura para o destino e preencha somente a cópia.
    - Preserve o conteúdo analítico. Não invente informação.
    - Onde o JSON não tiver valor, mantenha [preencher] e registre na seção Pendências.
    - Atualize data-criacao, data-atualizacao e origem.
    - Registre uma linha no Histórico.
    - Use somente os status globais: pendente, em andamento, aguardando usuário, bloqueado, desatualizado, concluído.
    - Retorne: caminho do artefato, operação realizada (criado/atualizado) e status.

### 6. Validar o artefato gerado

- Conferir se o arquivo foi salvo em `output/<jira-id>_user-story.md`.
- Conferir se todas as seções do asset estão presentes.
- Conferir se os campos `[preencher]` foram listados na seção Pendências.

### 7. Retornar ao Donda

Formato de retorno:

    Skill developer - Processo user-story
    Artefato: output/<jira-id>_user-story.md
    Operação: criado / atualizado
    Status: <status global>
    Campos pendentes: [lista]
    Resumo: [1-2 linhas]

---

## Regras

- Nunca preencher o template sem análise prévia do `developer`.
- Nunca inventar informação. Se não souber, marcar `[preencher]`.
- Sempre manter a estrutura do asset intacta.
- Sempre salvar em `output/<jira-id>_user-story.md`.
- Sempre retornar o caminho do artefato e a lista de campos `[preencher]`.
- Se o contexto for insuficiente para preencher a Identificação ou os Critérios de Aceite, parar e pedir ao Donda que solicite mais informação ao usuário antes de persistir.
- Se o campo Feature Toggle não for aplicável, marcar `[não aplicável]` em vez de `[preencher]`.
- Nunca alterar o arquivo de entrada do usuário.

## Campos obrigatórios

- ID do Jira
- Título
- Identificação (Eu como / Quero / Para)
- Pelo menos 1 regra de negócio
- Pelo menos 1 critério de aceite
- Pelo menos 1 regra técnica
- Pelo menos 1 risco ou dependência

## Formato de saída

Artefato markdown salvo em `output/<jira-id>_user-story.md`, com estrutura idêntica ao asset.

## Status globais permitidos

- `pendente`
- `em andamento`
- `aguardando usuário`
- `bloqueado`
- `desatualizado`
- `concluído`
