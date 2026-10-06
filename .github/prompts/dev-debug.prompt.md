---
name: dev-debug
description: Investiga um erro reportado até a causa raiz e a correção.
argument-hint: "<serviço> trace_id=<id> [log ou relato]"
agent: Donda
---

Processo `debug` da skill [developer](../skills/developer/SKILL.md).

Pacote de evidência: ${input:alvo:serviço, trace_id ou conversation_id e log do erro}
