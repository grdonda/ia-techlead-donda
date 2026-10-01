# Problema

    Identificação do assunto ou relato sobre erro, bug, fix, melhoria, feature, implementação, analise, confirmações etc

## Dor ou Necessidade

    Sessão do redis expirada é recriada automaticamente, mas o srv que envia os dados para lib do redis consulta a expiração,
    em caso de expiração ela recria o ID do redis e grava o contexto; então temos um problema de client_id e conversation_id repetidos em sessoes do Redis expiradas.

    Existem monitoramento de conversas por logs que são refletidos em um dashboard e estamos notando que existem
    conversar com mais de 70 horas em aberto com mesmo client_id e conversation_id. A quantidade de clientes está fora do comum

## Projeto envolvido

    projeto-1

## SRVs e Libs envolvolvidos

    srv-fed-chat
    srv-bff-chat
    srv-api-chat
    srv-srv-chat

## Etapas de analise do problema

    Existe um srv lib externo que gerencia redis;
    Existe um srv nosso que utiliza a lib do redis para interagir com o Redis;
    O TTL do Redis é de 30 min;
    A cada interação com a lib, o TTL é renovado.
    Caso o TTL expire, o cache é recriado.
    Não existe consulta por parte do srv que envia os dados para verificar se a sessão do Redis expirou.
    Dados enviados pelo srv com sessoes expiradas estão sendo processados como se fossem válidos, causando inconsistências.
    Existem logs de sessoes com mesmo client_id e conversation_id em sessões diferentes do Redis com TTL expirado.

## Oportunidade

    Implementar uma "trava" que detecte quando a sessão do Redis expirar e retorne um status de sessão expirada para quem chama a lib, evitando problemas de client_id e conversation_id repetidos.

    Criar uma "trava" no srv que chama a lib do redis quando a sessão estiver expirada
    Em caso de sessão expirada, retornar ao frontend a sessão expirada
    Frontend deve reiniciar a conversa no chat gerando novos IDs

### Cenários

    Dado que o envio de uma mensagem for realizado pelo usuario
    E for verificado que o TTL do redis ultrapassa o limite
    Então devolver ao request como sessão expirada

    Dado que o recebimento for sessão expirada
    Então realizar o reset da conversa gerando novos IDs
