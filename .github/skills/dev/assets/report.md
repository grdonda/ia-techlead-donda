# Report de erro

## Identificação

- Projeto: `<projeto ou Nao aplicavel>`
- Serviço: `<srv-nome>`
- Data: `<AAAA-MM-DD>`
- Branch analisada: `main`
- Trace/correlation/conversation ID: `<valor ou NAO LOCALIZADO>`

## Erro identificado

- Sintoma: `<ex. erros HTTP 500 no serviço X>`
- Mensagem ou exceção: `<texto objetivo do erro>`
- Ponto de ruptura: `<arquivo, classe, método ou operação>`

## Causa raiz

- Motivo: `<payload inválido, dado ausente ou outra causa confirmada>`
- Origem do dado incorreto: `<serviço ou etapa anterior, quando aplicável>`
- Comportamento não tratado: `<por que o serviço gerou o erro>`

## Solução

- Tratativa: `<validação, conversão, fallback ou outra alteração proposta>`
- Arquivos e pontos da correção: `<referências>`
- Outros erros possíveis avaliados: `<cenários relacionados e tratativa prevista>`
- Teste de reprodução: `<cURL, endpoint e resultado esperado>`
- Testes da correção: `<testes automatizados e/ou validação manual>`

## Observabilidade

- Instrumentação pontual: `<log, métrica ou trace a adicionar no fluxo>`
- Evidência de sucesso: `<informação que deverá ser localizada no Dynatrace>`
- DQL de validação: `<consulta ou caminho da evidência>`

## Branch de correção

- Jira: `<jira-id ou Nao aplicavel>`
- Branch oficial: `feature/fix-<jira-id>`
- Branch local provisória: `feature/fix-<titulo-curto>`
- Regra: analisar sempre a `main`; criar a branch local somente para implementar e testar a correção.

## Resumo para PR e comunicação

```text
Erro: <o que ocorreu e em qual serviço>.
Causa: <payload inválido, dado ausente ou causa confirmada>.
Solução: <tratativa aplicada para corrigir o erro e prevenir casos relacionados>.
Observabilidade: <instrumentação adicionada para validar o fluxo corrigido>.
Validação: <como a correção foi testada e qual resultado foi obtido>.
```

## Pendências

- `<somente informações que impedem confirmar causa, solução ou validação>`
