# Análise DEV de Sistema

## Objetivo

Analisar tecnicamente o SRV ou LIB necessário à história, definindo AS-IS, TO-BE, impactos, riscos e pendências.

## Processo

1. Confirme projeto, história, SRV/LIB, repositório autorizado e autorização de leitura.
2. Leia a história e os artefatos necessários em `dominios/<projeto>/historias/<JIRA-ID>/`.
3. Leia `dominios/<projeto>/contexto/` somente quando necessário e avise o usuário antes.
4. Use o `dev-analista` para levantar o AS-IS e os elementos técnicos necessários à análise.
5. Se o fluxo necessário não estiver conhecido, execute `executar-mapeamento-fluxo.md` e retorne à análise.
6. Confronte o AS-IS com a história para definir o TO-BE, incluindo alterações, impactos, contratos, validações, mensageria, observabilidade e dependências.
7. Use o `dev-operador` para registrar:

`dominios/<projeto>/historias/<JIRA-ID>/contexto/<JIRA-ID>_analise-dev.md`

## Regras

* Analise somente o escopo da história.
* Não implemente alterações.
* Não redefina requisitos.
* Considere somente informações confirmadas.
* Registre como pendência o que não puder ser confirmado.
* Quando utilizar o mapeamento de fluxo, aproveite os fluxos gerados como evidência técnica da análise.

## Saída

Atualize `status`, `data-atualizacao`, `responsavel` e pendências.

Status:

* `concluído`
* `aguardando usuário`
* `bloqueado`
