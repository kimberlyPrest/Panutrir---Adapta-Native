> **Arquivo — matriz da Fase 1 em 04/11/2026.** Documento histórico: a fonte única vigente de ordem e
> status é `04_fase-atual/matriz-specs-fases.md` (Fase 2). O status da Fase 1 aqui registra o aceite de
> 02/11/2026 com **T1.3 e T5.1 ainda abertas**.

# Matriz SPECs × Tasks — programa completo

**Fonte única de verdade** para ordem, dependências e status das tasks (EMENDA 02/2026). Se `fase.md`, `STATUS.md` ou uma SPEC divergirem desta matriz, vale a matriz; registre a divergência no changelog.

Legenda: ✔ concluída · ☐ a fazer · 🔒 bloqueada · ⏳ no ar, aguardando o teste do cliente da SPEC · ✖ cancelada. **Q** = pergunta ao cliente que a task faz e registra antes de implementar a parte dependente.

**Teste do cliente:** por SPEC, não por task (desde 30/10). Na Fase 1, só na SPEC-1-001 (T1.3, login) e na SPEC-1-007 (T7.5, aceite); as outras SPECs fecham pela prova automática. Regra em `AGENTS.md`.

## Fase 1 — Motor de meta Cliente × SKU com dados reais (aberta)

| Leva | ID | Task | SPEC | Dono | Depende de | Q | Status |
|---|---|---|---|---|---|---|---|
| — | T1.1 | Matriz papel×operação em migrations | SPEC-1-001 | Engenharia | — | — | ✔ 16/09 |
| — | T2.1 | Contratos e fixtures sintéticas | SPEC-1-002 | Dados | — | — | ✔ 16/09 |
| — | T2.1b | Contratos × metodologia ago/26 | SPEC-1-002 | Dados | — | — | ✔ 02/10 |
| — | T4.1 | Modelo do catálogo (reaproveitado com vínculo vigente único) | SPEC-1-004 | Dados | — | — | ✔ 01/10 |
| A | T1.2 | Ciclo de meta (tabela/RPC), operações renomeadas, papéis reais | SPEC-1-001 | Léo | T1.1 | — | ✔ 30/10 |
| A | T1.3 | Remover senha fixa da migration, trocar a senha, contas por convite | SPEC-1-001 | Léo | — | — | ☐ |
| A | T2.1c | Contrato `vendas` v2 contra as colunas reais; definir `venda_mensal` | SPEC-1-002 | Léo | T2.1b | — | ✔ 24/10 |
| A | T3.1 | Parâmetros versionados + sortimento/substituição em tabela; versão Out/26 oficial | SPEC-1-003 | Léo | T2.1b | Q-10 | ✔ 24/10 |
| B | T1.4 | Provar negações por papel e repetição do ciclo | SPEC-1-001 | Léo | T1.2, T1.3 | — | ✔ 02/11 |
| B | T2.2 | Script de carga agregada mensal, idempotente, com registro | SPEC-1-002 | Léo | T2.1c | — | ✔ 25/10 |
| B | T3.2 | Calendário: dias úteis e IS | SPEC-1-003 | Léo | T3.1 | Q-08, Q-09 | ✔ 30/10 |
| B | T4.2 | Carregar DE→PARA atual e produtos (linha, Panettone) | SPEC-1-004 | Léo | T4.1, T2.1c | Q-04 | ✔ 30/10 |
| C | T2.3 | Carregar Out/24–Set/26 reais e provar totais por mês | SPEC-1-002 | Léo | T2.2 | — | ✔ 31/10 |
| C | T3.3 | Execução versionada e prova de reprodutibilidade | SPEC-1-003 | Léo | T3.1, T1.2 | — | ✔ 30/10 |
| D | T4.3 | Auditoria de estrutura (gabarito: 27 clientes) | SPEC-1-004 | Léo | T4.2, T2.3 | Q-07 | ✔ 31/10 |
| D | T5.1 | Universo elegível, exclusões e sortimento; fixture calculada à mão | SPEC-1-005 | Léo | T2.3, T3.1, T4.2 | Q-41 | ☐ |
| E | T5.2 | Motor 24M para maduros | SPEC-1-005 | Léo | T5.1, T3.2 | Q-12, Q-13, Q-15, **Q-10b** | ✔ 02/11 |
| E | T5.3 | Introdução e introdução com zero | SPEC-1-005 | Léo | T5.1 | Q-14 | ✔ 02/11 |
| F | T5.4 | Piso técnico | SPEC-1-005 | Léo | T5.2 | Q-39 | ✔ 02/11 |
| F | T5.5 | Substituição PlufiNut → Pão de Leite (Assaí SP) | SPEC-1-005 | Léo | T5.2, T5.3 | Q-16 | ✔ 02/11 |
| G | T5.6 | Meta Original Ajustada, memória de cálculo e totais Out/26 | SPEC-1-005 | Léo | T5.4, T5.5, T3.3 | — | ✔ 02/11 |
| H | T6.1 | GAP total e Indireto/Direto por responsável | SPEC-1-006 | Léo | T5.6 | Q-17, Q-20 | ✔ 02/11 |
| I | T6.2 | Mix, convergência dos Especiais, GAP por linha | SPEC-1-006 | Léo | T6.1 | Q-18, Q-19, Q-42 | ✔ 02/11 |
| J | T6.3 | Descida do GAP, Meta Final e promotor em branco | SPEC-1-006 | Léo | T6.2 | Q-40 | ✔ 02/11 |
| K | T6.4 | Consolidações e prova de soma em todos os níveis | SPEC-1-006 | Léo | T6.3 | — | ✔ 02/11 |
| K | T7.1 | Teste automatizado contra o gabarito Out/26 | SPEC-1-007 | Léo | T6.3 | Q-21 | ✔ 02/11 |
| L | T7.2 | Painel de controles do ciclo | SPEC-1-007 | Léo | T7.1, T4.3 | — | ✔ 02/11 |
| L | T7.3 | Consulta drill-down com memória de cálculo | SPEC-1-007 | Léo | T6.4 | — | ✔ 02/11 |
| L | T7.4 | Exportação Cliente × SKU e consolidações | SPEC-1-007 | Léo | T6.4 | Q-22 | ✔ 02/11 |
| M | T7.5 | Demonstração de Out/26 e aceite da Fase 1 | SPEC-1-007 | Kim + Ângelo | T7.2, T7.3, T7.4 | — | ✔ 02/11 |

