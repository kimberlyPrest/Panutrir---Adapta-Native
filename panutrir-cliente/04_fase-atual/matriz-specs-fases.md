# Matriz SPECs × Tasks — Fase 2 (fase aberta)

Localização canônica: `04_fase-atual/`. A fase está aberta; a execução está **liberada** pela consultora (Kim, 04/11/2026).

Fonte única documental: `tasks.json`. As tabelas em `fase.md`, nas seis SPECs e nesta matriz devem permanecer coerentes. A liberação não fecha gates: tasks 🔒 seguem bloqueadas até suas pré-condições.

Legenda: ☐ a fazer · 🔒 bloqueada · ✔ concluída.

## Cobertura por SPEC

| SPEC | Tasks | CAs cobertos | Levas |
|---|---|---|---|
| SPEC-2-001 | T2.1.1, T2.1.2, T2.1.3, T2.1.4, T2.1.5 | CA-2-01, CA-2-02, CA-2-03, CA-2-04, CA-2-05 | A, B, D |
| SPEC-2-002 | T2.2.1, T2.2.2, T2.2.3, T2.2.4 | CA-2-06, CA-2-07, CA-2-08, CA-2-09, CA-2-10 | A, B, C |
| SPEC-2-003 | T2.3.1, T2.3.2, T2.3.3, T2.3.4 | CA-2-11, CA-2-12, CA-2-13, CA-2-14, CA-2-15 | B, C, D |
| SPEC-2-004 | T2.4.1, T2.4.2, T2.4.3, T2.4.4, T2.4.5, T2.4.6 | CA-2-16, CA-2-17, CA-2-18, CA-2-19, CA-2-20, CA-2-21, CA-2-22 | A, B, C, D, E |
| SPEC-2-005 | T2.5.1, T2.5.2, T2.5.3, T2.5.4, T2.5.5 | CA-2-23, CA-2-24, CA-2-25, CA-2-26, CA-2-27 | A, B, C, E |
| SPEC-2-006 | T2.6.1, T2.6.2, T2.6.3 | CA-2-28, CA-2-29, CA-2-30, CA-2-31 | A, B, C |

## Cobertura de critérios de aceite

| CA | SPEC | Tasks que provam |
|---|---|---|
| CA-2-01 | SPEC-2-001 | T2.1.1 |
| CA-2-02 | SPEC-2-001 | T2.1.3 |
| CA-2-03 | SPEC-2-001 | T2.1.5 |
| CA-2-04 | SPEC-2-001 | T2.1.4 |
| CA-2-05 | SPEC-2-001 | T2.1.2 |
| CA-2-06 | SPEC-2-002 | T2.2.1 |
| CA-2-07 | SPEC-2-002 | T2.2.3 |
| CA-2-08 | SPEC-2-002 | T2.2.4 |
| CA-2-09 | SPEC-2-002 | T2.2.2 |
| CA-2-10 | SPEC-2-002 | T2.2.4 |
| CA-2-11 | SPEC-2-003 | T2.3.1 |
| CA-2-12 | SPEC-2-003 | T2.3.3 |
| CA-2-13 | SPEC-2-003 | T2.3.4 |
| CA-2-14 | SPEC-2-003 | T2.3.2 |
| CA-2-15 | SPEC-2-003 | T2.3.3 |
| CA-2-16 | SPEC-2-004 | T2.4.1 |
| CA-2-17 | SPEC-2-004 | T2.4.2 |
| CA-2-18 | SPEC-2-004 | T2.4.3 |
| CA-2-19 | SPEC-2-004 | T2.4.1 |
| CA-2-20 | SPEC-2-004 | T2.4.4 |
| CA-2-21 | SPEC-2-004 | T2.4.6 |
| CA-2-22 | SPEC-2-004 | T2.4.5 |
| CA-2-23 | SPEC-2-005 | T2.5.1 |
| CA-2-24 | SPEC-2-005 | T2.5.2 |
| CA-2-25 | SPEC-2-005 | T2.5.3 |
| CA-2-26 | SPEC-2-005 | T2.5.4 |
| CA-2-27 | SPEC-2-005 | T2.5.5 |
| CA-2-28 | SPEC-2-006 | T2.6.1 |
| CA-2-29 | SPEC-2-006 | T2.6.2 |
| CA-2-30 | SPEC-2-006 | T2.6.3 |
| CA-2-31 | SPEC-2-006 | T2.6.1 |

## Dependências entre tasks

| Task | Depende de | Leva |
|---|---|---|
| T2.1.1 | — | A |
| T2.2.1 | — | A |
| T2.4.1 | — | A |
| T2.5.1 | — | A |
| T2.6.1 | — | A |
| T2.1.2 | T2.1.1 | B |
| T2.1.3 | — | B |
| T2.1.4 | T2.1.1 | B |
| T2.2.2 | T2.2.1 | B |
| T2.2.3 | — | B |
| T2.3.1 | — | B |
| T2.4.2 | T2.4.1 | B |
| T2.5.2 | T2.5.1 | B |
| T2.6.2 | T2.6.1 | B |
| T2.2.4 | T2.2.1 | C |
| T2.3.2 | T2.3.1 | C |
| T2.3.3 | T2.3.1 | C |
| T2.4.3 | T2.4.2 | C |
| T2.5.3 | T2.5.1, T2.5.2 | C |
| T2.5.4 | T2.4.2, T2.5.2 | C |
| T2.6.3 | T2.6.2 | C |
| T2.1.5 | T2.1.2, T2.1.3, T2.4.2 | D |
| T2.3.4 | T2.3.3 | D |
| T2.4.4 | T2.4.2 | D |
| T2.4.5 | T2.4.2 | D |
| T2.4.6 | T2.1.5, T2.4.4, T2.4.5, T2.6.2, T2.5.4 | E |
| T2.5.5 | T2.5.3 | E |

## Ordem por leva

- **A:** T2.1.1, T2.2.1, T2.4.1, T2.5.1, T2.6.1
- **B:** T2.1.2, T2.1.3, T2.1.4, T2.2.2, T2.2.3, T2.3.1, T2.4.2, T2.5.2, T2.6.2
- **C:** T2.2.4, T2.3.2, T2.3.3, T2.4.3, T2.5.3, T2.5.4, T2.6.3
- **D:** T2.1.5, T2.3.4, T2.4.4, T2.4.5
- **E:** T2.4.6, T2.5.5
