# Workflow - Teste de Carga com JMeter

## Objetivo

Criar a especificação e o plano de teste de carga para o fluxo implementado na história utilizando JMeter.

O processo utiliza:

* `skills/qa/assets/jmeter.md` como modelo da especificação.
* `.jmx` corporativo em `skills/qa/assets/` como referência técnica.
* História e task como fonte do objetivo e escopo.
* OpenAPI, curl, código e demais arquivos de contexto como fontes técnicas.

O resultado esperado é a criação de dois artefatos:

* `<JIRA-ID>-jmeter.md` — especificação do teste.
* `<JIRA-ID>-<SRV>-<SQUAD>.jmx` — plano JMeter específico da história.

---

## 1. Confirmar a necessidade

Antes de iniciar:

* Confirmar que existe necessidade de teste de carga.
* Identificar se a necessidade foi apontada pelo TechLead ou confirmada pelo PM.
* Considerar o escopo técnico definido pelo TechLead.
* Identificar a história ou task relacionada.

Não criar o plano quando não houver fluxo implementado ou informações suficientes para identificar o comportamento a ser testado.

---

## 2. Analisar a história e o fluxo

Analisar:

* História.
* Task relacionada.
* Critérios de aceite.
* Regras de negócio relevantes.
* Serviço envolvido.
* Fluxo implementado.
* Dependências.
* Informações técnicas disponíveis.

Quando necessário:

* Utilizar a skill PM para entendimento da história.
* Utilizar a skill DEV para entendimento da implementação.

O teste deve representar somente o fluxo relacionado à história.

---

## 3. Localizar os assets

Localizar os arquivos de referência disponíveis em:

`skills/qa/assets/`

Utilizar:

* `jmeter.md`
* Template `.jmx` corporativo.

O `jmeter.md` define a estrutura mínima da especificação do teste.

O `.jmx` corporativo define a estrutura técnica de referência para criação do plano JMeter.

Não alterar os arquivos originais.

---

## 4. Localizar as informações técnicas

Pesquisar no contexto da história as informações necessárias para preencher o plano.

Priorizar:

1. História e task.
2. Contrato OpenAPI.
3. `curl`.
4. Código do microserviço.
5. Documentação técnica.
6. Demais arquivos diretamente relacionados.

Identificar, quando aplicável:

* SRV.
* Endpoint.
* Método HTTP.
* Payload.
* Headers.
* Autenticação.
* Variáveis.
* Dados de teste.
* Dependências.
* Parâmetros de carga.
* Critérios de sucesso.

Utilizar as informações encontradas antes de solicitar dados adicionais.

Não inventar informações.

---

## 5. Criar a especificação do teste

Utilizar:

`skills/qa/assets/jmeter.md`

como modelo.

Criar:

`<JIRA-ID>-jmeter.md`

no diretório:

`dominios/<dominio>/historias/<JIRA-ID>/jmeter/`

A especificação deve registrar somente informações confirmadas.

Preencher:

* História.
* Serviço.
* Endpoint.
* Método.
* Objetivo.
* Cenário.
* Dados de entrada.
* Autenticação.
* Perfis de carga.
* Critérios de sucesso.
* Dependências.
* Limitações.
* Evidências.

---

## 6. Definir os perfis de carga

A especificação deve considerar, quando aplicável:

### Leve

Carga utilizada para validar o comportamento básico do fluxo.

Registrar:

* Usuários.
* RPS.
* Ramp-up.
* Duração.

### Média

Carga utilizada para avaliar o comportamento do fluxo em uma carga representativa.

Registrar:

* Usuários.
* RPS.
* Ramp-up.
* Duração.

### Agressiva

Carga utilizada para avaliar o comportamento do fluxo sob carga elevada.

Registrar:

* Usuários.
* RPS.
* Ramp-up.
* Duração.

Os valores devem ser definidos somente quando houver evidência ou critério confirmado.

Não criar valores padrão por suposição.

Quando necessário, registrar:

`Necessário validar`

---

## 7. Definir os critérios de sucesso

Registrar somente critérios confirmados.

Considerar, quando aplicável:

* Tempo de resposta.
* P95.
* P99.
* Taxa de erro.
* Throughput.

Não inventar limites de aprovação.

Quando os critérios não estiverem disponíveis, registrar a pendência na especificação.

---

## 8. Analisar o template JMeter

Localizar o `.jmx` corporativo em:

`skills/qa/assets/`

Analisar sua estrutura e identificar os componentes relevantes para reutilização.

Considerar:

* Thread Groups.
* HTTP Requests.
* Headers.
* Variáveis.
* Autenticação.
* Timers.
* Assertions.
* Massas.
* Configurações de execução.
* Outros componentes existentes no template.

O template deve ser utilizado como referência.

Não alterar o arquivo original.

---

## 9. Criar o JMX da história

Criar um novo `.jmx` a partir do template corporativo.

Utilizar como referência:

* `<JIRA-ID>-jmeter.md`
* História.
* Contrato.
* Curl.
* Código.
* Demais evidências técnicas.

Configurar o plano com:

* Endpoint.
* Método.
* Payload.
* Headers.
* Autenticação.
* Variáveis.
* Dados.
* Perfis de carga.
* Configurações necessárias.

