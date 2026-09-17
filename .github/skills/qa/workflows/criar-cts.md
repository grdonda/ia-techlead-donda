# Workflow - Criar Cenários de Teste

## Objetivo

Criar cenários de testes funcionais manuais a partir da história de negócio, requisitos, regras de negócio, critérios de aceite e informações técnicas disponíveis.

Cada cenário deve ser gerado utilizando obrigatoriamente o template:

    CT00N - titulo.md

O template define o formato final do cenário e deve ser preservado.

## 1. Analisar a história

Antes de criar os cenários:

* Ler a história e seus critérios de aceite.
* Identificar requisitos funcionais.
* Identificar regras de negócio.
* Identificar fluxos principais e alternativos.
* Identificar comportamentos esperados.
* Identificar possíveis cenários negativos e de borda.
* Identificar dependências relevantes.
* Identificar informações técnicas necessárias para compreender o comportamento.

Quando aplicável:

* Consultar os artefatos PM e DEV quando existirem.

Não analisar arquivos sem relação com a demanda.

## 2. Identificar cobertura

Para cada requisito, regra de negócio ou critério de aceite:

* Identificar pelo menos um cenário de teste quando houver comportamento testável.
* Identificar cenários positivos.
* Identificar cenários negativos quando aplicável.
* Identificar cenários de borda quando houver risco relevante.
* Identificar cenários de regressão quando houver impacto em funcionalidades existentes.

Evitar criar cenários duplicados.

Priorizar cenários de maior risco e impacto.

Preservar os cenários existentes.

## 3. Definir o cenário

Cada CT deve representar um comportamento específico e testável.

O cenário deve possuir:

* Objetivo claro.
* Pré-requisitos identificáveis.
* Condições de entrada conhecidas.
* Ação executada.
* Resultado esperado.

* Não combinar comportamentos independentes no mesmo CT.
* Quando dois fluxos possuem regras ou resultados diferentes, criar CTs separados.

## 4. Organização, arquivo e numeração dos cenários

Todo cenário de teste deve ser criado dentro da estrutura:

    dominios/<PROJETO>/historias/<JIRA-ID>/testes/<assunto>/cts/<cenario>.md

### Assunto

O `<assunto>` representa o agrupamento funcional do cenário.

Exemplo:

    dominios/<PROJETO>/historias/<JIRA-ID>/testes/cadastro/cts/
    dominios/<PROJETO>/historias/<JIRA-ID>/testes/consulta/cts/
    dominios/<PROJETO>/historias/<JIRA-ID>/testes/autenticacao/cts/

* Utilizar um assunto existente quando ele representar corretamente o cenário.
* Criar um novo assunto somente quando não existir um agrupamento adequado.
* Não criar assuntos duplicados ou com nomes equivalentes.

### Nome do arquivo

O arquivo deve seguir a nomenclatura:

    CT00N - <TÍTULO>.md

Exemplo:

    dominios/<PROJETO>/historias/<JIRA-ID>/testes/cadastro/cts/CT001 - cadastrar cliente.md

O título do arquivo deve corresponder ao título definido dentro do cenário.

### Numeração

* A numeração dos cenários é independente por assunto.
* A contagem deve reiniciar em CT001 para cada assunto.

Exemplo:

    dominios/<PROJETO>/historias/<JIRA-ID>/testes/cadastro/cts/
    ├── CT001 - cadastrar cliente.md
    ├── CT002 - alterar cliente.md
    └── CT003 - excluir cliente.md

    dominios/<PROJETO>/historias/<JIRA-ID>/testes/consulta/cts/
    ├── CT001 - consultar cliente.md
    └── CT002 - consultar cliente inexistente.md

Nesse caso, CT001 pode existir nos dois assuntos porque a sequência é controlada individualmente por assunto.

### Regra para determinar o próximo número

Antes de criar um cenário:

1. Identificar o assunto.
2. Verificar os arquivos existentes em `dominios/<PROJETO>/historias/<JIRA-ID>/testes/<assunto>/cts/`.
3. Identificar o maior número de CT existente.
4. Utilizar o próximo número após o maior CT existente.
5. Caso não existam cenários no assunto, iniciar em CT001.

Exemplo:

Se existirem:

    dominios/<PROJETO>/historias/<JIRA-ID>/testes/cadastro/cts/
    ├── CT001 - cadastrar cliente.md
    ├── CT002 - alterar cliente.md
    └── CT005 - excluir cliente.md

O próximo cenário deve utilizar:

    CT006

