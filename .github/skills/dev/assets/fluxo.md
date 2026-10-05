# Mapeamento de fluxo

Mapeamento de fluxo de um microserviço ou lib

## Escopo

- Projeto: `<projeto ou Nao aplicavel>`
- Serviço ou biblioteca: `<nome>`
- Repositório: `<caminho no workspace>`
- Endpoint ou operação: `<metodo e caminho ou nome da operacao>`
- Branch: `<git branch analisada ou NAO VERIFICADO>`

## Entradas

- Método e caminho do endpoint ou operação de entrada
- Parâmetros de rota, query, headers e corpo, conforme identificados
- Restrições de autenticação/autorização observadas, quando aplicável

## Contratos

    `<corpo da requisição>`
    `<resposta da requisição>`

## Chamada cURL (Bruno)

    ```sh
    <chamada cURL conforme exemplo localizado>
    ```

## Fluxo interno

Descrever em ordem o processamento desde a entrada até o retorno. Incluir validações, decisões, transformações, persistência e chamadas externas somente quando localizadas nas fontes.

## Fluxograma

Representar a entrada, os passos internos relevantes, decisões, comunicações, caminhos de erro e retorno.

    ```mermaid
    flowchart TD
        Entrada[Endpoint ou operacao de entrada] --> Processamento[Etapas confirmadas no codigo]
        Processamento --> Retorno[Retorno observado]
    ```

## Diagrama de Sequencia

Representar participantes, chamadas, respostas e retornos na ordem observada no código. Incluir caminhos de erro quando identificáveis.

    ```mermaid
    sequenceDiagram
        actor Cliente
        participant Entrada as Endpoint ou operacao
        Cliente->>Entrada: Requisicao
        Entrada-->>Cliente: Response observada
    ```

## Comunicações e dependências

Listar serviços, bibliotecas, eventos, estados e processos assíncronos ou externos identificados, mantendo cada processo assíncrono ou externo separado do fluxo principal.

- Serviços e bibliotecas envolvidos: `<nome e uso no fluxo; NAO VERIFICADO se a biblioteca não estiver clonada>`
- Eventos e estados: `<evidências ou NAO LOCALIZADO>`
- Processos assíncronos ou externos: `<nome, gatilho e retorno; ou NAO LOCALIZADO>`

## Erros e excecoes

- `<condicao, tratamento e retorno observados; ou NAO LOCALIZADO>`

## Observabilidade

- Logs, métricas, traces e identificadores de correlação encontrados: `<evidências ou NAO LOCALIZADO>`
