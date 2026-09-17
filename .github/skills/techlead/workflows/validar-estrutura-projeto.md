# Validar Estrutura de Projeto Existente

Use este workflow quando o usuario pedir para comparar `dominios/<PROJETO>/` ou `dominios/<PROJETO>/historias/<JIRA-ID>/` com a estrutura canonica ou identificar algo fora de contexto.

1. Confirme o projeto e a autorizacao explicita para leitura.
2. Leia [estrutura canonica](../assets/estrutura-canonica.md) e os workflows aplicaveis do TechLead.
3. Se o alvo for o projeto, liste `dominios/<PROJETO>/`, suas historias e os caminhos previstos no projeto; se o alvo for uma historia, trate `dominios/<PROJETO>/historias/<JIRA-ID>/` como raiz.
4. Compare somente os caminhos existentes com a estrutura canonica. Ausencia e permitida; caminho existente fora da estrutura, nome divergente, duplicidade ou referencia conflitante deve ser apontado.
5. Acesse `dominios/<PROJETO>/contexto/` quando o workflow exigir essa entrada e informe o usuario antes da leitura. Nao leia outros projetos ou historias fora do alvo.
6. Registre presentes, ausentes, fora de contexto, duplicados, inconsistencias e riscos em um relatorio de analise.
7. Nao altere, mova, remova ou crie arquivos do projeto analisado.
8. Informe os arquivos que precisariam ser alterados somente como proposta e aguarde autorizacao.
