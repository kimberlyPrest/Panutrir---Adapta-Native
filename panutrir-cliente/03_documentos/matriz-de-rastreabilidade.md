# Matriz de rastreabilidade (PRD v1.0 — EMENDA 02/2026)

## Metodologia → SPEC → Task

| Regra | Tema | SPEC | Tasks | Gabarito |
|---|---|---|---|---|
| M-01 | Bottom-up Cliente × SKU | SPEC-1-005, SPEC-1-006 | T5.1, T6.4 | G-01 |
| M-02 | Venda líquida | SPEC-1-002 | T2.1c, T2.2 | — |
| M-03 | Exclusão de Panettone | SPEC-1-004, SPEC-1-005 | T4.2, T5.1 | — |
| M-04 | Estrutura atual | SPEC-1-004 | T4.2, T4.3 | G-18 |
| M-05 | Elegibilidade 3 meses | SPEC-1-005 | T5.1 | G-11 |
| M-06 | Sortimento Assaí SP | SPEC-1-003, SPEC-1-005 | T3.1, T5.1 | — |
| M-07..M-11 | Motor 24M, produtividade, Pbase, baseline, G | SPEC-1-003, SPEC-1-005 | T3.2, T5.2 | — |
| M-12, M-13 | Introdução | SPEC-1-005 | T5.3 | G-12, G-13 |
| M-14 | Piso técnico | SPEC-1-005 | T5.4 | G-14 |
| M-15, M-16 | Substituição PlufiNut | SPEC-1-005 | T5.5 | G-15, G-16 |
| M-17, M-28 | Meta Original | SPEC-1-005 | T5.6 | G-02, G-05 |
| M-18..M-20 | GAP, Indireto, Direto | SPEC-1-006 | T6.1 | G-03, G-04, G-06, G-07 |
| M-21..M-23 | Mix, convergência, GAP por linha | SPEC-1-006 | T6.2 | G-08, G-09, G-10 |
| M-24, M-25, M-29, M-30 | Descida, promotor em branco, fechamentos | SPEC-1-006 | T6.3 | G-01, G-03 |
| M-26 | REVISAR < R$300 | SPEC-1-007 | T7.2 | G-17 |
| M-27 | Auditoria de estrutura | SPEC-1-004, SPEC-1-007 | T4.3, T7.2 | G-18 |
| M-31 | Consolidações | SPEC-1-006, SPEC-1-007 | T6.4, T7.3 | — |

## Requisito → SPEC → Fase

| Requisito | SPEC | Fase |
|---|---|---|
| RF-01, RF-02 | SPEC-1-001 | 1 |
| RF-03 | SPEC-1-002 | 1 |
| RF-04 | SPEC-1-002, SPEC-1-004 | 1 |
| RF-05, RF-07 | SPEC-1-003 | 1 |
| RF-06 | SPEC-1-003, SPEC-2-002 | 1–2 |
| RF-08 | SPEC-1-004 | 1 |
| RF-09, RF-10 | SPEC-1-005 | 1 |
| RF-11..RF-13 | SPEC-1-006 | 1 |
| RF-14..RF-16 | SPEC-1-007 | 1 |
| RF-17 | SPEC-2-001 | 2 |
| RF-18 | SPEC-2-002 | 2 |
| RF-19 | SPEC-2-003 | 2 |
| RF-20..RF-22 | SPEC-2-004 | 2 |
| RF-23 | SPEC-3-001 | 3 |
| RF-24 | SPEC-3-002 | 3 |
| RF-25 | SPEC-3-003 | 3 |
| RF-26 | SPEC-3-004 | 3 (opcional) |
| RF-27 | SPEC-4-001 | 4 (paralelo à 1) |
| RF-28 | SPEC-4-002 | 4 |
| RF-29 | SPEC-4-003 | 4 |
| RF-30 | SPEC-5-001 | 5 |
| RF-31 | SPEC-5-002 | 5 |
| K1..K5 | SPEC-5-003 | 5 |

## PRD v0.1 → v1.0

| Antes | Depois |
|---|---|
| RF-01, RF-02 | RF-01, RF-02 |
| RF-03..RF-05 (importação, validação, quarentena) | RF-03, RF-04 (carga agregada e auditoria) |
| RF-06 (catálogo temporal) | RF-08 (estrutura atual) |
| RF-07 (versionamento/snapshot) | RF-05, RF-07 |
| RF-08, RF-09 (painel/simulação sintética) | RF-14..RF-16 |
| RF-10..RF-17 (motor, exceções, reconciliação) | RF-09..RF-13, RF-19 |
| RF-18..RF-20 (workflow, publicação, consulta) | RF-20, RF-21 |
| RF-21 (acompanhamento) | RF-23, RF-24 |
| RF-22, RF-23 (campanhas) | RF-26 (ROI promocional, opcional) |
| RF-24, RF-25 (IA) | RF-31 |
| RF-26 (exportação auditável) | RF-16, RF-22 |
| K3 potencial externo (Nielsen/Scanntech) | fora do escopo |
| RN-12 (sem histórico nunca gera zero) | revogada → RN-10 |
| RN-18 (carteira vigente na data da venda) | revogada → RN-03 |
| — | RF-27..RF-30 (Logística e integração) — novos |
