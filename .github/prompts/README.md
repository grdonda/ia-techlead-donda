# Prompts da squad

Atalhos digitados no chat com `/`. Todos iniciam pelo Donda, que apresenta o plano e só executa após a sua autorização.

## Como usar

```text
/<comando> <alvo> [detalhes]
```

Sem argumentos, o chat pergunta o alvo.

## Comandos

| Comando | Para que serve | Exemplo |
| --- | --- | --- |
| `/dev-tech-review` | Validar tecnicamente uma história | `/dev-tech-review projeto-1 FEAT-1234` |
| `/dev-code-review` | Revisão de código, arquitetura ou mudança | `/dev-code-review pagamentos-srv endpoint POST /v1/pagamentos` |
| `/dev-desenvolvimento` | Implementar uma mudança definida | `/dev-desenvolvimento pagamentos-srv validar CPF no cadastro` |
| `/dev-testes` | Criar ou ajustar testes automatizados | `/dev-testes pagamentos-srv cálculo de juros` |
| `/dev-fluxo` | Mapear o fluxo de endpoints ou operações | `/dev-fluxo pagamentos-srv` |
| `/dev-debug` | Investigar um erro até a causa raiz | `/dev-debug pagamentos-srv trace_id=abc123` |
| `/pm-refinamento` | User Story e refinamento a partir de relato ou história | `/pm-refinamento FEAT-1234` |
| `/pm-csd` | Matriz de certezas, suposições e dúvidas | `/pm-csd FEAT-1234` |
| `/qa-cts` | Cenários de teste de uma história | `/qa-cts projeto-1 FEAT-1234` |
| `/dba-analise` | Estrutura, consultas e dados de um banco | `/dba-analise db-clientes projeto-1 entender tabela de contratos` |
| `/revisar-dominios` | Compara a estrutura real de `dominios/` com a canônica (somente leitura) | `/revisar-dominios projeto-1` |

## O que acontece

1. O Donda lê o catálogo da skill e apresenta o plano (processo, alvo e artefato de saída).
2. Você autoriza.
3. O subagente do papel executa a referência do processo e devolve o resultado.
4. O `operador` grava o artefato no destino definido pelo processo.

## Para adicionar um comando

Crie `<papel>-<processo>.prompt.md` nesta pasta, com `agent: Donda`, apontando a skill e o processo, e inclua uma linha na tabela acima. O processo em si (referência, asset e linha na tabela da skill) fica na pasta da skill.
