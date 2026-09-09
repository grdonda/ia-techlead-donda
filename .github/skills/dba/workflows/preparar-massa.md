# Preparar Massa de Dados

1. Leia a necessidade de banco do CT e confirme seu schema, dados esperados, referências ou resultados de queries fornecidos pelo usuário e ambiente autorizado.
2. Localize dados de baseline de teste existentes e crie queries e scripts somente a partir de estruturas e dados confirmados.
3. Preserve os dados de baseline preexistentes. Registre seu estado anterior e restaure somente alterações temporárias de campos explicitamente autorizadas; limpe apenas os dados inseridos para o teste.
4. Prefira scripts idempotentes. Inclua transação e validação quando aplicável.
5. Preencha [massa-sql.md](../assets/massa-sql.md) e salve-o como `CT00N - DB - <TITULO_CORRESPONDENTE>.md` em `testes/<ASSUNTO>/db/`.
6. Relate os pré-requisitos e não execute os scripts sem autorização.