# Mapeamento de Fluxo

## Objetivo

Mapear o fluxo técnico da funcionalidade solicitada a partir do código e gerar representações `flowchart` e `sequence` em Mermaid.

## Processo

1. Confirme o contexto autorizado.
2. Identifique o ponto ou pontos de entrada da funcionalidade:

   * endpoint/controller;
   * consumer/listener;
   * evento/job.
3. A partir de cada entrada funcional relevante, siga somente as chamadas reais do código que participam daquela funcionalidade até sua saída.
4. Identifique os componentes participantes:

   * Controller/Consumer;
   * Filter/Interceptor, quando participar;
   * Service/Use Case/Component;
   * Client/comunicação com outro serviço;
   * Repository/Banco;
   * Evento/Mensageria.
5. Registre a ordem real das chamadas e os retornos relevantes.
6. Registre também caminhos de erro ou exceção relevantes encontrados no fluxo, sem misturá-los ao caminho principal.
7. Para cada fluxo identificado, use o `dev-operador` para registrar um arquivo individual usando `assets/fluxo.md`.
8. Para cada fluxo, gere:

   * `flowchart TD` para representar o caminho estrutural;
   * `sequenceDiagram` para representar a ordem das interações.
9. Salve cada arquivo no caminho:
   `estudos/<srv>/<ordem>-<srv>-<fluxo-identificado>.md`
10. Quando acionado como dependência, devolva o conhecimento ao workflow chamador.

## Regras

* Mapeie somente as funcionalidades solicitadas.
* Gere um arquivo para cada fluxo identificado.
* Não misture fluxos diferentes no mesmo arquivo.
* Não mapeie o projeto inteiro.
* Não inclua entradas operacionais, como Actuator ou Swagger, salvo solicitação explícita.
* Não invente relações, componentes ou chamadas.
* Baseie cada ligação em evidência encontrada no código.
* Quando uma relação não puder ser confirmada, registre `DESCONHECIDO`.
* Não analise segurança, testes, riscos, observabilidade, qualidade, recomendações ou arquitetura geral.
* Não inclua componentes que apenas existam no projeto, mas não participem do fluxo.
* O `flowchart` deve representar o caminho técnico.
* O `sequence` deve representar a ordem temporal das interações encontradas.
* Os dois diagramas devem representar o mesmo fluxo descoberto, sem adicionar informações não presentes no outro.
* O nome do fluxo deve ser normalizado em `kebab-case`.
* Numere os arquivos na ordem dos fluxos funcionais identificados, iniciando em `01` e seguindo `N + 1`.
* Preserve a mesma ordem entre a identificação dos fluxos, os arquivos gerados e a documentação apresentada.
* Componentes transversais, como Filter, Interceptor ou Rate Limit, não devem gerar fluxo próprio quando apenas participarem de outro fluxo.

## Saída

Cada arquivo deve conter:

1. entrada;
2. flowchart;
3. sequence;
4. dependências;
5. saída principal;
6. caminhos de erro/exceção relevantes, quando existirem;
7. pontos `DESCONHECIDO`, quando existirem.