Não utilizar CT003 apenas por ser o primeiro número ausente.

A sequência deve continuar a partir do maior CT existente.

### Validação

Antes de salvar o arquivo:

* Confirmar que o assunto está correto.
* Confirmar que a pasta `dominios/<PROJETO>/historias/<JIRA-ID>/testes/<assunto>/cts/` existe ou deve ser criada.
* Confirmar o próximo número do CT.
* Confirmar que não existe outro arquivo com o mesmo CT no assunto.
* Confirmar que o nome do arquivo corresponde ao título do cenário.
* Preservar os cenários existentes.

## 5. Preencher o template

Utilizar exatamente a estrutura definida em:

    CT00N - titulo.md

Manter obrigatoriamente as seguintes seções:

* Título
* Summary
* Descrição
* Pré-requisitos
* Gherkin
* Cucumber (Xray)
* Outras informações para cadastro

Não remover, renomear ou criar novas seções no template sem solicitação explícita.

## 6. Summary

O campo Summary deve conter o mesmo título do CT.

Formato:

    CT001 - <TÍTULO>

O Summary deve ser curto, objetivo e compatível com o padrão Jira/Xray.

## 7. Descrição

Descrever objetivamente a cobertura do teste.

A descrição deve responder:

* O que está sendo validado?
* Qual regra, requisito ou comportamento está sendo coberto?

Não repetir todo o Gherkin.

## 8. Pré-requisitos

Informar todos os pré-requisitos necessários para execução do cenário.

Exemplos:

* Usuário cadastrado.
* Usuário autenticado.
* Registro existente.
* Serviço disponível.
* Massa específica disponível.
* Permissão necessária.

Quando não houver pré-requisitos específicos:

    N/A

Não inventar dados ou condições não identificadas na análise.

## 9. Gherkin

Utilizar Gherkin para descrever o cenário funcional.

Formato:

    Feature: <nome da funcionalidade>
        Scenario: <nome do cenário>
            Given <condição>
            When <ação>
            Then <resultado>

O Gherkin deve representar o comportamento funcional completo do cenário.

Regras:

* Given representa contexto ou condição inicial.
* When representa a ação.
* Then representa o resultado esperado.
* Utilizar And quando necessário.
* Evitar passos técnicos desnecessários.
* Priorizar comportamento observável.
* Não colocar implementação interna no lugar do comportamento funcional.

## 10. Cucumber (Xray)

O bloco Cucumber (xray) deve conter somente os passos necessários para cadastro do cenário no Xray.

Formato:

    Given <condição>
    When <ação>
    Then <resultado>

Não incluir:

    Feature:
    Scenario:

Manter o conteúdo consistente com o cenário definido no Gherkin.

## 11. Outras informações para cadastro

Manter obrigatoriamente os campos definidos pelo template:

    Company: Bradesco
    Squad: EQUALIPJ
    Prioridade: HIGH
    Issue: <JIRA-ID>

* Os valores devem ser preenchidos conforme as informações disponíveis para a história.
* Não assumir informações que não estejam disponíveis.
* Não criar novos campos.

## 12. Validação antes da entrega

Antes de finalizar cada CT, validar:

* [ ] Número do CT correto.
* [ ] Título objetivo.
* [ ] JIRA-ID correto.
* [ ] Summary corresponde ao título.
* [ ] Descrição representa a cobertura.
* [ ] Pré-requisitos definidos ou N/A.
* [ ] Gherkin válido.
* [ ] Cucumber compatível com o Gherkin.
* [ ] Informações de cadastro presentes.
* [ ] Não existem informações inventadas.
* [ ] Não existem cenários duplicados.
* [ ] O cenário possui requisito, regra ou critério de aceite relacionado.

## 13. Gaps e pendências

Quando não houver informação suficiente para criar um cenário corretamente:

* Não inventar a informação.
* Informar ao usuário.
* Registrar a pendência.
* Indicar qual informação precisa ser validada.

Exemplos:

    Necessário validar regra de negócio para usuário sem cadastro.
    Necessário confirmar status HTTP esperado para resposta de erro.
    Necessário confirmar massa necessária para execução do cenário.

## 14. Eficiência

* Analisar somente informações relevantes para a história.
* Evitar leitura desnecessária do repositório.
* Evitar cenários redundantes.
* Não repetir informações já conhecidas.
* Não gerar CTs para comportamentos não testáveis ou sem evidência.
* Priorizar cobertura de maior risco.
* Utilizar o template existente em vez de gerar estruturas alternativas.
