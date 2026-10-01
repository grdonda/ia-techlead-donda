# Workflow: fluxo

Mapeamento, somente para leitura, do fluxo de um ou mais endpoints de microserviço ou operações de biblioteca.

## Objetivo

Mapear o caminho entre a entrada, o processamento interno, as comunicações realizadas e os retornos produzidos, incluindo os caminhos de erro identificáveis no código.

## Entradas

- Pedido do usuário com o serviço ou biblioteca e o endpoint/operação, ou com o escopo de mapear todas as entradas declaradas pela aplicação.
- Repositório disponível no workspace em um dos caminhos:
  - microserviço de projeto: `dominios/<projeto>/srvs/<srv-nome>`;
  - microserviço compartilhado: `dominios/srvs/<srv-nome>`;
  - biblioteca: `dominios/srvs-shared/<lib-nome>`.
- Artefatos anteriores do mesmo mapeamento, quando existirem.

Se o serviço, repositório ou endpoint não puder ser identificado ou lido, registrar o bloqueio e solicitar o dado ausente ao Donda; não deduzir o fluxo apenas pelo nome do serviço.

## Saídas

O `operador` deve criar um artefato por endpoint ou operação, a partir de uma cópia do asset, preservando seus títulos e sua estrutura. O nome deve combinar o método HTTP com o caminho do endpoint, normalizando separadores e caracteres inválidos; para bibliotecas sem endpoint HTTP, usar o nome da operação.

Quando a análise for repetida, o plano do Donda deve listar os arquivos do mesmo escopo que serão substituídos e obter autorização antes de alterá-los. Preservar todos os artefatos fora do escopo.

- microserviço de projeto: `dominios/<projeto>/srvs/analises/fluxo/<srv-nome>/<metodo>-<endpoint-slug>.md`;
- microserviço compartilhado: `dominios/srvs/analises/fluxo/<srv-nome>/<metodo>-<endpoint-slug>.md`;
- biblioteca: `dominios/srvs-shared/analises/fluxo/<lib-nome>/<operacao-slug>.md`.
- Criar um artefato por endpoint de entrada declarado pela aplicação, exceto rotas geradas automaticamente pelo framework. Não tratar chamadas downstream como endpoints de entrada.

## Etapas

1. Confirmar a autorização recebida do Donda e identificar serviço/biblioteca, repositório e escopo dos endpoints/operações.
2. Registrar a branch analisada uma única vez. Se não puder ser confirmada, marcar `NAO VERIFICADO` no asset e continuar; não repetir a análise apenas para confirmar a branch.
3. Ler o asset [fluxo.md](../assets/fluxo.md), as fontes relacionadas ao fluxo e somente os artefatos anteriores do escopo que serão substituídos, sem alterá-los.
4. Para escopo de serviço, identificar em uma passagem os endpoints de entrada declarados pela aplicação, excluindo rotas geradas pelo framework. Encaminhar ao `dev-analista` uma única solicitação com a lista e as fontes relevantes; pedir um mapeamento independente por endpoint, com contratos, fluxo, erros e referências a arquivos e linhas.
5. Verificar a completude de cada endpoint contra o asset. Seções sem confirmação devem ser marcadas `PENDENTE`, `NAO LOCALIZADO` ou `NAO VERIFICADO`; não apresentar inferências como fatos.
6. Encaminhar ao `operador`, em um único lote, os mapeamentos estruturados, o asset e o destino de cada artefato autorizado, preservando títulos e estrutura.
7. Aguardar a confirmação do `operador` com os caminhos, operações e status persistidos; então retornar o resultado ao Donda.

## Regras

- Este workflow é somente de leitura para código: não solicitar nem realizar alterações de implementação, configuração ou testes.
- Leia somente arquivos relacionados ao fluxo.
- O `dev-analista` analisa o repositório, mas não persiste o artefato documental.
- O `operador` persiste o documento usando o asset; não complementa nem altera a análise recebida.
- Não inventar comportamento, contratos, dependências ou solução técnica.
- Basear o mapeamento em código, configuração, testes ou documentação localizados e registrar as referências no asset.
- Se o código não permitir confirmar uma informação, registrá-la como não verificada ou pendente.
- Em uma repetição autorizada, substituir apenas os artefatos listados no plano aprovado; não remover arquivos de outros endpoints ou análises.
- Não abrir novas rodadas de análise para repetir verificações já feitas; registrar dúvidas pontuais como não verificadas, salvo se impedirem o mapeamento solicitado.
