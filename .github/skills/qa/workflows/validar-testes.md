# Validar Testes QA

1. Confirme o projeto, a historia e a autorizacao explicita.
2. Leia a analise QA, a matriz, os CTs, os CT-DBs e o plano JMeter quando existirem.
3. Verifique rastreabilidade entre requisitos, regras, criterios de aceite e cenarios.
4. Identifique duplicidades, lacunas, nomenclatura incorreta, dependencias ausentes e evidencias insuficientes.
5. Registre o resultado no artefato de analise QA ou na matriz da historia, conforme o pedido.
6. Nao altere cenarios existentes neste workflow sem autorizacao explicita.
7. Atualize `status`, `data-atualizacao`, `responsavel` e pendencias; marque `concluído`, `aguardando usuário` ou `bloqueado` e pare.

## Regras

- O workflow e sob demanda e assincrono.
- Nao acione PM, DEV ou DBA automaticamente.
- Se houver dependencia entre skills, informe o usuario e pergunte se deve prosseguir ou aguardar.
