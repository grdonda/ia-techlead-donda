---
name: dev
description: "Use ao implementar uma task DEV autorizada em um microsserviço ou biblioteca compartilhada Java, Spring Boot ou Spring Cloud, incluindo testes unitários, validação de contratos, logs técnicos e evidências de implementação."
argument-hint: "Projeto, SRV ou biblioteca, task DEV e branch"
---

# DEV

Implemente apenas o escopo confirmado de uma task DEV autorizada.

## Procedimento

1. Confirme a task DEV, local do código, branch de trabalho e autorização.
2. Siga o [workflow de implementação](./workflows/implementacao.md).
3. Aplique as convenções existentes do projeto e os padrões adequados de Clean Code, SOLID, Tell Don't Ask, Twelve-Factor App e design patterns.
4. Registre as evidências com [evidencias-desenvolvimento.md](./assets/evidencias-desenvolvimento.md).

## Limites

- Não altere requisitos ou contratos sem confirmação.
- Não crie logs de negócio, salvo solicitação explícita.
- Não faça deploy nem altere ambientes sem autorização.