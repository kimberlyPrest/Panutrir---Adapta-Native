# Matriz SPECs × Tasks — programa completo

**Fonte única de verdade** para ordem, dependências e status das tasks (EMENDA 02/2026). Se `fase.md`, `STATUS.md` ou uma SPEC divergirem desta matriz, vale a matriz; registre a divergência no changelog.

Legenda: ✔ concluída · ☐ a fazer · 🔒 bloqueada · ✖ cancelada. **Q** = pergunta ao cliente que a task faz e registra antes de implementar a parte dependente.

## Fase 1 — Motor de meta Cliente × SKU com dados reais (aberta)

| Leva | ID | Task | SPEC | Dono | Depende de | Q | Status |
|---|---|---|---|---|---|---|---|
| — | T1.1 | Matriz papel×operação em migrations | SPEC-1-001 | Engenharia | — | — | ✔ 16/09 |
| — | T2.1 | Contratos e fixtures sintéticas | SPEC-1-002 | Dados | — | — | ✔ 16/09 |
| — | T2.1b | Contratos × metodologia ago/26 | SPEC-1-002 | Dados | — | — | ✔ 02/10 |
| — | T4.1 | Modelo do catálogo (reaproveitado com vínculo vigente único) | SPEC-1-004 | Dados | — | — | ✔ 01/10 |
| A | T1.2 | Ciclo de meta (tabela/RPC), operações renomeadas, papéis reais | SPEC-1-001 | Léo | T1.1 | — | ☐ |
| A | T1.3 | Remover senha fixa da migration, trocar a senha, contas por convite | SPEC-1-001 | Léo | — | — | ☐ |
| A | T2.1c | Contrato `vendas` v2 contra as colunas reais; definir `venda_mensal` | SPEC-1-002 | Léo | T2.1b | — | ☐ |
| A | T3.1 | Parâmetros versionados + sortimento/substituição em tabela; versão Out/26 oficial | SPEC-1-003 | Léo | T2.1b | Q-10 | ☐ |
| B | T1.4 | Provar negações por papel e repetição do ciclo | SPEC-1-001 | Ângelo | T1.2, T1.3 | — | ☐ |
| B | T2.2 | Script de carga agregada mensal, idempotente, com registro | SPEC-1-002 | Léo | T2.1c | — | ☐ |
| B | T3.2 | Calendário: dias úteis e IS | SPEC-1-003 | Léo | T3.1 | Q-08, Q-09 | ☐ |
| B | T4.2 | Carregar DE→PARA atual e produtos (linha, Panettone) | SPEC-1-004 | Léo | T4.1, T2.1c | Q-04 | ☐ |
| C | T2.3 | Carregar Out/24–Set/26 reais e provar totais por mês | SPEC-1-002 | Ângelo | T2.2 | — | ☐ |
| C | T3.3 | Execução versionada e prova de reprodutibilidade | SPEC-1-003 | Léo | T3.1, T1.2 | — | ☐ |
| D | T4.3 | Auditoria de estrutura (gabarito: 27 clientes) | SPEC-1-004 | Ângelo | T4.2, T2.3 | Q-07 | ☐ |
| D | T5.1 | Universo elegível, exclusões e sortimento; fixture calculada à mão | SPEC-1-005 | Léo | T2.3, T3.1, T4.2 | Q-41 | ☐ |
| E | T5.2 | Motor 24M para maduros | SPEC-1-005 | Léo | T5.1, T3.2 | Q-12, Q-13, Q-15 | ☐ |
| E | T5.3 | Introdução e introdução com zero | SPEC-1-005 | Léo | T5.1 | Q-14 | ☐ |
| F | T5.4 | Piso técnico | SPEC-1-005 | Léo | T5.2 | Q-39 | ☐ |
| F | T5.5 | Substituição PlufiNut → Pão de Leite (Assaí SP) | SPEC-1-005 | Léo | T5.2, T5.3 | Q-16 | ☐ |
| G | T5.6 | Meta Original Ajustada, memória de cálculo e totais Out/26 | SPEC-1-005 | Ângelo | T5.4, T5.5, T3.3 | — | ☐ |
| H | T6.1 | GAP total e Indireto/Direto por responsável | SPEC-1-006 | Léo | T5.6 | Q-17, Q-20 | ☐ |
| I | T6.2 | Mix, convergência dos Especiais, GAP por linha | SPEC-1-006 | Léo | T6.1 | Q-18, Q-19, Q-42 | ☐ |
| J | T6.3 | Descida do GAP, Meta Final e promotor em branco | SPEC-1-006 | Léo | T6.2 | Q-40 | ☐ |
| K | T6.4 | Consolidações e prova de soma em todos os níveis | SPEC-1-006 | Ângelo | T6.3 | — | ☐ |
| K | T7.1 | Teste automatizado contra o gabarito Out/26 | SPEC-1-007 | Léo | T6.3 | Q-21 | ☐ |
| L | T7.2 | Painel de controles do ciclo | SPEC-1-007 | Léo | T7.1, T4.3 | — | ☐ |
| L | T7.3 | Consulta drill-down com memória de cálculo | SPEC-1-007 | Léo | T6.4 | — | ☐ |
| L | T7.4 | Exportação Cliente × SKU e consolidações | SPEC-1-007 | Léo | T6.4 | Q-22 | ☐ |
| M | T7.5 | Demonstração de Out/26 e aceite da Fase 1 | SPEC-1-007 | Kim + Ângelo | T7.2, T7.3, T7.4 | — | ☐ |

### Tasks canceladas pela EMENDA 02

