# Mapeamento de Fluxo

## Objetivo

Mapear os fluxos técnicos das funcionalidades solicitadas a partir do código e gerar artefatos individuais em Markdown, com representações `flowchart` e `sequence` em Mermaid.

## Processo

1. Confirme o contexto autorizado.
2. Identifique os pontos de entrada da funcionalidade:
   - endpoint/controller;
   - consumer/listener;
   - evento;
   - job.
3. Considere cada ponto de entrada funcional como um fluxo técnico independente.
4. Para uma entrada HTTP explicitamente informada, localize primeiro o método/controller pelo método HTTP e caminho exatos antes de realizar buscas amplas.
5. Para cada ponto de entrada:
   - delegue a análise ao `dev-analista`;
   - receba um único `Modelo Factual`;
   - determine a identidade canônica do fluxo;
   - determine o artefato correspondente;
   - aplique a política de reconciliação;
   - delegue a persistência ao `dev-operador`.
6. Use `assets/fluxo.md` como template estrutural do artefato.
7. Preserve somente fatos confirmados pelo `Modelo Factual`.
8. Valide Mermaid antes da persistência.
9. Quando a execução for em massa, preserve a ordem dos fluxos identificados e dos artefatos gerados.
10. Ao concluir, informe o resultado consolidado.

## Identidade Canônica do Fluxo

A identidade canônica deve representar a entrada funcional, e não o nome do arquivo existente.

### HTTP

Para endpoints HTTP, use:

`<método HTTP> <rota normalizada>`

Exemplos:

- `POST /api/auth/login`
- `GET /api/users/me`
- `PATCH /api/users/{id}`

### Consumer ou Listener

Use a combinação das informações que identificam inequivocamente a entrada consumidora, por exemplo:

- tópico/fila;
- evento;
- handler/consumer quando necessário para desambiguação.

### Evento

Use o tipo do evento e o consumidor/handler quando necessário para identificar a entrada.

### Job

Use o identificador funcional do job e seu trigger quando necessário para desambiguação.

A identidade canônica deve ser derivada do ponto de entrada confirmado pelo `dev-analista`.

## Política de Reconciliação de Artefatos

Para cada fluxo identificado, determine o estado do artefato correspondente.

### Criar

Crie um novo arquivo quando:

- o fluxo foi confirmado;
- não existe artefato correspondente à mesma identidade canônica.

Use:

`estudos/<srv>/<ordem>-<srv>-<fluxo-identificado>.md`

O nome deve ser normalizado em `kebab-case`.

### Atualizar

Atualize integralmente o arquivo existente quando:

- a identidade canônica for exatamente a mesma;
- o arquivo representar o mesmo fluxo funcional.

A atualização deve substituir integralmente o conteúdo do arquivo.

Não faça append, prepend ou edição parcial.

### Conflito

Considere como conflito quando:

- existirem dois ou mais arquivos candidatos para a mesma identidade canônica;
- não for possível determinar qual é o artefato oficial;
- um arquivo existente possuir identidade incompatível com a entrada atual;
- a relação entre o arquivo encontrado e o fluxo atual não puder ser confirmada.

Em caso de conflito:

1. não escolha arbitrariamente um arquivo;
2. não sobrescreva arquivos candidatos;
3. não remova arquivos;
4. informe os candidatos encontrados;
5. solicite decisão do usuário.

### Arquivo não correspondente

Quando existir arquivo no diretório e ele não puder ser associado com segurança a nenhum fluxo identificado na execução:

- não remova;
- não sobrescreva;
- não renomeie;
- não reutilize;
- registre como `artefato não reconciliado`.

Arquivos não reconciliados não devem bloquear a geração de novos fluxos, salvo quando houver conflito de identidade.

### Remoção

Não remova artefatos automaticamente durante o mapeamento.

A remoção somente pode ocorrer quando o usuário autorizar explicitamente uma operação de limpeza ou reconciliação destrutiva.

Exemplo de autorização:

`reconciliar e remover artefatos órfãos`

Sem essa autorização, preserve os arquivos e reporte-os.

## Pergunta ao Usuário

O workflow pode solicitar decisão ao usuário somente quando a decisão não puder ser determinada com segurança ou quando houver uma operação destrutiva.

Pergunte quando:

- houver conflito entre múltiplos artefatos candidatos;
- houver ambiguidade sobre qual arquivo representa o fluxo;
- houver solicitação de remoção de arquivos sem autorização explícita;
- uma decisão de escopo for indispensável para continuar.

Não pergunte quando:

- o fluxo novo não possui artefato correspondente;
- existe exatamente um artefato da mesma identidade canônica;
- o comportamento de criar ou atualizar estiver determinado pelas regras deste workflow.

A pergunta deve apresentar somente as opções necessárias para a decisão.

## Descoberta de Fluxos

1. Identifique somente os pontos de entrada solicitados.
2. Em execução em massa, identifique todos os pontos de entrada funcionais do SRV autorizado.
3. Não transforme estruturas internas em fluxos:
   - Controller sem endpoint adicional;
   - Service;
   - Use Case;
   - Component;
   - Repository;
   - Filter;
   - Interceptor;
   - Rate Limit;
   - Auditoria;
   - Migration.
4. Não inclua entradas operacionais, como Actuator ou Swagger, salvo solicitação explícita.
5. Não misture fluxos diferentes no mesmo arquivo.
6. Cada endpoint HTTP deve possuir um fluxo individual.
7. Cada consumer, listener, evento ou job que seja ponto de entrada deve possuir um fluxo individual.
8. Não una endpoints distintos apenas porque pertencem à mesma jornada funcional.
9. Não mapeie o projeto inteiro além do escopo autorizado.

