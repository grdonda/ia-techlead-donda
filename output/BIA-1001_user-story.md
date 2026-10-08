# BIA-1001 — Aplicar lib de log de negócio no projeto do WhatsApp PJ para registrar segmento

---
status: pendente
data-criacao: 2026-10-08
data-atualizacao: 2026-10-08
origem: Solicitação do usuário
---

## Identificação

- **Eu como:** time técnico responsável pelo projeto WhatsApp PJ
- **Quero:** integrar a biblioteca oficial de log de negócio para registrar o segmento do cliente
- **Para:** disponibilizar o JSON gerado ao time do dashboard de negócio, com os logs no Databricks

## Detalhamento do Negócio

### Regras de Negócio

- O log de negócio deve registrar o segmento do cliente. Os dados destinados ao dashboard devem seguir a definição já feita pelo PM; os campos e o formato não foram fornecidos neste contexto.

## Critérios de Aceite

- [ ] Após a integração, o fluxo registra o segmento do cliente, gera JSON consumível pelo time do dashboard de negócio e mantém os logs no Databricks. Os campos e o formato do JSON devem corresponder à definição do PM, ainda pendente de confirmação.

## Detalhamento Técnico

### Regras Técnicas

#### 1. Feature Toggle

- [preencher]

#### 2. Microserviço

- Alvo informado: projeto WhatsApp PJ. Nome técnico do microserviço ou repositório: [preencher]

#### 3. Integração

- Confirmar a biblioteca oficial, possivelmente `wats-lib-bia-log-negocio`, e sua versão; seguir a documentação oficial. A integração deve gerar JSON para consumo pelo time do dashboard e registrar os logs no Databricks.

#### 4. Testes

- [preencher]

#### 5. Segurança e Performance

- [preencher]

## Riscos e Dependências

- **Dependência:** confirmação da biblioteca oficial e acesso à sua documentação; definição do PM para os campos e o formato do JSON.
- **Risco:** sem a biblioteca e o contrato do JSON confirmados, não é possível validar a compatibilidade nem o consumo pelo dashboard.

## Test Coverage

- [preencher]

## Attachments

- https://github.com/Bradesco-Core/wats-srv-bia-varejo-gerenciado

## Observações

- O PM já definiu o que deve ir ao dashboard, mas essa definição não foi incluída nas entradas fornecidas.

## Pendências

- [preencher] Confirmar biblioteca oficial, versão e documentação aplicável.
- [preencher] Informar os campos e o formato do JSON definidos pelo PM, incluindo como representar o segmento.
- [preencher] Identificar o microserviço ou repositório técnico do WhatsApp PJ.
- [preencher] Definir testes, cobertura esperada e requisitos de segurança e performance.
- [preencher] Confirmar se Feature Toggle é aplicável.

## Histórico

| Data | Operação | Origem | Status |
|---|---|---|---|
| 2026-10-08 | Criação da história | Solicitação do usuário | pendente |