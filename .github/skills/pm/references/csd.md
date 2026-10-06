# Processo: csd

Matriz de Certezas, Suposições e Dúvidas para controlar incertezas rastreáveis em um texto. É instrumento de validação do entendimento.

Estrutura de pastas: [dominios](../../../instructions/dominios.instructions.md).

## Entradas

- Fonte ou conteúdo a analisar, contexto e anexos.
- CSD anterior e esclarecimentos do usuário, se existirem.

## Saída

A partir do asset [csd](../assets/csd.md):

- História: `dominios/<projetos>/historias/<jira-id>/refinamento/<jira-id>_csd.md`.
- Demanda ad-hoc ou outro texto: `dominios/refinamentos/<assuntos>/csd.md`.

## Tipos de item

- `CERTEZA`: sustentada pelo texto ou por evidência registrada.
- `SUPOSIÇÃO`: interpretação não confirmada.
- `DÚVIDA`: pergunta explícita sobre informação ou regra.
- `LACUNA`: informação necessária não apresentada.
- `CONFLITO`: informações incompatíveis.
- `REFERÊNCIA`: referência citada, ausente ou não verificável.

## Etapas

1. Identificar a fonte, o contexto e os anexos.
2. Ler a fonte atual, o CSD mais recente e os esclarecimentos.
3. Registrar cada informação relevante como ocorrência auditável, com trecho original, referência, observação e interpretação separados.
4. Para toda suposição, dúvida, lacuna, conflito ou referência não verificável, registrar impacto e pergunta objetiva.
5. Persistir o artefato, preservando histórico e atualizando data, status e pendências.
6. Ao receber resposta, registrar a origem e marcar o item `RESPONDIDA`; não considerá-lo resolvido.
7. Reanalisar a resposta (contradições, consequências, incorporação); marcar `VALIDADA` e depois `INCORPORADA` somente quando confirmada e refletida no artefato adequado.
8. Se restarem itens `PENDENTE`, definir o status `aguardando usuário` ou `bloqueado` e registrar o próximo processo.

## Critério de encerramento

- Nenhum item `PENDENTE` sem tratamento.
- Respostas com origem registrada.
- Sem conflito relevante sem decisão.
- Itens resolvidos `VALIDADOS` ou `INCORPORADOS`.
- Reanálise sem novas incertezas relevantes.

## Regras

- Não alterar a fonte original.
- Não resolver dúvida por inferência quando a confirmação for necessária.
- Registrar certezas relevantes que sustentem o entendimento ou a resolução de uma incerteza.
- Seguir o formato do asset.