## Mapeamento Técnico

Para cada fluxo:

1. O `dev-analista` deve seguir somente as chamadas e interações realmente executadas.
2. O `dev-analista` deve produzir um único `Modelo Factual`.
3. O `Modelo Factual` é a única fonte de fatos do artefato.
4. O `flowchart` representa a estrutura do caminho técnico.
5. O `sequence` representa a ordem temporal das interações.
6. Os dois diagramas representam o mesmo fluxo funcional, mas não precisam possuir as mesmas arestas.
7. Preserve as pré-condições e dependências estruturais identificadas pelo `dev-analista`.
8. Não transforme etapas condicionais ou sequenciais em caminhos paralelos.
9. Caminhos de erro devem ser representados quando confirmados e relevantes.
10. Erros e saídas devem utilizar nós concretos no Mermaid.
11. Não utilize `subgraph`.
12. Não invente relações, componentes ou comportamento.
13. Quando uma relação não puder ser confirmada, registre `DESCONHECIDO`.

## Dependências

A seção `Dependências` deve conter somente recursos ou integrações externos ao limite do componente analisado e concretamente confirmados pelo `Modelo Factual`.

Não classifique como dependência externa:

- Controller;
- Service;
- Use Case;
- Component;
- Repository;
- Filter;
- Interceptor;
- DTO;
- entidade;
- classe de domínio;
- biblioteca interna;
- framework interno;
- abstração interna.

Quando nenhuma dependência externa concreta estiver confirmada, escreva:

`Nenhuma dependência externa confirmada.`

Não inferira banco, cache, broker, Redis, Kafka ou outra infraestrutura apenas pela presença de bibliotecas, frameworks ou abstrações.

## Configuração e Contratos

O mapeamento de fluxo não deve gerar contratos externos ou CURL nesta etapa.

Quando o fluxo contiver comunicação externa, o `dev-analista` pode registrar fatos confirmados sobre a comunicação no `Modelo Factual`, mas a extração formal do contrato pertence a workflow específico de contratos.

Arquivos de configuração, como:

- `application.properties`;
- `application.yml`;
- `application-*.properties`;
- `application-*.yml`;

podem complementar informações da comunicação, mas não provam isoladamente que uma integração participa do fluxo.

A participação da integração deve ser confirmada pelo código executado.

## Persistência

Para cada fluxo confirmado:

1. escolha o artefato correspondente conforme a Política de Reconciliação;
2. delegue a persistência ao `dev-operador`;
3. informe ao operador:
   - identidade canônica;
   - operação determinada: `criar` ou `atualizar`;
   - caminho do artefato;
   - `Modelo Factual`;
   - template;
   - restrições relevantes;
4. não permita que o operador altere a decisão de reconciliação;
5. não permita que o operador invente fatos adicionais.

## Validação do Artefato

Antes de considerar o fluxo concluído, confirme:

1. Existe exatamente um arquivo correspondente à identidade do fluxo.
2. O arquivo foi criado ou atualizado conforme a decisão do workflow.
3. O arquivo segue `assets/fluxo.md`.
4. Contém `flowchart TD`.
5. Contém `sequenceDiagram`.
6. Mermaid é sintaticamente válido.
7. Não utiliza `subgraph`.
8. O `flowchart` utiliza apenas nós concretos.
9. O `sequence` utiliza somente participantes confirmados.
10. Os diagramas representam o mesmo fluxo funcional.
11. As dependências estruturais do fluxo foram preservadas.
12. Os caminhos de erro confirmados foram representados.
13. Dependências externas foram confirmadas no `Modelo Factual`.
14. Nenhum componente interno foi classificado como dependência externa.
15. Não existem trechos residuais de versão anterior.
16. Não existem seções extras fora do template.
17. Nenhum arquivo fora do escopo foi alterado.

Se a validação falhar:

- marque o fluxo como `bloqueado`;
- não faça correções fora do escopo;
- registre o motivo.

## Regras

- Mapeie somente o escopo autorizado.
- Não invente requisitos, dependências, relações ou comportamento.
- Não redefina requisitos funcionais.
- Não implemente código.
- Não altere código-fonte do SRV.
- Não acione outras skills.
- Não execute contratos ou CURL neste workflow.
- Não use conhecimento geral para completar informações ausentes.
- Preserve evidências do código analisado.
- Não sobrescreva um arquivo de identidade diferente.
- Não remova arquivos sem autorização explícita.
- Não tome decisões destrutivas por inferência.
- Pare e solicite decisão quando existir conflito real.
- Preserve artefatos não reconciliados e reporte-os.
- Em execução em massa, trate cada fluxo independentemente.

## Saída

### Execução Individual

Informe:

- identidade do fluxo;
- operação: `criado`, `atualizado`, `bloqueado` ou `aguardando usuário`;
- arquivo;
- pendências.

### Execução em Massa

Informe:

- quantidade de pontos de entrada identificados;
- quantidade de fluxos criados;
- quantidade de fluxos atualizados;
- quantidade de fluxos bloqueados;
- quantidade de conflitos;
- quantidade de artefatos não reconciliados;
- arquivos criados;
- arquivos atualizados;
- conflitos que exigem decisão;
- pendências.

Pare após a conclusão ou após uma decisão necessária do usuário.