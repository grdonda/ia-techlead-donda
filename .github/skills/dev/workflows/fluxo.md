# Workflow: fluxo

Mapeamento, somente para leitura, do fluxo de um ou mais endpoints de microserviço ou operações de biblioteca.

## Objetivo

Mapear o caminho entre a entrada, o processamento interno, as comunicações realizadas e os retornos produzidos, incluindo os caminhos de erro identificáveis no código.

## Entradas

- microserviço de projeto: `dominios/<projeto>/srvs/<srv-nome>`;
- microserviço compartilhado: `dominios/srvs/<srv-nome>`;
- biblioteca: `dominios/srvs-shared/<lib-nome>`.

## Saídas

- microserviço de projeto: `dominios/<projeto>/srvs/analises/fluxo/<srv-nome>/<metodo>-<endpoint-slug>.md`;
- microserviço compartilhado: `dominios/srvs/analises/fluxo/<srv-nome>/<metodo>-<endpoint-slug>.md`;
- biblioteca: `dominios/srvs-shared/analises/fluxo/<lib-nome>/<operacao-slug>.md`.

O `operador` deve criar um artefato por endpoint ou operação, a partir de uma cópia do asset, preservando seus títulos.
O nome deve combinar o método HTTP com o caminho do endpoint, normalizando separadores e caracteres inválidos; para bibliotecas sem endpoint HTTP, usar o nome da operação.

## Etapas

1. Confirmar a autorização recebida do Donda e identificar serviço/biblioteca, repositório e escopo dos endpoints/operações.
2. Registrar a branch analisada uma única vez. Se não puder ser confirmada, marcar `NAO VERIFICADO` no asset e continuar; não repetir a análise apenas para confirmar a branch.
3. Ler o asset como tópicos a serem pesquisados pelo agente, as fontes relacionadas ao fluxo, sem alterá-los.
4. Analisar os properties e a configuração para identificar comunicações externas (endpoints, filas, bancos).
5. Para escopo de serviço, identificar em uma passagem os endpoints de entrada declarados pela aplicação, excluindo rotas geradas pelo framework. Encaminhar ao `dev-analista` uma única solicitação com a lista e as fontes relevantes; pedir um mapeamento independente por endpoint, com contratos, fluxo, erros, comunicações e dependências e referências a arquivos e linhas de acordo com as instruções de preenchimento do asset.
6. Levantar os serviços e bibliotecas envolvidos e verificar em `dominios/srvs-shared/<lib-nome>`; se não estiver clonada, registrar `NAO VERIFICADO` e retornar ao Donda a pendência de clone.
7. Separar comunicação assíncrona e externa como processos à parte do fluxo principal (ex.: identificação de cliente, classificador de texto).
8. Verificar a completude de cada endpoint contra o asset. Seções sem confirmação devem ser marcadas `PENDENTE`, `NAO LOCALIZADO` ou `NAO VERIFICADO`; não apresentar inferências como fatos.
9. Encaminhar ao `operador`, em um único lote, os mapeamentos estruturados, o asset e o destino de cada artefato autorizado, preservando títulos e estrutura.
10. Aguardar a confirmação do `operador` com os caminhos, operações e status persistidos; então retornar o resultado ao Donda.

## Regras

- Este workflow é somente de leitura para código: não solicitar nem realizar alterações de implementação, configuração ou testes.
- Leia somente arquivos relacionados ao fluxo.
- Basear o mapeamento em código, configuração, testes ou documentação localizados e registrar as referências no asset.
- Se o código não permitir confirmar uma informação, registrá-la como não verificada ou pendente.
- Em uma repetição autorizada, substituir apenas os artefatos listados no plano aprovado; não remover arquivos de outros endpoints ou análises.
- Não abrir novas rodadas de análise para repetir verificações já feitas; registrar dúvidas pontuais como não verificadas, salvo se impedirem o mapeamento solicitado.
- Criar um artefato por endpoint de entrada declarado pela aplicação, exceto rotas geradas automaticamente pelo framework.
- Não tratar chamadas downstream como endpoints de entrada.
- Analisar bibliotecas somente no uso dentro do fluxo; biblioteca não clonada não bloqueia o mapeamento e deve ser registrada como `NAO VERIFICADO`.

## Asset

- [fluxo.md](../assets/fluxo.md)
- preservar somente as seções; o conteudo de orientação deve ser sobrescrito pela analise.
