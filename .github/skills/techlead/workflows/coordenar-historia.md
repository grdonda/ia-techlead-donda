# Coordenar História

Use este workflow para identificar a etapa técnica permitida e encaminhar a próxima solicitação, sem executar outra skill automaticamente.

1. Confirme o projeto, a história e a autorização explícita para leitura dos artefatos.
2. Leia o arquivo da história e o artefato mais recente de cada etapa existente.
3. Classifique a situação atual como `pendente`, `em andamento`, `aguardando usuário`, `bloqueado`, `desatualizado` ou `concluído`.
4. Identifique a próxima etapa permitida com base nos pré-requisitos confirmados.
5. Informe a skill, o workflow, os artefatos de entrada, a pendência e a autorização necessária para prosseguir.
6. Não crie tasks, não implemente código, não crie testes e não prepare massa neste workflow.
7. Aguarde a solicitação do usuário para acionar a próxima skill.

## Saída

Registrar na resposta:

* etapa atual e status;
* artefato mais recente consultado;
* próxima etapa recomendada;
* pré-requisitos ausentes ou pendências;
* skill e workflow que poderão ser solicitados em seguida.
