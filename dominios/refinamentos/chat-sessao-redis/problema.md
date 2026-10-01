# Relato

## O que aconteceu

    Existe um srv lib externo que gerencia redis;
    Existe um srv nosso que utiliza a lib do redis para interagir com o Redis;
    O TTL do Redis é de 30 min;
    A cada interação com a lib, o TTL é renovado.
    Caso o TTL expire, o cache é recriado.
    Não existe consulta por parte do srv que envia os dados para verificar se a sessão do Redis expirou.
    Dados enviados pelo srv com sessoes expiradas estão sendo processados como se fossem válidos, causando inconsistências.
    Existem logs de sessoes com mesmo client_id e conversation_id em sessões diferentes do Redis com TTL expirado.

## Projeto envolvido

    projeto-1

## SRVs e Libs envolvolvidos

    srv-fed-chat
    srv-bff-chat
    srv-api-chat
    srv-srv-chat

## Etapas de analise do problema

    o fed chama o endpoint para iniciar conversa /api/chat/conversa e gera o client_id e conversation_id e espera a mensagem do usuario

    usuario manda a mensagem que é agregada aos dados gerados e enviada para o endpoint /api/chat/mensagem

    Existe um srv lib externo que gerencia redis;
    Existe um srv nosso que utiliza a lib do redis para interagir com o Redis;
    O TTL do Redis é de 30 min;
    A cada interação com a lib, o TTL é renovado.
    Caso o TTL expire, o cache é recriado.
    Não existe consulta por parte do srv que envia os dados para verificar se a sessão do Redis expirou.
    Dados enviados pelo srv com sessoes expiradas estão sendo processados como se fossem válidos, causando inconsistências.
    Existem logs de sessoes com mesmo client_id e conversation_id em sessões diferentes do Redis com TTL expirado.

## Reprodução do erro

    janela do chat aberta e com mensagens com intervalo posterior a 30 min mantem o cliente_id e conversarion_in gravando nos logs

    janela recuperada idem;

    envio de CURL no endereço do chat no BFF tbm permite continuar conversas pós expiração do token

    logs gerados com intervalo de mensagens com mais de 30 min entre elas com mesmos client_id e conversation_id

## Oportunidade

    Implementar uma "trava" que detecte quando a sessão do Redis expirar e retorne um status de sessão expirada para quem chama a lib, evitando problemas de client_id e conversation_id repetidos.

    Criar uma "trava" no srv que chama a lib do redis quando a sessão estiver expirada
    Em caso de sessão expirada, retornar ao frontend a sessão expirada
    Frontend deve reiniciar a conversa no chat gerando novos IDs
