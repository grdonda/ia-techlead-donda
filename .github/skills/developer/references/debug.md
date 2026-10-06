# Processo: debug

Investigação de um erro reportado até a causa raiz, correção guiada e report.

Estrutura de pastas: [dominios](../../../instructions/dominios.instructions.md).

## Entradas

- Pacote de evidência: trace_id e/ou conversation_id, nome do serviço e log do erro; POD e timestamp quando disponíveis. Peça apenas o item ausente.
- Relato opcional, conforme o escopo:
	- projeto: `dominios/<projetos>/srvs/analises/debug/<srv-nome>/problema-<data>.md`;
	- serviço compartilhado: `dominios/srvs/analises/debug/<srv-nome>/problema-<data>.md`;
	- serviço de biblioteca compartilhada: `dominios/srvs-shared/analises/debug/<srv-nome>/problema-<data>.md`.

## Saída

Gerar `report-<data>.md` a partir do asset [report](../assets/report.md), conforme o escopo:

- projeto: `dominios/<projetos>/srvs/analises/debug/<srv-nome>/report-<data>.md`;
- serviço compartilhado: `dominios/srvs/analises/debug/<srv-nome>/report-<data>.md`;
- serviço de biblioteca compartilhada: `dominios/srvs-shared/analises/debug/<srv-nome>/report-<data>.md`.

`<srv-nome>` é o serviço da causa raiz; `<data>` é `AAAA-MM-DD`.

## Etapas

1. Ler o pacote e o relato.
2. Propor consulta DQL para reconstruir o trace; o usuário executa e cola o resultado. Repetir com consultas mais direcionadas até distinguir causa de consequência.
3. Confirmar o ponto de ruptura e a causa raiz por identificadores e janela de tempo.
4. Se o serviço da causa raiz não for da squad, registrar a triagem no report e encerrar a investigação de código.
5. Se for da squad, ler o fluxo até a entrada, montar o cURL e reproduzir o erro localmente.
6. Apresentar diagnóstico e alteração proposta; aguardar autorização antes de editar.
7. Implementar na branch de correção definida no asset, avaliar erros relacionados e fornecer instruções de teste.
8. Validar com o usuário até confirmar sucesso; ajustar e repetir se necessário.
9. Propor observabilidade pontual e a DQL de validação em homologação.
10. Devolver o report consolidado, com resumo para PR e comunicação.

## Regras

- Investigar upstream, downstream e bibliotecas relevantes antes de concluir a causa.
