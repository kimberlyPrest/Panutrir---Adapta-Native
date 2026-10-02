# Fase 1 — Tasks

> Projeto: Panutrir — Sistema de Metas Comerciais
> Contrato documental v0.9.3 + EMENDA 01/2026 (23/09)

## Tasks

| ID | Task | SPEC | Leva | Status |
|----|------|------|------|--------|
| T1.1 | Bootstrap Supabase + RLS + papéis | SPEC-1-001 | A | ✔ concluída (QA v0.0.8, teste humano 6/6) |
| T2.1 | Importação de bases + catálogo | SPEC-1-002 | B | ✔ concluída (QA v0.0.10, teste humano 6/6) |
| T2.1b | **Revisão de contratos com a metodologia oficial (EMENDA 01/2026)** | SPEC-1-002 | B | ✔ concluída (QA v0.0.13, teste humano aprovado 02/10) |
| T4.1 | Cálculo de potencial | SPEC-1-004 | D | ✔ concluída (QA v0.0.12, teste humano aprovado 01/10) |
| T6.2 | Distribuição de metas com fórmula oficial | SPEC-1-006 | F | aberta (desbloqueada pela conclusão da T2.1b) |
| T6.x | Demais tasks da leva F | SPEC-1-006 | F | desbloqueadas; aguardam seleção em novo pedido |

## Bloqueios

- **EMENDA 01/2026 aplicada**: T2.1b concluída em 02/10/2026 — o bloqueio das
  tasks 2-010..016 está encerrado.
- CSV histórico do cliente segue como gate de execução (G1–G3).

## Histórico

- 02/10: T2.1b concluída — contratos revisados contra a metodologia oficial de
  cálculo da meta: vendas v1.1.0 (venda líquida + canal direto/indireto),
  produtos v1.1.0 (linha Branco/Especial), novo contrato `parametros_calculo`
  v1.0.0 (parâmetros versionados, valores sintéticos), catálogo v1.1.0 com
  rastreabilidade bloco a bloco; QA v0.0.13; leva F desbloqueada.
- 01/10: T4.1 concluída — modelo temporal do catálogo canônico (6 tabelas com
  RLS, 5 constraints EXCLUDE anti-sobreposição, pendências de resolução);
  QA v0.0.12; banco restaurado após pausa do Supabase e revalidado.
- 23/09: EMENDA 01/2026 aplicada — TASK-2.1b aberta; T6.2 passa a usar a
  fórmula oficial da memória de cálculo ago/2026.
- 17/09: T4.1 movida para verificação humana.
- 16/09: T1.1 e T2.1 concluídas com teste humano 6/6.
