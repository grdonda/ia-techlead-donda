---
projeto: <PROJETO>
jira: <JIRA-ID>
etapa: jmeter
status: pendente
data-criacao: <AAAA-MM-DD HH:mm>
data-atualizacao: <AAAA-MM-DD HH:mm>
responsavel: qa
---

# Plano de Teste de Carga

## História

    JIRA-ID: <JIRA-ID>
    Serviço: <SRV>
    Endpoint: <ENDPOINT>
    Método: <GET|POST|PUT|DELETE>

## Objetivo

Descrever o objetivo do teste de carga para o fluxo da história.

## Cenário

Descrever resumidamente o fluxo que será submetido à carga.

## Dados de entrada

Informar somente os dados necessários para executar o fluxo.

Payload:

    <JSON ou referência ao payload>

Autenticação:

    <tipo de autenticação ou N/A>

## Perfis de carga

### Leve

Objetivo: validar o comportamento básico do fluxo sob baixa carga.

    Usuários: <quantidade>
    RPS: <quantidade>
    Ramp-up: <tempo>
    Duração: <tempo>

### Média

Objetivo: avaliar o comportamento do fluxo em carga representativa.

    Usuários: <quantidade>
    RPS: <quantidade>
    Ramp-up: <tempo>
    Duração: <tempo>

### Agressiva

Objetivo: avaliar o comportamento do fluxo sob carga elevada.

    Usuários: <quantidade>
    RPS: <quantidade>
    Ramp-up: <tempo>
    Duração: <tempo>

## Critérios de sucesso

Definir somente critérios confirmados para a história.

* Tempo de resposta: <valor ou N/A>
* P95: <valor ou N/A>
* P99: <valor ou N/A>
* Taxa de erro: <valor ou N/A>
* Throughput: <valor ou N/A>

## Dependências

Listar dependências relevantes para execução e interpretação do teste.

## Limitações

Registrar limitações conhecidas que possam afetar o resultado.

## Evidências

Referenciar as fontes utilizadas para definir o plano.

Exemplos:

* História / Task
* OpenAPI
* curl
* Código do microserviço
* Outros documentos de contexto
