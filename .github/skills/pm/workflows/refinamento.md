# Refinamento

Organização da informação da história local `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md` para facilitar o entendimento e o refinamento.

## Objetivo

- identificar no texto da história `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md` local:
  - o objetivo da história
  - criterios de aceite
  - definições de pronto
  - critérios de prioridade
  - microsserviços envolvidos e afetados
  - arquivos anexos e citados na historia
  - plataformas envolvidas
  - dependências externas de negócio e técnicas
  - riscos e impactos identificados
  - Organizar a compreensão da história sem alterar a história oficial.
  - Garantir que todas as informações relevantes da história sejam compreendidas e documentadas corretamente.

## Etapas

1. Informe ao usuario o início do processo de refinamento da história.
2. Leia o refinamento mais recente e marque `status: em andamento`.
3. Verifique o inventário de anexos concluído em `dominios/<projeto>/historias/<JIRA-ID>/contexto/<JIRA-ID>_anexos.md`.
4. Use o `pm-analista` para analisar a historia e o inventário.
5. Entregue a análise ao `pm-operador`, que atualiza `data-atualizacao`, status e pendências.
6. Marque `concluído` ou `bloqueado`, salve o artefato e aguarde a próxima solicitação.

## Regras e Limites

- não imprima detalhes intermediários do processo no chat
- siga rigorosamente o formato do arquivo [refinamento.md](../assets/refinamento.md)
- siga a ordem das seções conforme definido no arquivo [refinamento.md](../assets/refinamento.md)
- não altere o conteúdo do arquivo [refinamento.md](../assets/refinamento.md) original

## Artefatos

- `dominios/<projeto>/historias/<JIRA-ID>/refinamento/<JIRA-ID>_refinamento-<DATA:aaaa-mm-dd-hh-mm>.md`
