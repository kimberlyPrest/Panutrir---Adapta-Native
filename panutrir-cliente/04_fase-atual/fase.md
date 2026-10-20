# Fase 1 — Motor de meta Cliente × SKU com dados reais

**Estado:** ABERTA — reescrita pela EMENDA 02/2026 (20/10/2026)  
**Janela indicativa:** 20/10 – 14/11/2026  
**Objetivo:** o sistema calcula a meta de Out/26 com dados reais pela metodologia oficial e reproduz a planilha do Paulo: R$13.000.000,00 fechados, gabarito batendo e cada número explicado.

## Entrega demonstrável

Paulo e Léo abrem o painel do ciclo Out/26, veem os controles da planilha lado a lado com o gabarito (G-01..G-18), descem de Empresa até um Cliente × SKU escolhido por eles e entendem de onde veio o número.

## SPECs

| SPEC | Tema | Requisitos |
|---|---|---|
| SPEC-1-001 | Acesso, papéis e ciclo de meta | RF-01, RF-02 |
| SPEC-1-002 | Carga das bases reais de vendas | RF-03, RF-04 |
| SPEC-1-003 | Parâmetros, calendário e execução versionada | RF-05, RF-06, RF-07 |
| SPEC-1-004 | Estrutura comercial, produtos e auditoria | RF-04, RF-08 |
| SPEC-1-005 | Motor da Meta Original | RF-09, RF-10 |
| SPEC-1-006 | GAP da Diretoria e distribuição | RF-11, RF-12, RF-13 |
| SPEC-1-007 | Gabarito, painel de controles e consulta | RF-14, RF-15, RF-16 |

## Critérios de aceite da fase

CA-1-01 a CA-1-25, detalhados nas SPECs. O bloqueante é **CA-1-21**: o teste de gabarito passa em G-01..G-18.

## Tasks

A ordem, as dependências e o status estão em `matriz-specs-fases.md` (fonte única). Resumo por leva:

| Leva | Tasks |
|---|---|
| — | T1.1 ✔ · T2.1 ✔ · T2.1b ✔ · T4.1 ✔ |
| A | T1.2 · T1.3 · T2.1c · T3.1 |
| B | T1.4 · T2.2 · T3.2 · T4.2 |
| C | T2.3 · T3.3 |
| D | T4.3 · T5.1 |
| E | T5.2 · T5.3 |
| F | T5.4 · T5.5 |
| G | T5.6 |
| H | T6.1 |
| I | T6.2 |
| J | T6.3 |
| K | T6.4 · T7.1 |
| L | T7.2 · T7.3 · T7.4 |
| M | T7.5 |

## Perguntas ao cliente desta fase

Q-01..Q-25 e Q-39..Q-42 em `03_documentos/perguntas-ao-cliente.md`. Elas **não bloqueiam o início**: cada task pergunta quando precisa (protocolo em `AGENTS.md`).

## Fora desta fase

Aprovação/publicação, consulta pela equipe, cenários, acompanhamento, logística e IA.

## Histórico

- 20/10: EMENDA 02 — fase reescrita (dados reais, metodologia Out/26, Cliente × SKU). Tasks T1.1, T2.1, T2.1b e T4.1 aproveitadas; as demais tasks antigas foram canceladas ou absorvidas (ver matriz). As DÚVIDAS de 02/10 (T1.2, T6.2, blocos 9–10, origem OFICIAL) foram resolvidas pela emenda.
- 02/10: T2.1b concluída; T1.2 e T6.2 bloqueadas por dúvidas.
- 01/10: T4.1 concluída; banco restaurado após pausa do Supabase.
- 23/09: EMENDA 01 (superada).
- 16/09: T1.1 e T2.1 concluídas.
