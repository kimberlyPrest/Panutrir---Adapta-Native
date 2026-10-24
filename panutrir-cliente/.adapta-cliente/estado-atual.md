# Estado atual — Adapta Cliente

- task_id: T3.1
- champion: Ângelo
- spec: 04_fase-atual/specs/SPEC-1-003.md
- etapa: aguardando_teste_humano
- autorizacao_implementacao: confirmada 2026-10-24T15:17-03:00 — mensagem do Alex: "pode"
- teste_humano: pendente
- verificacao_automatica: passou — CA-1-07 provado no banco: versão OUT-2026-v1 oficial com 16 parâmetros e seus valores conferidos um a um; UPDATE em P-07 recusado (23001); DELETE em P-02 recusado (23001); versão nova via `criar_versao_parametros` preserva a anterior intacta (v1 continua 0,02591659 e v2 fica 0,03); versão sem motivo recusada (23514); parâmetro inexistente recusado (23514); segunda versão oficial no mesmo mês recusada (23P01); `set role anon` vê 0 e sessão autenticada vê 16; 5 SKUs de sortimento e 1 substituição 81661→5 taxa 0,59 gravados.
- aprendizado: pendente
- ultima_acao: T3.1 implementada em 24/10/2026. Criadas as migrations `20261024150000_t31_parametros_versionados.sql` e `20261024150100_t31_seed_parametros_out2026.sql` (primeiras migrations versionadas em repositório deste projeto), o contrato `contracts/parametros_calculo.v2.0.0.json` e a suíte `contracts/testes_t31.py`. Um bug real foi encontrado pela própria prova (trigger travava o rascunho) e corrigido na migration `t31_corrige_imutabilidade_rascunho`.
- proxima_acao: aguardar o teste humano do Alex
- atualizado_em: 2026-10-24T15:35:00-03:00
- observacao: Q-10 e Q-20 continuam abertas e foram tratadas sem inventar regra — P-07 carregado como informado, P-16 vazio com `pendente_de='Q-20'`. A escrita usa `criar_configurar_ciclo` porque `editar_parametros` ainda não existe (nasce na T1.2, bloqueada); consequência registrada como DÚVIDA para a Kim: `gestor_dados` fica com leitura e sem escrita em parâmetros. A suíte `testes_t31.py` exige JWT de usuário autenticado e, sem ele, sai com código 2 e a mensagem do que falta — nunca em silêncio.
