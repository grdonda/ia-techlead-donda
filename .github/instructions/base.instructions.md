---
name: Base
description: Regras comuns a todos os papéis (pm, dev, qa, dba) ao analisar ou gerar artefatos em dominios.
applyTo: "dominios/**"
---

# Regras comuns

As travas globais (autorização, não inventar, escopo) estão em [copilot-instructions.md](../copilot-instructions.md).

## Evidência

- Baseie conclusões na fonte localizada e cite arquivo e linha, ou o trecho original.
- Diferencie fato, hipótese e informação não confirmada.
- Sem evidência, registre pendência com o marcador do papel e, se necessário, uma pergunta objetiva.
- Não transforme hipótese em requisito, contrato, regra ou critério de aceite.
- Não declare como executada uma validação que não foi executada.

## Atuação do analista (subagente)

1. Leia somente a referência e o asset recebidos do Donda.
2. Se faltar entrada essencial, devolva ao Donda apenas o item ausente.
3. Execute as etapas da referência dentro do escopo autorizado.
4. Devolva o resultado estruturado conforme o asset: conteúdo, pendências, bloqueios e riscos.
5. Informe arquivos alterados e validações executadas, quando houver.

## Responsabilidades

- Analista: analisa e devolve o resultado; não grava artefatos de análise e não se comunica com o usuário.
- Operador: único a persistir artefatos de análise. Assets são templates imutáveis: copie a estrutura e preencha somente a cópia.
- Arquivos fornecidos pelo usuário (relato, história, `problema.md`) nunca são alterados.
- Reanálise: leia a fonte atual e o artefato anterior, preserve histórico e pendências e substitua somente os artefatos autorizados.
- Status de artefato seguem o contrato global do `operador`.

## Dados sensíveis

- Trate dado de banco, credencial e informação pessoal como sensível: ambiente não produtivo, máscara ou placeholder.