Criar o arquivo em:

`dominios/<dominio>/historias/<JIRA-ID>/jmeter/`

Utilizar o padrão:

`<JIRA-ID>-<SRV>-<SQUAD>.jmx`

Não alterar o template corporativo.

---

## 10. Validar a consistência dos artefatos

Antes da execução, verificar se:

* O `<JIRA-ID>-jmeter.md` representa o teste planejado.
* O `.jmx` implementa o que está especificado no `.md`.
* Endpoint e método estão corretos.
* Payload está correto.
* Autenticação está configurada.
* Variáveis estão configuradas.
* Perfis de carga correspondem à especificação.
* Critérios de sucesso estão registrados.
* Dependências estão identificadas.

Não considerar o plano pronto quando houver divergências relevantes.

---

## 11. Validar localmente

Quando houver ambiente e condições disponíveis, executar uma validação local utilizando baixa carga.

Validar:

* Fluxo.
* Endpoint.
* Payload.
* Headers.
* Autenticação.
* Variáveis.
* Dados.
* Resposta.
* Assertions.
* Ausência de erros básicos.

A validação local serve para verificar o plano.

Ela não representa a capacidade final da aplicação.

---

## 12. Executar alta carga

Executar alta carga somente no Portal de Performance e mediante autorização explícita.

Utilizar o `.jmx` específico da história.

O Portal de Performance realiza a execução de alta escala e gera o relatório.

---

## 13. Analisar o relatório

Quando o relatório estiver disponível, analisar:

* Throughput.
* Tempo médio de resposta.
* P95.
* P99.
* Taxa de erro.
* Erros.
* Comportamento durante a carga.
* Evidências.
* Limitações.

O relatório do Portal é a principal evidência para avaliação da execução de alta carga.

---

## 14. Classificar o resultado

Classificar como:

* `Excelente`
* `Bom`
* `Atenção`
* `Falhou`
* `Não conclusivo`

Sempre apresentar justificativa baseada em evidências.

Utilizar `Não conclusivo` quando:

* Não houver dados suficientes.
* Não houver critérios de sucesso suficientes.
* Existir dependência externa não isolada.
* Existir limitação relevante para interpretação.
* O relatório não permitir uma conclusão segura.

---

## 15. Dependências e limitações

Registrar dependências que possam influenciar a execução ou o resultado.

Considerar:

* APIs externas.
* Serviços internos.
* Banco de dados.
* Autenticação.
* Filas.
* Serviços de terceiros.
* Massa de dados.
* Ambiente.
* Portal de Performance.

Registrar limitações conhecidas.

---

## 16. Evidências

Registrar as fontes utilizadas para criação e análise do teste.

Podem incluir:

* História.
* Task.
* OpenAPI.
* Curl.
* Código do microserviço.
* `jmeter.md`.
* Template `.jmx`.
* Relatório do Portal.
* Prints.
* Logs.
* Métricas.

Relatórios ou prints anteriores podem ser utilizados somente como contexto complementar.

Não utilizar resultados anteriores para inventar parâmetros ou critérios do teste atual.

---

## 17. Recomendações

Sugerir ajustes somente quando houver evidência suficiente.

As recomendações devem estar relacionadas a:

* Relatório.
* Implementação.
* Contrato.
* Critérios confirmados.
* Comportamento observado.
* Limitações identificadas.

Cada recomendação deve indicar o problema, a evidência e a ação recomendada.

---

## 18. Validação final

Antes de finalizar:

* [ ] Necessidade de teste confirmada.
* [ ] História ou task identificada.
* [ ] Fluxo identificado.
* [ ] SRV identificado.
* [ ] Endpoint confirmado.
* [ ] Método confirmado.
* [ ] Payload confirmado.
* [ ] Autenticação identificada.
* [ ] Parâmetros de carga confirmados ou pendenciados.
* [ ] Critérios de sucesso confirmados ou pendenciados.
* [ ] `jmeter.md` utilizado.
* [ ] Template `.jmx` utilizado.
* [ ] Template original preservado.
* [ ] `<JIRA-ID>-jmeter.md` criado.
* [ ] `.jmx` específico criado.
* [ ] Os dois artefatos estão consistentes.
* [ ] Dependências identificadas.
* [ ] Limitações registradas.
* [ ] Nenhuma informação foi inventada.

---

## 19. Regras

* Não inventar parâmetros de carga.
* Não inventar payloads.
* Não inventar contratos.
* Não inventar dados.
* Não inventar critérios de sucesso.
* Não inventar configurações do Portal.
* Não alterar `skills/qa/assets/jmeter.md`.
* Não alterar o template `.jmx` corporativo.
* Utilizar evidências disponíveis antes de solicitar informações adicionais.
* Registrar pendências quando uma informação não puder ser confirmada.
* O teste deve representar o fluxo da história.
* A especificação `.md` deve representar o plano de teste.
* O `.jmx` deve implementar a especificação `.md`.
* A validação local deve utilizar baixa carga.
* A validação local não representa a capacidade final.
* A alta carga deve ser executada no Portal de Performance.
* A alta carga exige autorização explícita.
* O relatório do Portal deve ser utilizado como evidência da execução.
* Utilizar `Não conclusivo` quando as evidências forem insuficientes.