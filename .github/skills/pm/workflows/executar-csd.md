# Workflow: CSD

    Matriz de Certezas, Suposições e Dúvidas para controlar incertezas rastreáveis em qualquer texto encaminhado por outro workflow.

## Objetivo

    - Analisar o conteúdo recebido, ou designado, registrar fatos relevantes e identificar suposições, dúvidas, lacunas, conflitos e referências não verificadas sem inventar requisitos ou decisões.
    - A CSD é um instrumento de validação do entendimento. Não substitui refinamento, análise técnica, mapeamento de fluxo ou definição de solução.

## Tipos de item

- `CERTEZA`: informação sustentada pelo texto ou por evidência registrada.
- `SUPOSIÇÃO`: interpretação não confirmada.
- `DÚVIDA`: pergunta explícita sobre uma informação ou regra.
- `LACUNA`: informação necessária que não foi apresentada.
- `CONFLITO`: informações incompatíveis entre si.
- `REFERÊNCIA`: referência citada, ausente ou não verificável.

## Etapas

1. Confirmar a autorização recebida do `donda`.
2. Identificar a fonte, o contexto e os anexos encaminhados.
3. Ler a fonte atual, o artefato CSD mais recente e os esclarecimentos disponíveis.
4. Encaminhar a fonte, o artefato anterior e os esclarecimentos ao `pm-analista` para análise conforme `../assets/csd.md`.
5. Receber a análise com cada informação relevante registrada como ocorrência auditável, mantendo o trecho original, a referência, a observação e a interpretação separadas.
6. Exigir que cada suposição, dúvida, lacuna, conflito ou referência não verificável possua impacto e pergunta objetiva de esclarecimento, quando aplicável.
7. Encaminhar a análise ao `operador` para criar ou atualizar o artefato, preservando o histórico e atualizando data, status e pendências.
8. Quando houver resposta, encaminhá-la ao `pm-analista` para registrar sua origem e marcar o item como `RESPONDIDA`; não considerá-lo resolvido automaticamente.
9. Encaminhar a reanálise da resposta ao `pm-analista` para verificar contradições, consequências e necessidade de incorporação. Marcar o item como `VALIDADA` e depois `INCORPORADA` somente quando a informação estiver suficientemente confirmada e refletida no artefato adequado.
10. Se ainda houver itens `PENDENTE`, solicitar ao `operador` o status `aguardando usuário` ou `bloqueado`, conforme a dependência, e registrar o próximo workflow.
11. Concluir somente quando não houver incerteza relevante sem tratamento, retornando o caminho e o status ao `donda`.

## Regras

- Não emitir detalhes intermediários da análise no chat.
- Não alterar a fonte original encaminhada.
- Não transformar suposição em requisito, contrato, regra ou critério de aceite.
- Não resolver dúvida por inferência quando a confirmação for necessária.
- Registrar certezas relevantes quando elas sustentarem o entendimento ou a resolução de uma incerteza.
- Usar rigorosamente o formato de [csd.md](../assets/csd.md).
- O `pm-analista` não substitui análise técnica de desenvolvimento; deve registrar a necessidade de investigação quando aplicável.
- O `operador` define e confirma o caminho final e o status do artefato.

## Critério de encerramento

A CSD pode ser concluída somente quando:

- não existirem itens `PENDENTE` sem tratamento;
- as respostas possuírem origem registrada;
- não existirem conflitos relevantes sem decisão;
- os itens resolvidos estiverem `VALIDADOS` ou `INCORPORADOS`;
- a reanálise não identificar novas incertezas relevantes.

## Artefatos

- Para história: `dominios/<projeto>/historias/<JIRA-ID>/csd/<JIRA-ID>_csd.md`.
- Para demanda ad-hoc ou outro texto: `dominios/refinamentos/`.
