# CSD

Matriz de Certeza, Suposições e Dúvidas de uma história `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md` local.

## Objetivo

- identificar no texto da história `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md` local:
  - gaps
  - ambiguidades
  - lacunas
  - referências ausentes
  - suposições
  - dúvidas
  - anexos faltantes
  - inconsistências
  - contradições, duplicações, divergência de informações

## Etapas

1. Informe ao usuario o início do processo de CSD da história.
2. Leia a CSD mais recente e marque `status: em andamento`.
3. Verifique o inventário de anexos concluído em `dominios/<projeto>/historias/<JIRA-ID>/contexto/<JIRA-ID>_anexos.md`.
4. Use o `pm-analista` para analisar a historia e o inventário.
5. Entregue a análise ao `pm-operador`, que atualiza `data-atualizacao`, status e pendências.
6. Marque `concluído`, `aguardando usuário` ou `bloqueado`, salve o artefato e aguarde a próxima solicitação.

## Regras e Limites

- não imprima detalhes intermediários do processo no chat
- siga rigorosamente o formato do arquivo [csd.md](../assets/csd.md)
- siga a ordem das seções conforme definido no arquivo [csd.md](../assets/csd.md)
- não altere o conteúdo do arquivo [csd.md](../assets/csd.md) original

## Artefatos

- `dominios/<projeto>/historias/<JIRA-ID>/csd/<JIRA-ID>_csd-<DATA:aaaa-mm-dd-hh-mm>.md`
