# Analise QA

1. Confirme o projeto, a historia, o repositorio ou contexto autorizado e a solicitacao do usuario.
2. Leia a historia e os artefatos disponiveis de refinamento, TechLead, DEV, contratos e testes relacionados.
3. Identifique requisitos, regras, criterios de aceite, fluxos, riscos, integracoes, dados e necessidades de regressao.
4. Relacione os requisitos aos cenarios existentes e identifique gaps de cobertura sem inventar comportamento.
5. Registre a analise no asset [analise.md](../assets/analise.md) dentro do contexto da historia.
6. Se depender de massa ou validacao de banco, registre a dependencia e aguarde solicitacao explicita para acionar DBA.
7. Marque o artefato como `concluído`, `aguardando usuário` ou `bloqueado`, atualize `data-atualizacao`, `responsavel` e pendencias e pare.

## Regras

- O workflow e sob demanda e assincrono.
- Nao acione PM, DEV ou DBA automaticamente.
- Refinamento, analise DEV e estudos sao fontes de contexto quando existirem, nao bloqueios automaticos.
- Se houver dependencia entre skills, informe o usuario e pergunte se deve prosseguir ou aguardar.
