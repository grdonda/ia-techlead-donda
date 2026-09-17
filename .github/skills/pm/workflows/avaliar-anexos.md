# Avaliar Anexos

Classificacao unica dos anexos disponiveis antes do refinamento ou da CSD.

## Etapas

1. Confirme o projeto e a historia local.
2. Leia o inventário mais recente e marque `status: em andamento`.
3. Leia os anexos aplicaveis em `dominios/<projeto>/contexto/` e `dominios/<projeto>/historias/<JIRA-ID>/contexto/`.
4. Classifique cada arquivo como `Projeto`, `Historia` ou `Implementacao`.
5. Preencha [inventario-anexos.md](../assets/inventario-anexos.md).
6. Salve como `dominios/<projeto>/historias/<JIRA-ID>/contexto/<JIRA-ID>_anexos.md`.
7. Atualize `status`, `data-atualizacao` e pendências; se já estiver concluído e válido, reutilize-o.

## Regras

- Nao altere a historia oficial nem os anexos originais.
- Leia CSV, SQL, imagens e PDF somente quando forem relevantes ao workflow.
- Registre `Nao localizado` ou `Nao verificavel` quando aplicavel.
- Finalize a etapa e aguarde a proxima solicitacao do usuario.
