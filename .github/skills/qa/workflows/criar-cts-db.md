# Criar Cenário de Teste com Banco (CT-DB)

## Objetivo

Criar um cenário de teste que descreva a preparação, o estado ou a validação de dados de banco necessários para um CT funcional.

O CT-DB documenta a necessidade de dados e o resultado esperado no banco. A preparação de massa e os scripts SQL autorizados são responsabilidade da skill DBA.

## Pré-requisitos

1. Confirmar o projeto, a história e a autorização explícita.
2. Ler a história, os critérios de aceite e o CT funcional relacionado, quando existir.
3. Identificar a necessidade de estado, registro, relacionamento ou limpeza de dados.
4. Não inventar schema, tabela, coluna, chave, filtro ou valores de banco.

## Organização e nomenclatura

Salvar o cenário em:

    dominios/<PROJETO>/historias/<JIRA-ID>/testes/<assunto>/dbs/CT00N - DB - <TITULO>.md

Utilizar o asset [cts-db.md](../assets/cts-db.md) como template e preservar suas seções.

O número do CT-DB deve corresponder ao CT funcional relacionado quando houver vínculo direto. Quando não houver CT funcional, registrar a justificativa e manter a numeração do assunto.

## Conteúdo obrigatório

Preencher:

* título objetivo do CT-DB;
* história relacionada;
* resumo e descrição da necessidade de banco;
* pré-requisitos;
* estado ou massa necessária;
* Gherkin do estado inicial, ação e resultado esperado quando aplicável;
* Cucumber compatível quando o cenário for cadastrado no Xray;
* informações de cadastro confirmadas.

## Regras de banco

* Descrever apenas dados e comportamentos confirmados.
* Não registrar senha, credencial ou dado sensível em texto puro.
* Não incluir SQL de alteração neste artefato sem autorização e confirmação do contexto.
* Solicitar a skill DBA quando for necessário consultar, inserir, atualizar, validar ou limpar dados.
* Não acionar a skill DBA automaticamente.

## Validação antes da entrega

* Confirmar a relação com a história e o CT funcional, quando existir.
* Confirmar que a pasta e o nome do arquivo seguem a estrutura canônica.
* Confirmar que a massa necessária está descrita sem inventar dados.
* Confirmar que o resultado esperado é verificável.
* Registrar pendências quando schema, registros ou filtros dependerem de validação.
* Atualizar `status`, `data-atualizacao`, `responsavel` e pendências.

Ao concluir, salve o artefato, informe a dependência da DBA quando aplicável e aguarde a próxima solicitação.
