# Processo: fluxo

Mapeamento somente leitura do fluxo de endpoints de microsserviço ou operações de biblioteca.

Estrutura de pastas: [dominios](../../../instructions/dominios.instructions.md).

## Entradas

- Serviço ou biblioteca alvo e, opcionalmente, os endpoints ou operações.

## Saída

Um artefato por endpoint ou operação. O destino deve seguir um dos caminhos canônicos de `analises/fluxo/` definidos na [estrutura de dominios](../../../instructions/dominios.instructions.md); não duplicar nem criar caminhos alternativos nesta referência.

O nome do arquivo segue o padrão `<metodo>-<endpoint-slug>.md` para endpoints e `<operacao-slug>.md` para operações de biblioteca.

## Uso do asset e persistência

O [fluxo-asset](../assets/fluxo-asset.md) é a estrutura do artefato, não um local para instruções de execução. Use suas seções como roteiro de pesquisa e análise; as instruções deste processo não devem ser copiadas para o artefato final.

- Preencher campos somente com informações confirmadas em código, configuração ou exemplos localizados; registrar `NAO LOCALIZADO`, `NAO VERIFICADO` ou `NAO APLICAVEL` quando couber.
- Registrar payloads de requisição e resposta como JSON válido, sem inventar campos ou valores.
- Montar o cURL persistido em múltiplas linhas, com método, URL, headers e payload confirmados; formatar o JSON com indentação. Sem payload, omitir `Content-Type` e `--data-raw`.
- Construir os diagramas a partir das chamadas e decisões confirmadas no fluxo.
- O executor devolve o conteúdo estruturado sem gravar o artefato. O operador copia o asset, preenche a cópia com o resultado recebido e persiste no caminho canônico definido na instrução de dominios.

## Etapas

1. Registrar a branch analisada uma única vez; se não confirmada, `NAO VERIFICADO`.
2. Ler properties e configuração para identificar comunicações externas (endpoints, filas, bancos).
3. Listar os endpoints de entrada declarados pela aplicação, exceto rotas geradas pelo framework; chamadas downstream não são entradas.
4. Pesquisar e analisar cada endpoint ou operação usando o asset como roteiro: contratos, fluxo, erros, comunicações, dependências e referências a arquivo e linha.
5. Verificar bibliotecas envolvidas em `dominios/srvs-shared/<lib-nome>`.
6. Manter processos assíncronos e externos separados do fluxo principal.
7. Conferir se cada seção do asset está preenchida com evidência ou com o marcador adequado.
8. Devolver ao Donda o conteúdo estruturado conforme o asset, um resultado por endpoint ou operação, para persistência posterior do operador.

## Regras

- Ler somente arquivos relacionados ao fluxo; não repetir verificações já feitas.
- Não inventar contratos, payloads, respostas ou resultados; usar `NAO LOCALIZADO` ou `NAO VERIFICADO` quando aplicável.
