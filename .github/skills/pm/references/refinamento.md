# Processo: refinamento

Produz User Story e refinamento estruturados a partir de um relato ou de uma história, de forma rastreável.

Estrutura de pastas: [dominios](../../../instructions/dominios.instructions.md).

## Entradas

- Relato local: `dominios/refinamentos/<assuntos>/problema.md`.
- História: `dominios/<projetos>/historias/<jira-id>/<jira-id>.md`; é a fonte oficial, mesmo quando criada a partir de análise local.
- Anexos e artefatos anteriores, se existirem.

## Saída

| Cenário | Artefato | Asset |
| --- | --- | --- |
| Relato | `dominios/refinamentos/<assuntos>/historia.md` | [historia](../assets/historia.md) |
| Relato | `dominios/refinamentos/<assuntos>/refinamento.md` | [refinamento](../assets/refinamento.md) |
| História | `dominios/<projetos>/historias/<jira-id>/refinamento/<jira-id>_refinamento.md` | [refinamento](../assets/refinamento.md) |

## Etapas

### Relato

1. Validar a existência de `problema.md`; ler relato, anexos e artefatos anteriores.
2. Organizar a User Story conforme o asset, separando declarado, interpretação, hipótese, desconhecido e pendência.
3. Persistir `historia.md` antes de seguir.
4. Reanalisar a história com o relato e as evidências para preencher o refinamento.
5. Persistir `refinamento.md`.

### História

1. Validar a existência da história; ler história, anexos e refinamento anterior.
2. Analisar a história e identificar mudanças, lacunas, conflitos e pendências conforme o asset.
3. Persistir o refinamento.

### Fonte atualizada

1. Identificar o cenário; ler a fonte atualizada e o artefato mais recente.
2. Comparar e classificar: confirmado, alterado, resolvido, desatualizado, pendente.
3. Relato: atualizar `historia.md` primeiro e reanalisar para o `refinamento.md`. História: atualizar o refinamento.
4. Persistir cada artefato atualizado.

## Regras

- Preservar histórico, informações ainda válidas, pendências e `data-atualizacao`.
- Só considerar uma informação resolvida com evidência ou declaração explícita na fonte atualizada.
- Não inventar estimativas, decisões ou solução técnica.
- Não emitir detalhes intermediários da análise no chat.
