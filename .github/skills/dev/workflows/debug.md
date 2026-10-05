# Workflow: debug

Troubleshooting de um erro reportado, a partir de evidências, até a causa raiz, a correção guiada e o report para o relator.

## Objetivo

Investigar um erro reportado, correlacionar evidências do Dynatrace em um loop interativo até localizar o ponto de ruptura e a causa raiz, triar a responsabilidade, reproduzir o erro, corrigir o código de forma guiada quando for da squad, validar a correção junto com o usuário e manter o report atualizado para o relator e para o commit.

## Entradas

- Pacote de evidência inicial obtido pelo usuário no Dynatrace a partir da reclamação: trace_id e/ou conversation_id, nome do serviço (Dynatrace/Java) e o log do erro capturado; POD (ArgoCD) e timestamp quando disponíveis.
- Se algum item do pacote estiver ausente, solicitar ao Donda somente o item faltante; não bloquear pelos demais.
- Repositórios dos serviços e bibliotecas candidatos devem estar disponíveis no workspace:
  - microserviço de projeto: `dominios/<projeto>/srvs/<srv-nome>`;
  - microserviço compartilhado: `dominios/srvs/<srv-nome>`;
  - biblioteca: `dominios/srvs-shared/<lib-nome>`.

Ler o arquivo do relato do problema quando existir:

- `dominios/<projeto>/srvs/analises/erros/<srv-nome>/problema-<data>.md`

## Evidências do erro

Arquivos complementares para análise, quando existirem: imagens, logs, txt, json, sql, outros.

- microserviço de projeto: `dominios/<projeto>/srvs/analises/erros/<srv-nome>/evidencias/<data>`;
- microserviço compartilhado: `dominios/srvs/analises/erros/<srv-nome>/evidencias/<data>`;
- biblioteca: `dominios/srvs-shared/analises/erros/<srv-nome>/evidencias/<data>`.

O agente não acessa o Dynatrace diretamente. Todo aprofundamento de evidência é feito por consulta DQL proposta em chat: o usuário executa manualmente e cola o resultado (print ou texto) de volta na conversa.

## Artefato

- `dominios/<projeto>/srvs/analises/erros/<srv-nome>/report-<data>.md`
- `<srv-nome>` é o serviço identificado como causa raiz; `<data>` é a data da investigação no formato `AAAA-MM-DD`, usada nas três pastas para diferenciar investigações do mesmo serviço.
- A pasta `analises` fica no mesmo nível dos repositórios de serviço, dentro de `srvs`; nunca dentro do repositório clonado do serviço (`<srv-nome>`).

## Etapas

1. Ler o pacote de evidência inicial e o relato; se faltar item essencial, solicitar apenas o item ausente ao Donda.
2. Gerar a primeira consulta DQL para reconstruir o distributed trace a partir do trace_id/conversation_id, cobrindo os serviços antes e depois do ponto onde o erro apareceu.
3. Registrar cada consulta DQL proposta e o resultado colado pelo usuário; propor a próxima consulta mais direcionada até haver evidência suficiente para distinguir a causa (serviço que originou o dado incorreto ou ausente) da consequência (serviço onde a exceção estourou).
4. Confirmar o ponto de ruptura e a causa raiz com base nas evidências correlacionadas por identificadores e janela de tempo.
5. Verificar se o serviço identificado como causa raiz pertence à squad. Se não pertencer, registrar a triagem, redigir o report inicial indicando o time ou serviço responsável pela correção e encerrar a investigação de código.
6. Se pertencer à squad, o `dev-analista` lê o fluxo até o ponto de entrada, monta o cURL de reprodução e reproduz o erro localmente, documentando o resultado.
7. Confirmada a reprodução, apresentar ao usuário o diagnóstico e a alteração proposta; aguardar autorização explícita antes de editar qualquer arquivo do repositório.
8. Após autorizado, o `dev-analista` implementa a correção no repositório e fornece as instruções de teste ao usuário.
9. Conduzir a validação guiada: aguardar o resultado do reteste relatado pelo usuário; se não confirmar sucesso, ajustar a correção e repetir até a consolidação.
10. Propor a observabilidade pontual a ser adicionada no trecho corrigido e a consulta DQL para validar a correção em homologação.
11. Atualizar o report com o problema, a causa raiz, a correção aplicada e a observabilidade introduzida, em texto pronto para o relator e reaproveitável na mensagem de commit.
12. Encaminhar ao `operador` o resultado consolidado a partir do asset [report.md](../assets/report.md), preservando títulos e estrutura.
13. Aguardar a confirmação do `operador` com o caminho e o status persistido; então retornar o resultado ao Donda.

## Regras

- O agente não acessa o Dynatrace diretamente; toda consulta DQL é entregue ao usuário para execução manual e o resultado retorna colado no chat.
- Quando o serviço identificado como causa raiz não pertencer à squad, não implementar correção; registrar a triagem e delegar.
- Quando pertencer à squad, o `dev-analista` pode reproduzir o erro localmente e propor a alteração; a implementação no repositório só ocorre após autorização explícita do usuário para aquela alteração específica.
- Após implementar, o `dev-analista` conduz a validação guiada com o usuário até a correção ser consolidada; não declarar sucesso sem confirmação do usuário.
- Não executar deploy nem homologação; essas etapas permanecem manuais.
- O `operador` persiste o artefato usando o asset; não complementa nem altera a análise recebida.
- Não presumir comportamento não localizado nas evidências.
- Diferenciar fato, hipótese e informação não confirmada.
- Toda conclusão deve possuir evidência correspondente.
- Preservar os identificadores fornecidos pelo usuário.
- Correlacionar evidências por identificadores e contexto temporal.
- Considerar o horário dos eventos ao reconstruir a sequência do erro.
- Investigar chamadas downstream e upstream quando forem relevantes para a falha.
- Investigar bibliotecas utilizadas pelo fluxo quando elas puderem explicar o comportamento observado.
- Não encerrar a investigação apenas porque foi encontrado o primeiro erro.
- Verificar se o erro encontrado é causa ou consequência de outro erro.
- Continuar a investigação enquanto existirem caminhos relevantes ainda não analisados.
- Não inventar dependências, fluxos, contratos, comportamentos ou resultados de validação.
- Quando não for possível confirmar a causa, registrar explicitamente a limitação.
