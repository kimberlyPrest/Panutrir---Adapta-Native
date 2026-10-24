# Estado atual — Adapta Cliente

- task_id: T2.2
- champion: Ângelo
- spec: 04_fase-atual/specs/SPEC-1-002.md
- etapa: aguardando_teste_humano
- autorizacao_implementacao: confirmada 2026-10-24T18:06-03:00 — mensagem do Alex: "Sim"
- teste_humano: pendente
- verificacao_automatica: passou — 15 verificações da suíte T2.2 em Postgres 18.4 local, mais provas manuais: (1) 2 cargas seguidas → 5 linhas, 0 duplicatas, 2 registros; (2) recarga de agosto não altera julho (4 linhas / R$ 1.645,50 intactos); (3) falha no meio da transação reverte tudo; (4) conexão inválida não deixa registro preso em `em_andamento`; (5) linhas inválidas contadas por motivo com exemplos listados; (6) venda_liquida negativa preservada (troca 150 > venda 100 → -50,00); (7) volume real de 2026: 82.601 combinações em 3 meses, diferença 0,00 contra a fonte. Suítes T2.1c (32 verificações) e T3.1 seguem passando. Migration aplicada no Supabase.
- aprendizado: pendente
- ultima_acao: T2.2 implementada em 24/10/2026. Criados `supabase/migrations/20261024180000_t22_venda_mensal_e_carga.sql`, `contracts/carga_vendas.py` e `contracts/testes_t22.py`. Achado que mudou o código: o BI exporta valores com lixo de ponto flutuante (15.899999999999999 em vez de 15,90), o que gerava divergência de centavos por mês; corrigido com arredondamento a 2 casas na leitura.
- proxima_acao: aguardar o teste humano do Alex
- atualizado_em: 2026-10-24T18:40:00-03:00
- observacao: a T2.2 foi provada contra um Postgres local, não contra o Supabase — o ambiente não tem a senha do banco. O que está provado é a lógica de transação e idempotência; o desempenho com as 888.756 linhas reais no Supabase do plano gratuito só a T2.3 (Ângelo) vai revelar. A carga exige `DATABASE_URL`; sem ela o script explica e sai com código 2, nunca em silêncio.
