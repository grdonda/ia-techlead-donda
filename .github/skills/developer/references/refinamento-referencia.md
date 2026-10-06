# Processo: refinamento

Produz User Story e refinamento rastreáveis a partir de um relato local ou de uma história oficial.
Estrutura de pastas: [dominios](../../../instructions/dominios.instructions.md).

## Cenários

### Relato local

Usar quando a entrada for um problema ou demanda ad hoc em `dominios/refinamentos/<assuntos>/problema.md`.

Entradas:

- `problema.md`.
- Anexos referenciados pelo relato.
- História anterior, se existir no mesmo conjunto, apenas como contexto histórico.

Regras do cenário:

- Não exigir serviço, Figma ou Git.
- Ler o problema, os anexos e os artefatos anteriores disponíveis.
- Gerar primeiro `historia.md` e depois `refinamento.md`.
- Registrar pendências objetivas quando algo faltar, sem inventar informação.

Saída:

| Cenário | Artefato | Asset |
| --- | --- | --- |
| Relato | `dominios/refinamentos/<assuntos>/historia.md` | [historia](../assets/historia.md) |
| Relato | `dominios/refinamentos/<assuntos>/refinamento.md` | [refinamento-asset](../assets/refinamento-asset.md) |

### História

Usar quando a entrada for uma história oficial em `dominios/<projetos>/historias/<jira-id>/<jira-id>.md`.

Entradas:

- História oficial.
- Refinamento anterior, se existir.
- Figma, quando anexado ou mencionado e acessível.
- Serviço relacionado, quando existir no diretório canônico do projeto ou quando estiver mencionado na história e for localizado no workspace.

Regras do cenário:

- Ler a história oficial e o refinamento anterior antes de atualizar.
- Se houver Figma acessível, usá-lo como fonte factual adicional.
- Se o serviço for relevante, localizar apenas o repositório canônico do domínio e tratar o código como baseline observável, sem propor solução técnica.
- Se o nome do serviço for ambíguo, o repositório não existir ou a evidência não estiver acessível, registrar pendência e consultar o usuário somente se isso for necessário para prosseguir.
- Quando houver repo de serviço relevante e o processo tiver autorização para seguir, o workflow futuro deve avisar que vai atualizar o baseline; então validar o estado com `git status --short`, mudar para `main` e executar `git pull --ff-only` apenas se o estado local estiver limpo. Se houver alterações locais, `main` ausente, conflito ou pull falhar, parar de usar o código como baseline e registrar pendência. Não forçar, não stash, não resetar.
- Após o `git pull --ff-only`, informar ao usuário o resultado da atualização da branch ou a falha ocorrida; se houver erro, parar de usar o baseline e manter a regra de interrupção.
- Comparar o estado atual confirmado com o comportamento desejado e enriquecer os critérios de aceite.

Saída:

| Cenário | Artefato | Asset |
| --- | --- | --- |
| História | `dominios/<projetos>/historias/<jira-id>/refinamento/<jira-id>_refinamento.md` | [refinamento-asset](../assets/refinamento-asset.md) |

## Regras

- A análise de produto do Developer é factual, read-only e limitada ao refinamento.
- Não desenhar solução técnica, não implementar e não fazer análise técnica profunda.
- Não substituir o `tech-review` do Developer.
- O baseline de serviço serve apenas para comparação factual com o comportamento desejado e para enriquecer critérios de aceite rastreáveis à história ou ao Figma.
- Preservar histórico, informações ainda válidas, pendências e `data-atualizacao`.
- Só considerar uma informação resolvida com evidência ou declaração explícita na fonte atualizada.
- Não emitir detalhes intermediários da análise no chat.