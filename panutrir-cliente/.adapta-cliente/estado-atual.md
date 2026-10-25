# Estado atual — Adapta Cliente

- task_id: T2.2
- champion: Ângelo
- spec: 04_fase-atual/specs/SPEC-1-002.md
- etapa: concluida
- autorizacao_implementacao: confirmada 2026-10-24T18:06-03:00 — mensagem do Alex: "Sim"
- teste_humano: aprovado por Alex em 25/10/2026 — "ele ja foi feito e passou"
- verificacao_automatica: passou — 15 verificações da suíte T2.2 em Postgres 18.4 local, mais provas manuais: (1) 2 cargas seguidas → 5 linhas, 0 duplicatas, 2 registros; (2) recarga de agosto não altera julho (4 linhas / R$ 1.645,50 intactos); (3) falha no meio da transação reverte tudo; (4) conexão inválida não deixa registro preso em `em_andamento`; (5) linhas inválidas contadas por motivo com exemplos listados; (6) venda_liquida negativa preservada (troca 150 > venda 100 → -50,00); (7) volume real de 2026: 82.601 combinações em 3 meses, diferença 0,00 contra a fonte. Suítes T2.1c (32 verificações) e T3.1 seguem passando. Migration aplicada no Supabase.
- aprendizado: aprendido — (1) O BI exporta valores monetários com lixo de ponto flutuante (até 15 casas: 15.899999999999999 em vez de 15,90); arredondar a 2 casas NA LEITURA é obrigatório, senão a soma acumula centavos por mês e nenhuma conferência de tolerância R$ 0,01 fecha. (2) Prova de transação precisa ser feita com falha simulada DENTRO da transação — foi o que mostrou que não sobra mês parcial. (3) Um teste que passa sempre não é teste: a primeira versão da prova de "venda_liquida negativa" usava `True` como resultado e passaria mesmo com zero linhas; reescrita para gravar troca > venda e conferir -50,00.
- ultima_acao: T2.2 concluída em 25/10/2026. Entregues e publicados: `supabase/migrations/20261024180000_t22_venda_mensal_e_carga.sql`, `contracts/carga_vendas.py` e `contracts/testes_t22.py`. Fase 1 em 7/30 (23%).
- proxima_acao: T2.3 (carregar Out/24–Set/26 reais e provar os totais por mês) — dono Ângelo. Alternativas sem bloqueio: T3.2 (perguntas Q-08/Q-09) e T4.2 (Q-04).
- atualizado_em: 2026-10-25T02:20:00-03:00
- observacao: a T2.2 foi provada contra um Postgres 18.4 local, não contra o Supabase — o ambiente não tem a senha do banco. Está provada a lógica de transação e idempotência; o desempenho com as 888.756 linhas reais no Supabase do plano gratuito só a T2.3 (Ângelo) vai revelar. A carga exige `DATABASE_URL`; sem ela o script explica e sai com código 2, nunca em silêncio. PENDÊNCIA SEPARADA: os artefatos de código (migrations e contracts) vivem no repositório de documentação, e o repositório de código (`login-panutrir-ucjxoqmba`) não recebe commit desde 15/09 — a decisão de onde o código deve morar está aberta com o Alex.
