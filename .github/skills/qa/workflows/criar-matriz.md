# Workflow - Matriz de Cenários de Teste

## Objetivo

Criar a matriz de testes da história utilizando o asset:

`skills/qa/assets/matriz.md`

A matriz deve consolidar os requisitos, regras, critérios de aceitação e cenários de teste da história, mantendo a rastreabilidade entre esses elementos.

O resultado deve ser um artefato específico da história.

---

## 1. Analisar a história

Analisar:

* História.
* Issue JIRA.
* Critérios de aceitação.
* Regras de negócio.
* Requisitos.
* Fluxos principais.
* Fluxos alternativos.
* Requisitos técnicos quando aplicável.

Quando necessário:

* Utilizar a skill PM para entendimento da história.
* Utilizar a skill DEV para entendimento da implementação.

Não inventar requisitos, regras ou critérios.

---

## 2. Localizar os cenários

Localizar os CTs existentes em:

`historias/<JIRA-ID>/testes/`

Identificar os assuntos existentes.

Exemplo:

`testes/cadastro/`

`testes/consulta/`

`testes/autenticacao/`

Utilizar os CTs existentes como fonte para preenchimento da matriz.

Não criar, alterar ou renomear CTs neste workflow.

---

## 3. Localizar informações de planejamento

Identificar, quando disponíveis:

* Sprint.
* Fix Version.
* Test Plan (TP).
* Test Execution (TE).
* Test Sets (TS).
* Assuntos utilizados para agrupamento dos CTs.

Utilizar as informações existentes no contexto da história, Jira/Xray ou demais fontes disponíveis.

Não inventar valores.

Quando uma informação não estiver disponível:

`Não identificado`

ou

`Necessário validar`

---

## 4. Utilizar o asset da matriz

Utilizar obrigatoriamente:

`skills/qa/assets/matriz.md`

como modelo do artefato.

Preservar sua estrutura.

Não criar uma estrutura alternativa.

A matriz gerada deve manter as seções definidas no asset.

---

## 5. Preencher as referências da história

Na seção de referências, identificar os elementos cobertos pelos testes.

Considerar:

* CA — Critérios de Aceitação.
* RN — Regras de Negócio.
* RT — Requisitos Técnicos.
* RI — Requisitos de Integração.
* RF — Requisitos Funcionais.
* Outros requisitos identificados na história.

Relacionar cada item à sua descrição correspondente.

Não criar identificadores que não estejam disponíveis sem deixar claro que foram criados somente para organização da matriz.

---

## 6. Relacionar os CTs

Para cada CT existente:

* Identificar o assunto.
* Identificar o título.
* Identificar a descrição.
* Identificar a regra, requisito ou critério coberto.
* Identificar o Cucumber.

Relacionar o CT ao elemento de negócio ou requisito correspondente.

A relação deve ser baseada no comportamento efetivamente coberto pelo CT.

Não considerar cobertura somente pela semelhança entre títulos.

---

## 7. Organizar por Test Set

Agrupar os cenários conforme os assuntos definidos na matriz.

Cada grupo deve seguir o padrão:

`TS - <ASSUNTO>`

Exemplo:

`TS - Cadastro`

`TS - Consulta`

`TS - Autenticação`

Relacionar os CTs correspondentes a cada grupo.

Não criar TS ou assunto sem evidência ou informação suficiente.

---

## 8. Preencher a tabela de cenários

Para cada grupo, preencher:

| ID | CT Titulo | Descrição | Regra coberta | Cucumber |
|---|---|---|---|---|
| 001 | <CT Título> | <Descrição> | CA001 - <texto> | <Cucumber> |

Utilizar os dados existentes nos CTs.

Não duplicar ou alterar o conteúdo original dos cenários.

O Cucumber deve corresponder ao cenário relacionado.

---

## 9. Identificar cobertura

Verificar se:

* Critérios de aceitação possuem CT relacionado.
* Regras de negócio possuem CT relacionado.
* Requisitos funcionais possuem CT relacionado.
* Requisitos técnicos possuem CT relacionado quando aplicável.
* Requisitos de integração possuem CT relacionado quando aplicável.

Identificar elementos sem cobertura.

Também identificar CTs que não possuam uma relação clara com requisito, regra ou critério.

---

## 10. Identificar gaps

Registrar:

* Requisitos sem cobertura.
* Regras sem cobertura.
* Critérios de aceitação sem cobertura.
* CTs sem rastreabilidade.
* Cenários positivos ausentes quando relevantes.
* Cenários negativos ausentes quando relevantes.
* Cenários de borda ausentes quando relevantes.

Não criar CT neste workflow.

Quando houver necessidade de novo cenário, registrar como gap ou TODO para posterior criação utilizando:

`workflows/criar-cenarios.md`

---

## 11. Avaliar a cobertura

Avaliar a qualidade da cobertura considerando:

* Requisitos.
* Regras de negócio.
* Critérios de aceitação.
* Cenários positivos.
* Cenários negativos.
* Cenários de borda.
* Riscos.
* Integrações quando aplicável.

A quantidade de CTs não determina sozinha a qualidade da cobertura.

---

## 12. Score

Avaliar a cobertura de 0 a 10.

Considerar:

* Cobertura dos requisitos.
* Cobertura das regras.
* Cobertura dos critérios de aceitação.
* Cobertura dos cenários relevantes.
* Riscos identificados.
* Rastreabilidade.

Sempre apresentar justificativa objetiva para o score.

---

## 13. TODOs

Registrar ações necessárias para melhorar a cobertura.

Cada TODO deve conter:

* Descrição.
* Motivo.
* Prioridade.

Exemplo:

`TODO: Criar CT para validar <comportamento>.`

`Motivo: CA002 não possui cobertura identificada.`

`Prioridade: Alta`

Não criar TODOs sem impacto real na cobertura.

---

## 14. Validação final

Antes de finalizar a matriz:

* [ ] Asset `matriz.md` utilizado.
* [ ] JIRA-ID correto.
* [ ] Sprint preenchido ou pendenciado.
* [ ] Fix Version preenchido ou pendenciado.
* [ ] TP identificado ou pendenciado.
* [ ] TE identificado ou pendenciado.
* [ ] TS identificados ou pendenciados.
* [ ] Requisitos identificados.
* [ ] Regras identificadas.
* [ ] Critérios de aceitação identificados.
* [ ] CTs existentes relacionados.
* [ ] CTs agrupados por assunto.
* [ ] Cucumber correspondente aos CTs.
* [ ] Rastreabilidade validada.
* [ ] Gaps identificados.
* [ ] TODOs identificados quando necessários.
* [ ] Score calculado.
* [ ] Nenhuma informação inventada.

---

## 15. Regras

* Utilizar `skills/qa/assets/matriz.md` como modelo.
* Não alterar o asset original.
* Não criar CTs neste workflow.
* Não alterar CTs existentes.
* Não inventar requisitos.
* Não inventar regras.
* Não inventar critérios de aceitação.
* Não inventar informações de Jira/Xray.
* Não inventar relacionamentos entre CTs e requisitos.
* Utilizar evidências disponíveis.
* Registrar informações ausentes como pendência.
* Preservar os cenários existentes.
* Utilizar `workflows/criar-cenarios.md` quando um novo CT for necessário.

---

## 16. Eficiência

* Ler somente a história e os CTs relacionados.
* Utilizar o asset existente em vez de criar uma estrutura alternativa.
* Evitar repetir o conteúdo completo dos CTs.
* Utilizar referências aos CTs sempre que possível.
* Não analisar arquivos sem relação com a matriz.
* Não repetir informações já identificadas.