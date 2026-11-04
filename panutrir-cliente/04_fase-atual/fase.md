# Fase 1 — Motor de meta Cliente × SKU com dados reais

**Estado:** ACEITA (02/11/2026, T7.5/CA-1-25) — reescrita pela EMENDA 02/2026 (20/10/2026)  
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

## Teste do cliente

Por SPEC, não por task. Na Fase 1 são dois testes: o login com contas convidadas (SPEC-1-001, na T1.3) e a demonstração de Out/26 ao Paulo (SPEC-1-007, aceite da fase). As SPECs 1-002 a 1-006 fecham pela prova automática contra a fonte e o gabarito. Regra completa em `AGENTS.md`.

## Tasks

Visão operacional das 30 tasks da fase. A **ordem, as dependências e o status** continuam vindo de
`matriz-specs-fases.md` (fonte única); se houver divergência, vale a matriz. Os campos `Task`,
`Dono`, `Critério`, `Evidência esperada` e `Pré-condições` são os de `## Tasks vinculadas` da SPEC
de cada task; `Recorte da prova` é a linha GREEN do `## TDD` da SPEC e `Leva` é a da matriz.
**28 concluídas; abertas: T1.3 e T5.1.**

| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência esperada | Pré-condições | Status | Leva |
|---|---|---|---|---|---|---|---|---|---|
| T1.1 | Matriz papel×operação em migrations | Engenharia | SPEC-1-001 | concluída em 16/09 (QA v0.0.8, teste humano 6/6) | TDD da SPEC-1-001, GREEN: `SPEC-1-001/GREEN`: criar, repetir, negar | concluída em 16/09 (QA v0.0.8, teste humano 6/6) | — | ✔ 16/09 | — |
| T2.1 | Contratos e fixtures sintéticas | Dados | SPEC-1-002 | concluída em 16/09 (QA v0.0.10) | TDD da SPEC-1-002, GREEN: `SPEC-1-002/GREEN` com fixture sintética; depois com a base real | concluída em 16/09 (QA v0.0.10) | — | ✔ 16/09 | — |
| T2.1b | Contratos × metodologia ago/26 | Dados | SPEC-1-002 | concluída em 02/10 (QA v0.0.13); a regra "OFICIAL bloqueado" é retirada pela EMENDA 02 | TDD da SPEC-1-002, GREEN: `SPEC-1-002/GREEN` com fixture sintética; depois com a base real | concluída em 02/10 (QA v0.0.13); a regra "OFICIAL bloqueado" é retirada pela EMENDA 02 | — | ✔ 02/10 | — |
| T4.1 | Modelo temporal do catálogo canônico | Dados | SPEC-1-004 | concluída em 01/10 (QA v0.0.12); reaproveitada com um vínculo vigente aberto | TDD da SPEC-1-004, GREEN: `SPEC-1-004/GREEN` com fixture; depois com o DE→PARA real | concluída em 01/10 (QA v0.0.12); reaproveitada com um vínculo vigente aberto | — | ✔ 01/10 | — |
| T1.2 | Criar tabela/RPC do ciclo de meta, renomear operações da matriz e atribuir papéis reais | Léo | SPEC-1-001 | CA-1-01, CA-1-02 | TDD da SPEC-1-001, GREEN: `SPEC-1-001/GREEN`: criar, repetir, negar | CA-1-01 e CA-1-02 passam | T1.1 | ✔ 30/10 | A |
| T1.3 | Remover seed com senha da migration, trocar a senha exposta e provisionar contas por convite | Léo | SPEC-1-001 | CA-1-03 | TDD da SPEC-1-001, GREEN: `SPEC-1-001/GREEN`: criar, repetir, negar | CA-1-03; login das contas reais funciona | — | ☐ | A |
| T2.1c | Revisar o contrato `vendas` contra as colunas reais das congeladas (só o cabeçalho, sem copiar dados) e definir `venda_mensal` | Léo | SPEC-1-002 | contrato v2.0.0 mapeia cada campo de M-02 e M-05 | TDD da SPEC-1-002, GREEN: `SPEC-1-002/GREEN` com fixture sintética; depois com a base real | contrato v2.0.0 mapeia cada campo de M-02 e M-05 | T2.1b | ✔ 24/10 | A |
| T3.1 | Criar `parametros_versao`, sortimento e substituição como tabelas; carregar a versão Out/26 oficial | Léo | SPEC-1-003 | CA-1-07 | TDD da SPEC-1-003, GREEN: `SPEC-1-003/GREEN`: criar versão, alterar, consultar ambas; executar duas vezes | CA-1-07; Q-10 respondida | T2.1b | ✔ 24/10 | A |
| T1.4 | Provar negações por papel e repetição do ciclo | Léo | SPEC-1-001 | relatório papel×operação com 7 operações; repetição sem duplicar | TDD da SPEC-1-001, GREEN: `SPEC-1-001/GREEN`: criar, repetir, negar | relatório papel×operação com 7 operações; repetição sem duplicar | T1.2, T1.3 | ✔ 02/11 | B |
| T2.2 | Implementar o script de carga agregada mensal, idempotente por mês, com registro de carga | Léo | SPEC-1-002 | CA-1-05, CA-1-06 | TDD da SPEC-1-002, GREEN: `SPEC-1-002/GREEN` com fixture sintética; depois com a base real | CA-1-05 e CA-1-06 com fixture | T2.1c | ✔ 25/10 | B |
| T3.2 | Criar `calendario_mes` com dias úteis e IS (importar ou calcular conforme Q-08/Q-09) | Léo | SPEC-1-003 | CA-1-08 | TDD da SPEC-1-003, GREEN: `SPEC-1-003/GREEN`: criar versão, alterar, consultar ambas; executar duas vezes | CA-1-08; Q-08 e Q-09 respondidas | T3.1 | ✔ 30/10 | B |
| T4.2 | Carregar DE→PARA atual e base de produtos (linha, Panettone) nas tabelas da T4.1 | Léo | SPEC-1-004 | CA-1-11 | TDD da SPEC-1-004, GREEN: `SPEC-1-004/GREEN` com fixture; depois com o DE→PARA real | CA-1-11; Q-04 respondida | T4.1, T2.1c | ✔ 30/10 | B |
| T2.3 | Carregar Out/24–Set/26 reais e provar os totais por mês contra a fonte | Léo | SPEC-1-002 | CA-1-04 | TDD da SPEC-1-002, GREEN: `SPEC-1-002/GREEN` com fixture sintética; depois com a base real | CA-1-04: tabela mês × total fonte × total banco × diferença | T2.2 | ✔ 31/10 | C |
| T3.3 | Criar `execucao_calculo` e o vínculo dos resultados; provar reprodutibilidade | Léo | SPEC-1-003 | CA-1-09 | TDD da SPEC-1-003, GREEN: `SPEC-1-003/GREEN`: criar versão, alterar, consultar ambas; executar duas vezes | CA-1-09 | T3.1, T1.2 | ✔ 30/10 | C |
| T4.3 | Implementar a auditoria de estrutura e provar 27 clientes em Out/26 | Léo | SPEC-1-004 | CA-1-10, CA-1-12 | TDD da SPEC-1-004, GREEN: `SPEC-1-004/GREEN` com fixture; depois com o DE→PARA real | CA-1-10 e CA-1-12; Q-07 respondida | T4.2, T2.3 | ✔ 31/10 | D |
| T5.1 | Universo elegível, exclusões e sortimento restrito; fixture com casos calculados à mão para todos os regimes | Léo | SPEC-1-005 | CA-1-13 | TDD da SPEC-1-005, GREEN: `SPEC-1-005/GREEN`: fixture passa; depois Out/26 real contra o gabarito | CA-1-13; Q-41 respondida | T2.3, T3.1, T4.2 | ☐ | D |
| T5.2 | Motor 24M para maduros (produtividade, dessazonalização, blocos, Pbase, baseline, G) | Léo | SPEC-1-005 | casos de maduro da fixture passam; Q-12, Q-13 e Q-15 respondidas | TDD da SPEC-1-005, GREEN: `SPEC-1-005/GREEN`: fixture passa; depois Out/26 real contra o gabarito | casos de maduro da fixture passam; Q-12, Q-13 e Q-15 respondidas | T5.1, T3.2 | ✔ 02/11 | E |
| T5.3 | Regras de introdução e introdução com zero | Léo | SPEC-1-005 | G-12, G-13 | TDD da SPEC-1-005, GREEN: `SPEC-1-005/GREEN`: fixture passa; depois Out/26 real contra o gabarito | G-12 e G-13; Q-14 respondida | T5.1 | ✔ 02/11 | E |
| T5.4 | Piso técnico para maduros | Léo | SPEC-1-005 | G-14 | TDD da SPEC-1-005, GREEN: `SPEC-1-005/GREEN`: fixture passa; depois Out/26 real contra o gabarito | G-14; Q-39 respondida | T5.2 | ✔ 02/11 | F |
| T5.5 | Substituição PlufiNut → Pão de Leite (Assaí SP) a partir da tabela de substituição | Léo | SPEC-1-005 | G-15, G-16 | TDD da SPEC-1-005, GREEN: `SPEC-1-005/GREEN`: fixture passa; depois Out/26 real contra o gabarito | G-15 e G-16; Q-16 respondida | T5.2, T5.3 | ✔ 02/11 | F |
| T5.6 | Meta Original Ajustada, memória de cálculo e conferência dos totais Out/26 | Léo | SPEC-1-005 | CA-1-14, CA-1-15, CA-1-16 | TDD da SPEC-1-005, GREEN: `SPEC-1-005/GREEN`: fixture passa; depois Out/26 real contra o gabarito | CA-1-14, CA-1-15, CA-1-16 | T5.4, T5.5, T3.3 | ✔ 02/11 | G |
| T6.1 | GAP total e separação Indireto/Direto por responsável | Léo | SPEC-1-006 | CA-1-17 | TDD da SPEC-1-006, GREEN: `SPEC-1-006/GREEN` com a fixture; depois Out/26 real | CA-1-17; Q-17 e Q-20 respondidas | T5.6 | ✔ 02/11 | H |
| T6.2 | Mix de linha, convergência dos Especiais e GAP por linha | Léo | SPEC-1-006 | CA-1-18 | TDD da SPEC-1-006, GREEN: `SPEC-1-006/GREEN` com a fixture; depois Out/26 real | CA-1-18; Q-18, Q-19 e Q-42 respondidas | T6.1 | ✔ 02/11 | I |
| T6.3 | Descida do GAP até Cliente × SKU, Meta Final e promotor em branco | Léo | SPEC-1-006 | CA-1-19 | TDD da SPEC-1-006, GREEN: `SPEC-1-006/GREEN` com a fixture; depois Out/26 real | CA-1-19; Q-40 respondida | T6.2 | ✔ 02/11 | J |
| T6.4 | Consolidações em todos os níveis e prova de soma | Léo | SPEC-1-006 | CA-1-20 | TDD da SPEC-1-006, GREEN: `SPEC-1-006/GREEN` com a fixture; depois Out/26 real | CA-1-20 | T6.3 | ✔ 02/11 | K |
| T7.1 | Teste automatizado de reconciliação contra o gabarito Out/26 | Léo | SPEC-1-007 | CA-1-21 | TDD da SPEC-1-007, GREEN: versão oficial | CA-1-21; Q-21 perguntada | T6.3 | ✔ 02/11 | K |
| T7.2 | Painel de controles do ciclo | Léo | SPEC-1-007 | CA-1-22 | TDD da SPEC-1-007, GREEN: versão oficial | CA-1-22 | T7.1, T4.3 | ✔ 02/11 | L |
| T7.3 | Consulta drill-down com memória de cálculo | Léo | SPEC-1-007 | CA-1-23 | TDD da SPEC-1-007, GREEN: versão oficial | CA-1-23 | T6.4 | ✔ 02/11 | L |
| T7.4 | Exportação Cliente × SKU e consolidações | Léo | SPEC-1-007 | CA-1-24 | TDD da SPEC-1-007, GREEN: versão oficial | CA-1-24; Q-22 respondida | T6.4 | ✔ 02/11 | L |
| T7.5 | Demonstração de Out/26 ao Paulo e ao Léo e aceite da Fase 1 | Kim + Ângelo | SPEC-1-007 | CA-1-25 | TDD da SPEC-1-007, GREEN: versão oficial | CA-1-25 | T7.2, T7.3, T7.4 | ✔ 02/11 | M |

