# Mapeamento de Fluxo

## Objetivo

Mapear o fluxo técnico da funcionalidade solicitada a partir do código e gerar representações `flowchart` e `sequence` em Mermaid.

## Processo

1. Confirme o contexto autorizado.
2. Identifique o ponto ou pontos de entrada da funcionalidade:

   * endpoint/controller;
   * consumer/listener;
   * evento/job.
3. A partir de cada entrada relevante, siga somente as chamadas reais do código que participam daquela funcionalidade até sua saída.
4. Identifique os componentes participantes:

   * Controller/Consumer;
   * Filter/Interceptor, quando participar;
   * Service/Use Case/Component;
   * Client/comunicação com outro serviço;
   * Repository/Banco;
   * Evento/Mensageria.
5. Registre a ordem real das chamadas e os retornos relevantes.
6. Para cada fluxo identificado, use o `dev-operador` para registrar um arquivo individual usando `assets/fluxo.md`.
7. Para cada fluxo, gere:

   * `flowchart TD` para representar o caminho estrutural;
   * `sequenceDiagram` para representar a ordem das interações.
8. Salve cada arquivo no caminho:
   `estudos/<srv>/<srv>-<fluxo-identificado>.md`
9. Quando acionado como dependência, devolva o conhecimento ao workflow chamador.

## Regras

* Mapeie somente as funcionalidades solicitadas.
* Gere um arquivo para cada fluxo identificado.
* Não misture fluxos diferentes no mesmo arquivo.
* Não mapeie o projeto inteiro.
* Não invente relações, componentes ou chamadas.
* Baseie cada ligação em evidência encontrada no código.
* Quando uma relação não puder ser confirmada, registre `DESCONHECIDO`.
* Não analise segurança, testes, riscos, observabilidade, qualidade, recomendações ou arquitetura geral.
* Não inclua componentes que apenas existam no projeto, mas não participem do fluxo.
* O `flowchart` deve representar o caminho técnico.
* O `sequence` deve representar a ordem temporal das interações encontradas.
* Os dois diagramas devem representar o mesmo fluxo descoberto, sem adicionar informações não presentes no outro.
* O nome do fluxo deve ser normalizado em `kebab-case`.

## Saída

Cada arquivo deve conter:

1. entrada;
2. flowchart;
3. sequence;
4. dependências;
5. saída;
6. pontos `DESCONHECIDO`, quando existirem.