### Tasks canceladas pela EMENDA 02

| ID antigo | O que era | Para onde foi |
|---|---|---|
| T1.3 (antiga) | negações, sessão e recuperação | T1.4 |
| T2.2, T2.3 (antigas) | staging com SHA-256 e rollback | T2.2, T2.3 novas (carga agregada) |
| T3.1–T3.3 (antigas) | quarentena e exportação blindada | registro de carga (T2.2) e exportação sanitizada (T7.4) |
| T4.2, T4.3 (antigas) | resolução por vigência temporal | ✖ cancelada (M-04 usa a estrutura atual) |
| T5.1–T5.3 (antigas) | snapshot imutável | T3.3 (execução versionada) |
| T6.1–T6.3 (antigas) | painel e simulação sintética | SPEC-1-005..007 |

## Fase 2 — Ciclo mensal operável (retrato de 04/11/2026 — a fonte vigente é `04_fase-atual/matriz-specs-fases.md`; execução não liberada)

Plano, critérios e evidências: a Fase 2 passou a viver em `04_fase-atual/` (caminho relativo à raiz da pasta do cliente) na reorganização de 04/11/2026. As linhas acima são o retrato de como estavam nesta data.

| Task | Descrição | SPEC | Dono | Dependências | Status | Leva |
|---|---|---|---|---|---|---|
| T2.1.1 | Derivar as janelas do ciclo do mês de referência (elegibilidade T−3, motor T−24, mix T−6 e idade do SKU em meses) e gravá-las no registro do ciclo | SPEC-2-001 | Léo | Fase 1 aceita (02/11/2026) | ☐ | A |
| T2.2.1 | Entregar a tela de parâmetros versionados (P-01..P-18) com criação de versão e autor e motivo obrigatórios, aceitando valor PENDENTE explícito | SPEC-2-002 | Léo | Fase 1 aceita (02/11/2026) | ☐ | A |
| T2.4.1 | Apurar a reconciliação por modo (VALIDAÇÃO DA REGRA e EXECUÇÃO) e exigir, em cada divergência, causa declarada, dono e referência da pendência que a resolve | SPEC-2-004 | Léo | Fase 1 aceita (02/11/2026) | ☐ | A |
| T2.5.1 | Criar os papéis de consulta e o vínculo usuário→carteira por papel (supervisor, promotor, diretoria), sem inferir vínculo por código ambíguo entre papéis | SPEC-2-005 | Léo | Fase 1 aceita (02/11/2026) | ☐ | A |
| T2.6.1 | Extrair a meta publicada numa consulta de saída com o layout lido de parâmetro (P-18), recusando layout fixo no código | SPEC-2-006 | Léo | Fase 1 aceita (02/11/2026) | ☐ | A |
| T2.1.2 | Herdar a versão de parâmetros do ciclo anterior gravando Meta Diretoria, IS, dias úteis e G como requer_confirmação e forçar não reconciliada a execução que usar parâmetro não confirmado | SPEC-2-001 | Léo | T2.1.1 | ☐ | B |
| T2.1.3 | Construir a rotina operacional de carga mensal sem SQL, com registro e idempotência por mês; entregar fluxo para operação do Ângelo | SPEC-2-001 | Léo | Fase 1 aceita (02/11/2026) | ☐ | B |
| T2.1.4 | Provar que o ciclo 2026-10 aceito continua idêntico depois da derivação das janelas, comparando insumos e totais por regime | SPEC-2-001 | Léo | T2.1.1 | ☐ | B |
| T2.2.2 | Mostrar o diff campo a campo entre duas versões de parâmetros e quais execuções usaram cada versão | SPEC-2-002 | Léo | T2.2.1 | ☐ | B |
| T2.2.3 | Dar vigência por ciclo às regras por rede (sortimento restrito, substituição e exclusões) e recusar vigência retroativa | SPEC-2-002 | Léo | Fase 1 aceita (02/11/2026) | ☐ | B |
| T2.3.1 | Criar execução de cenário a partir de versão derivada marcada simulacao, sem tocar a execução oficial | SPEC-2-003 | Léo | Fase 1 aceita (02/11/2026) | ☐ | B |
| T2.4.2 | Executar aprovar e publicar com trilha append-only (ator, operação, alvo, motivo, timestamp UTC) e recusa auditada | SPEC-2-004 | Léo | T2.4.1 | ☐ | B |
| T2.5.2 | Entregar a consulta por perfil: supervisor vê a própria equipe, promotor a própria carteira e Diretoria a empresa | SPEC-2-005 | Léo | T2.5.1 | ☐ | B |
| T2.6.2 | Refrescar a meta publicada para o Metabase de forma idempotente e conferir no destino o total publicado | SPEC-2-006 | Léo | T2.6.1; Q-22 respondida; acesso e autorização do destino Metabase verificados | 🔒 | B |
| T2.2.4 | Bloquear criação de versão em ciclo aprovado ou publicado e recusar oficializar versão com parâmetro pendente, auditando as duas negativas | SPEC-2-002 | Léo | T2.2.1 | ☐ | C |
| T2.3.2 | Aplicar o limite de cenários por ciclo (P-17) com recusa auditada ao exceder e alerta registrado enquanto o valor estiver pendente | SPEC-2-003 | Léo | T2.3.1 | ☐ | C |
| T2.3.3 | Comparar dois cenários por canal, supervisor e linha, com diferença absoluta e percentual, somas fechando e o parâmetro causador identificado | SPEC-2-003 | Léo | T2.3.1 | ☐ | C |
| T2.4.3 | Congelar a publicação e obrigar a correção por nova execução publicada como versão 2 com motivo, preservando a versão 1 consultável | SPEC-2-004 | Léo | T2.4.2 | ☐ | C |
| T2.5.3 | Aplicar RLS por carteira nas tabelas de resultado e provar a negativa em três frentes: consulta pela interface, RPC e acesso direto à tabela | SPEC-2-005 | Léo | T2.5.1; T2.5.2 | ☐ | C |
| T2.5.4 | Fazer a consulta exibir somente a meta publicada, com o ciclo declarado e a memória de cálculo disponível | SPEC-2-005 | Léo | T2.4.2; T2.5.2 | ☐ | C |
| T2.6.3 | Restringir o extrato à meta publicada, incluir o campo de perfil necessário à permissão no destino e registrar a responsabilidade do cliente pela configuração do Metabase | SPEC-2-006 | Léo | T2.6.2 | ☐ | C |
| T2.1.5 | Rodar Nov/26 pelo sistema e pelo processo atual do Paulo e reconciliar as diferenças uma a uma até o aceite | SPEC-2-001 | Ângelo | T2.1.2; T2.1.3; T2.4.2; D1, D2, D3 e Q-42 respondidas | 🔒 | D |
| T2.3.4 | Promover um cenário a candidato oficial registrando autor, motivo e versão derivada, sem publicar | SPEC-2-003 | Léo | T2.3.3 | ☐ | D |
| T2.4.4 | Registrar os quatro marcos do ciclo (mês fechado carregado, execução, aprovação e publicação) com timestamp UTC e calcular o prazo do K2 | SPEC-2-004 | Léo | T2.4.2 | ☐ | D |
| T2.4.5 | Recusar ajuste manual do número final em qualquer nível e exigir que a exceção entre por regra ou por parâmetro versionado | SPEC-2-004 | Léo | T2.4.2 | ☐ | D |
| T2.4.6 | Publicar o ciclo Dez/26 antes do primeiro dia de dezembro e medir o prazo do K2 no ciclo real | SPEC-2-004 | Ângelo | T2.1.5; T2.4.4; T2.4.5; T2.6.2; T2.5.4 | ☐ | E |
| T2.5.5 | Provar o isolamento real com contas convidadas (2 supervisores, 2 promotores e diretoria) e nenhuma credencial exposta em tela, front, migration ou endpoint | SPEC-2-005 | Léo | T2.5.3; Gate G-SEG satisfeito; Convites e privatização dos repositórios concluídos pelo cliente | 🔒 | E |

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
