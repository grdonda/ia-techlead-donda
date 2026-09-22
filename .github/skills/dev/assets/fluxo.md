# Fluxo — <nome>

## Objetivo

<descrição breve da funcionalidade>

## Entrada

* <endpoint/evento/consumer/job>

## Flowchart

```mermaid
flowchart TD
    A["Entrada"] --> B["Componente"]
    B --> C["Componente"]
    C --> D["Saída"]
```

## Sequence

```mermaid
sequenceDiagram
    participant A as Entrada
    participant B as Componente
    participant C as Componente
    participant D as Saída

    A->>B: chamada
    B->>C: chamada
    C-->>B: retorno
    B-->>A: resposta
```

## Dependências

* <serviço>
* <banco>
* <evento/mensageria>

## Saída

* <resposta/resultado>

## Pontos desconhecidos

* <item>
