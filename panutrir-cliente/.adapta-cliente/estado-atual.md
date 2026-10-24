# Estado atual — Adapta Cliente

- task_id: nenhuma (T2.1c concluída em 24/10/2026)
- champion: Ângelo
- spec: 04_fase-atual/specs/SPEC-1-002.md
- etapa: concluida
- autorizacao_implementacao: confirmada 2026-10-24T13:54-03:00 — mensagem do Alex: "Autorizo implementar a T2.1c"
- teste_humano: aprovado 2026-10-24T14:43-03:00 — mensagem do Alex: "Testei e funcionou — pode concluir a T2.1c"
- verificacao_automatica: passou — reverificação do zero no fechamento: 32/32 verificações da suíte RED/GREEN/REGRESSÃO; validador CLI funciona; nenhum segredo no diff; nenhum dado real de cliente nas fixtures; os três caminhos de erro respondem (coluna obrigatória faltando, arquivo inexistente, arquivo vazio) com código de saída 1; nenhum `except` vazio, `|| true` ou truncamento em zero; contrato v2.0.0 mapeia os três campos de M-02 e a venda bruta de M-05
- aprendizado: capturado:06_notas/aprendizado-continuo/AP-2026-10-24-1445-congeladas-tipo-esconde-troca.md e AP-2026-10-24-1446-estorno-negativo-legitimo.md
- ultima_acao: T2.1c concluída em 24/10/2026 após teste humano aprovado. Entregues `contracts/vendas.v2.0.0.json`, `contracts/venda_mensal.v1.0.0.json`, `contracts/validador_vendas.py`, `contracts/testes_t21c.py` e 2 fixtures sintéticas em `fixtures/t21c/`. Atualizados matriz, SPEC-1-002, STATUS.md (5 de 30 tasks, 16,7%) e changelog.
- proxima_acao: aguardar decisão do Alex sobre a próxima task — as elegíveis são T1.3 (senha exposta, aguardando aval para troca) e T3.1 (parâmetros Out/26, depende da Q-10, que é do Paulo)
- atualizado_em: 2026-10-24T14:48:00-03:00
- observacao: T1.2 permanece bloqueada aguardando a Kim (`06_notas/2026-10-22-duvidas-t12-para-kim.md`). Dúvida aberta e não bloqueante da T2.1c: o G-11 (29.003 combinações) não é reproduzido por M-05 literal em Jul–Set/26 (dá 29.752; diferença de 749 = G-16) — pertence à T5.1.
