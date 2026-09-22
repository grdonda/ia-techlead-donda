# Criar Task DEV para o Jira

## Objetivo

Transformar o TO-BE definido na análise DEV em uma ou mais Tasks DEV de implementação.

## Processo

1. Confirme projeto, história de origem, SRV/LIB, repositório autorizado e solicitação do usuário.
2. Leia a história e os artefatos necessários ao contexto.
3. Valide a existência e atualidade da análise DEV.
4. Se a análise DEV estiver ausente ou insuficiente, interrompa e solicite `executar-analise.md`.
5. Divida o TO-BE em Tasks DEV, unificadas ou separadas por componente ou etapa.
6. Use o `dev-operador` para criar ou atualizar:

`dominios/<projeto>/historias/<JIRA-ID>/tasks/Task 00N - DEV - <TITULO>.md`

## Regras

* Não reanalise o repositório.
* Não redefina a solução técnica.
* Não invente requisitos, dependências ou alterações.
* Preserve o conteúdo técnico definido na análise DEV.
* A numeração inicia em `Task 001` e segue `N + 1`.
* Não crie história derivada nem Task do TechLead.
* Não publique no Jira sem autorização explícita.

## Saída

Cada Task DEV deve conter o necessário para implementação, entendimento e validação.

Atualize `status`, `data-atualizacao`, `responsavel`, evidências e pendências.

Status:

* `concluído`
* `aguardando usuário`
* `bloqueado`