| ID antigo | O que era | Para onde foi |
|---|---|---|
| T1.3 (antiga) | negações, sessão e recuperação | T1.4 |
| T2.2, T2.3 (antigas) | staging com SHA-256 e rollback | T2.2, T2.3 novas (carga agregada) |
| T3.1–T3.3 (antigas) | quarentena e exportação blindada | registro de carga (T2.2) e exportação sanitizada (T7.4) |
| T4.2, T4.3 (antigas) | resolução por vigência temporal | ✖ cancelada (M-04 usa a estrutura atual) |
| T5.1–T5.3 (antigas) | snapshot imutável | T3.3 (execução versionada) |
| T6.1–T6.3 (antigas) | painel e simulação sintética | SPEC-1-005..007 |

## Fase 2 — Ciclo mensal operável (planejada)

| ID | Task | SPEC | Depende de | Q | Status |
|---|---|---|---|---|---|
| F2-T1.1 | Avanço das janelas e herança de parâmetros | SPEC-2-001 | Fase 1 aceita | — | ☐ |
| F2-T1.2 | Carga recorrente do mês fechado | SPEC-2-001 | F2-T1.1 | — | ☐ |
| F2-T1.3 | Nov/26 em paralelo com o processo atual | SPEC-2-001 | F2-T1.2 | — | ☐ |
| F2-T2.1 | Tela de parâmetros versionados | SPEC-2-002 | Fase 1 aceita | — | ☐ |
| F2-T2.2 | Regras por rede (sortimento, substituição, exclusão) | SPEC-2-002 | F2-T2.1 | — | ☐ |
| F2-T3.1 | Execuções de simulação | SPEC-2-003 | F2-T2.1 | — | ☐ |
| F2-T3.2 | Comparação de cenários e promoção | SPEC-2-003 | F2-T3.1 | — | ☐ |
| F2-T4.1 | Aprovar/publicar com bloqueio e versões | SPEC-2-004 | F2-T1.1 | — | ☐ |
| F2-T4.2 | Consulta por perfil | SPEC-2-004 | F2-T4.1 | — | ☐ |
| F2-T4.3 | Entrega ao Metabase e medição de K2 (Dez/26) | SPEC-2-004 | F2-T4.1 | — | ☐ |

## Fase 3 — Acompanhamento e indicadores (planejada)

| ID | Task | SPEC | Depende de | Q | Status |
|---|---|---|---|---|---|
| F3-T1.1 | Carga recorrente do realizado | SPEC-3-001 | Fase 2 aceita | Q-30 | ☐ |
| F3-T1.2 | Painel realizado × meta × projeção | SPEC-3-001 | F3-T1.1 | — | ☐ |
| F3-T2.1 | Indicador de trocas | SPEC-3-002 | F3-T1.1 | — | ☐ |
| F3-T2.2 | Indicador de visitas | SPEC-3-002 | F3-T1.1 | Q-31 | ☐ |
| F3-T3.1 | Piso por promotor e concentração de REVISAR | SPEC-3-003 | Fase 2 aceita | — | ☐ |
| F3-T3.2 | Visão por Key Account | SPEC-3-003 | F3-T3.1 | — | ☐ |
| F3-T4.1 | Cadastro de campanha e venda incremental (opcional) | SPEC-3-004 | Fase 2 aceita | Q-33 | ☐ |
| F3-T4.2 | Meta incremental no ciclo e relatório pós-campanha (opcional) | SPEC-3-004 | F3-T4.1, F3-T1.2 | — | ☐ |

## Fase 4 — Módulo Logística (descoberta já em andamento)

| ID | Task | SPEC | Depende de | Q | Status |
|---|---|---|---|---|---|
| F4-T1.1 | Levantamento do processo atual por CD com Marcelo | SPEC-4-001 | reunião agendada | Q-34..Q-37 | ☐ |
| F4-T1.2 | Inventário de dados e baseline de K4/K5 | SPEC-4-001 | F4-T1.1 | — | ☐ |
| F4-T1.3 | Emenda das SPECs 4-002 e 4-003 | SPEC-4-001 | F4-T1.2 | — | ☐ |
| F4-T2.1 | CDs, áreas e localização de clientes | SPEC-4-002 | F4-T1.3 | — | ☐ |
| F4-T2.2 | Veículos, capacidades e frete | SPEC-4-002 | F4-T1.3 | — | ☐ |
| F4-T3.1 | Algoritmo de montagem de cargas | SPEC-4-003 | F4-T2.1, F4-T2.2 | — | ☐ |
| F4-T3.2 | Comparação com o plano manual (10 dias) | SPEC-4-003 | F4-T3.1 | — | ☐ |
| F4-T3.3 | Tela de proposta, aceite e ajuste | SPEC-4-003 | F4-T3.1 | — | ☐ |

## Fase 5 — Integração e IA assistiva (planejada)

| ID | Task | SPEC | Depende de | Q | Status |
|---|---|---|---|---|---|
| F5-T1.1 | Meta → volume por CD/semana | SPEC-5-001 | Fases 2 e 4 aceitas | — | ☐ |
| F5-T1.2 | Volume × capacidade e alertas | SPEC-5-001 | F5-T1.1 | — | ☐ |
| F5-T2.1 | IA explica a meta a partir da memória de cálculo | SPEC-5-002 | Fase 2 aceita | — | ☐ |
| F5-T2.2 | Sugestões com aceite humano auditado | SPEC-5-002 | F5-T2.1 | — | ☐ |
| F5-T3.1 | Medição final dos KPIs | SPEC-5-003 | F5-T1.2, F5-T2.2 | — | ☐ |
| F5-T3.2 | Runbooks e treinamento | SPEC-5-003 | F5-T3.1 | — | ☐ |
| F5-T3.3 | Portabilidade e encerramento | SPEC-5-003 | F5-T3.2 | — | ☐ |
