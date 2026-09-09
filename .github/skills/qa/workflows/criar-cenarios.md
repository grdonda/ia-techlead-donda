# Criar Cenários de Teste

1. Leia a história, tasks técnicas, comportamento confirmado, contratos e análise relevante.
2. Agrupe os cenários por assunto aplicável e crie CTs usando [ct.md](../assets/ct.md), reiniciando em `CT001` para cada assunto.
3. Cubra sucesso, erro, regressão, integrações, Feature Toggle, Family and Friends e plataformas aplicáveis.
4. Crie registros de TS, TP, TE e Fix Version usando [ts.md](../assets/ts.md) e [tp-te.md](../assets/tp-te.md).
5. Quando um CT precisar de preparação de massa, preencha [ct-db.md](../assets/ct-db.md) com a operação de dados esperada e aguarde uma solicitação de DBA.