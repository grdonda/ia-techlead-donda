# Workflow: refinar

Etapas do refinamento

## Objetivo

Produzir artefatos claros e rastreáveis para a próxima etapa, preservando as informações fornecidas e distinguindo fatos, hipóteses, desconhecidos e pendências.

## Regras

- Ler as fontes e os artefatos anteriores sem alterar os arquivos de entrada.
- Não inventar requisitos, decisões, contratos, dependências, estimativas ou solução técnica.
- Não emitir detalhes intermediários da análise no chat.
- Ler a fonte atualizada e o artefato mais recente antes de iniciar ou retomar uma etapa.
- Comparar fonte e artefato anterior, identificando informações confirmadas, alteradas, resolvidas, desatualizadas e pendentes.
- Preservar histórico, informações ainda válidas e pendências não resolvidas.
- Não considerar uma informação resolvida sem evidência ou declaração explícita na fonte atualizada.
- O `pm-analista` analisa e entrega conteúdo estruturado; não persiste arquivos.
- O `operador` persiste cada artefato usando o asset correspondente e confirma caminho, operação e status final.

## Cenários de entrada

### Relato local

- Entrada: `dominios/refinamentos/<ASSUNTO>/problema.md`.
- User Story: `dominios/refinamentos/<ASSUNTO>/historia.md`.
- Refinamento: `dominios/refinamentos/<ASSUNTO>/refinamento.md`.

### História com JIRA-ID

- Entrada: `dominios/<projeto>/historias/<JIRA-ID>/<JIRA-ID>.md`.
- Refinamento: `dominios/<projeto>/historias/<JIRA-ID>/refinamento/<JIRA-ID>_refinamento.md`.
- A história pode ter sido criada por terceiros ou pelo usuário com base em uma análise local. O conteúdo disponível na história é a fonte para o refinamento.

## Etapas

### Relato local: problema para User Story e refinamento

1. Confirmar a autorização recebida do `donda` e validar a existência de `problema.md`.
2. Ler o relato, anexos e artefatos anteriores do assunto, se existirem.
3. Encaminhar `problema.md` ao `pm-analista` para organizar a User Story conforme `../assets/historia.md`, separando informações declaradas, interpretações, hipóteses, desconhecidos e pendências.
4. Encaminhar o resultado ao `operador` para criar ou atualizar `dominios/refinamentos/<ASSUNTO>/historia.md` e confirmar a persistência.
5. Ler a história persistida junto com o relato original e evidências disponíveis.
6. Encaminhar essas fontes ao `pm-analista` para analisar e preencher `../assets/refinamento.md`.
7. Encaminhar o resultado ao `operador` para criar ou atualizar `dominios/refinamentos/<ASSUNTO>/refinamento.md`, preservando histórico, pendências e `data-atualizacao`.

### História com JIRA-ID: história para refinamento

1. Confirmar a autorização recebida do `donda` e validar a existência da história oficial.
2. Ler a história, anexos e refinamentos anteriores, se existirem.
3. Encaminhar a história e o refinamento anterior ao `pm-analista`, quando houver, para analisar a história e identificar mudanças, lacunas, conflitos e pendências usando `../assets/refinamento.md`.
4. Encaminhar o resultado ao `operador` para criar ou atualizar `dominios/<projeto>/historias/<JIRA-ID>/refinamento/<JIRA-ID>_refinamento.md`, preservando histórico, pendências e `data-atualizacao`.

### Fonte ou artefato atualizado

1. Identificar se a fonte atualizada é um relato local, uma User Story local ou uma história com JIRA-ID.
2. Ler a fonte atualizada e o artefato mais recente correspondente.
3. Encaminhar ambos ao `pm-analista` para comparar informações confirmadas, alteradas, resolvidas, desatualizadas e pendentes.
4. No cenário local, atualizar primeiro `historia.md` quando a mudança vier de `problema.md`; depois reanalisar essa história para atualizar `refinamento.md`.
5. No cenário JIRA-ID, atualizar diretamente o refinamento correspondente à história.
6. Encaminhar cada artefato atualizado ao `operador` para persistência, preservando o histórico.

## Saídas e assets

| Cenário | Artefato | Asset |
| --- | --- | --- |
| Relato local | `dominios/refinamentos/<ASSUNTO>/historia.md` | `../assets/historia.md` |
| Relato local | `dominios/refinamentos/<ASSUNTO>/refinamento.md` | `../assets/refinamento.md` |
| História com JIRA-ID | `dominios/<projeto>/historias/<JIRA-ID>/refinamento/<JIRA-ID>_refinamento.md` | `../assets/refinamento.md` |

## Conclusão

- Aguardar confirmação do `operador` para cada artefato persistido.
- Retornar ao `donda` os caminhos finais, os status confirmados e as pendências ou bloqueios relevantes.
