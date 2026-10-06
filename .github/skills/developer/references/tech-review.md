# Processo: tech-review

Validação técnica de uma História pelo dev, antes do refinamento com a Squad.

Estrutura de pastas: [dominios](../../../instructions/dominios.instructions.md).

## Entradas

- História oficial: `dominios/<projetos>/historias/<jira-id>/<jira-id>.md`. Se não existir, avisar o usuário e encerrar.
- Opcionais: refinamento e CSD da história; mapeamento de fluxo dos serviços envolvidos em `analises/fluxo/<srv-nome>/`.

## Saída

`dominios/<projetos>/historias/<jira-id>/tech-review/<jira-id>_tech-review.md`, a partir do asset [tech-review](../assets/tech-review.md).

## Etapas

1. Ler a história e, se existirem, o refinamento e o CSD.
2. Identificar os microsserviços e bibliotecas envolvidos e localizar seus repositórios no workspace.
3. Ler o código e a configuração relevantes de cada serviço; reaproveitar o mapeamento de fluxo quando existir.
4. Identificar contratos, integrações e comunicação entre os serviços.
5. Identificar dependências, riscos e impactos técnicos, por serviço.
6. Validar tecnicamente a história: o que ela pede é compatível com o que existe? Registrar lacunas técnicas e perguntas objetivas.
7. Classificar cada risco e achado por severidade.
8. Devolver o tech-review estruturado.
