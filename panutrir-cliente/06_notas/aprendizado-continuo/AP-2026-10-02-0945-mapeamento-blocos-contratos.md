# AP-2026-10-02-0945 — Mapeamento bloco a bloco da metodologia oficial nos contratos

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T2.1b / SPEC-1-002 (EMENDA 01/2026)
- Sinal: ao incorporar uma metodologia oficial de cálculo por emenda, a revisão dos contratos de dados só é verificável quando cada bloco do cálculo é mapeado explicitamente para o contrato/estrutura que fornece o insumo — e os valores oficiais dos parâmetros permanecem bloqueados até os gates de dados reais.
- Evidência: `contracts/catalogo-schemas.json` v1.1.0, seção `methodology_traceability` (8 blocos mapeados); fixtures em `fixtures/synthetic/` com `origem` restrita a SINTETICO (caso inválido I-020 rejeita OFICIAL); QA do Skip v0.0.13 passou.
- Regra reutilizável: quando uma emenda introduz uma fórmula/método oficial, criar uma seção de rastreabilidade bloco→contrato no catálogo de schemas e versionar a estrutura dos parâmetros com valores sintéticos, reservando os valores oficiais para a task de implementação do cálculo.
- Quando aplicar: qualquer task de revisão de contratos/estruturas disparada por mudança de metodologia ou fórmula oficial.
- Quando não aplicar: mudanças puramente estruturais sem fórmula associada (não há blocos a mapear).
- Confiança: alta — mapeamento verificado bloco a bloco no catálogo v1.1.0 e aprovado pelo champion.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
