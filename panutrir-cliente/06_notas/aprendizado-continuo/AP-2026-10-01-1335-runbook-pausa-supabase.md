# AP-2026-10-01-1335 — Runbook de pausa e restauração do Supabase

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T4.1 / SPEC-1-004 (incidente operacional durante a verificação humana)
- Sinal: o projeto Supabase do plano gratuito pausa após ~1 semana de inatividade (status INACTIVE, timeouts de conexão). A restauração (restore_project) fica em COMING_UP por 5–15 minutos e o banco aceita conexão ANTES de terminar de restaurar — checagens imediatas pós-conexão podem indicar falsamente que o schema foi perdido (0 tabelas / 0 migrations), induzindo à reaplicação desnecessária de migrations.
- Evidência: restauração de 01/10/2026 — após reaplicar as 7 migrations do Skip, o histórico e os dados pré-pausa reapareceram (auditoria com os 9 eventos de teste humano da T1.1); verificação final: 12 tabelas com RLS, matriz 6×7 (42 decisões), 5 constraints EXCLUDE ativas, btree_gist no schema extensions, prova de sobreposição passando em transação revertida.
- Regra reutilizável: runbook pós-pausa — restore_project → aguardar COMING_UP terminar (5–15 min) → checar list_migrations/list_tables/contagens → só reaplicar as migrations do Skip se o schema realmente não voltar; migrations são idempotentes (IF NOT EXISTS / DROP IF EXISTS), então reaplicar não corrompe, mas o histórico pode ficar com versões duplicadas (mesmo nome em datas diferentes) — inofensivo.
- Quando aplicar: qualquer reativação do projeto Supabase deste projeto; considerar uso periódico ou upgrade de plano para evitar o ciclo.
- Quando não aplicar: projetos com plano pago (não pausam por inatividade) ou restauração de backup oficial.
- Confiança: alta — comportamento observado e confirmado em duas restaurações (28/09 e 01/10).
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