### Resumo por leva

| Leva | Tasks |
|---|---|
| — | T1.1 ✔ · T2.1 ✔ · T2.1b ✔ · T4.1 ✔ |
| A | T1.2 ✔ · T1.3 ☐ · T2.1c ✔ · T3.1 ✔ |
| B | T1.4 ✔ · T2.2 ✔ · T3.2 ✔ · T4.2 ✔ |
| C | T2.3 ✔ · T3.3 ✔ |
| D | T4.3 ✔ · T5.1 ☐ |
| E | T5.2 ✔ · T5.3 ✔ |
| F | T5.4 ✔ · T5.5 ✔ |
| G | T5.6 ✔ |
| H | T6.1 ✔ |
| I | T6.2 ✔ |
| J | T6.3 ✔ |
| K | T6.4 ✔ · T7.1 ✔ |
| L | T7.2 ✔ · T7.3 ✔ · T7.4 ✔ |
| M | T7.5 ✔ |

## Perguntas ao cliente desta fase

20 perguntas (Q-04..Q-22 e Q-39..Q-42) em `03_documentos/perguntas-ao-cliente.md`. Elas **não bloqueiam o início**: cada task pergunta quando precisa (protocolo em `AGENTS.md`).

## Fora desta fase

Aprovação/publicação, consulta pela equipe, cenários, acompanhamento, logística e IA.

## Histórico

- 30/10: teste do cliente passa a ser por SPEC (dois na fase: T1.3 e SPEC-1-007). As tasks de prova T1.4, T2.3, T4.3, T5.6 e T6.4 passam ao Léo, com prova automática.
- 20/10: EMENDA 02 — fase reescrita (dados reais, metodologia Out/26, Cliente × SKU). Tasks T1.1, T2.1, T2.1b e T4.1 aproveitadas; as demais tasks antigas foram canceladas ou absorvidas (ver matriz). As DÚVIDAS de 02/10 (T1.2, T6.2, blocos 9–10, origem OFICIAL) foram resolvidas pela emenda.
- 02/10: T2.1b concluída; T1.2 e T6.2 bloqueadas por dúvidas.
- 01/10: T4.1 concluída; banco restaurado após pausa do Supabase.
- 23/09: EMENDA 01 (superada).
- 16/09: T1.1 e T2.1 concluídas.
- 02/11: **Fase 1 aceita pelo cliente** (T7.5/CA-1-25). Matriz em 28/30 ✔; pendências T1.3 e T5.1 carregadas. Próxima: Fase 2, aguardando a liberação da consultora.
