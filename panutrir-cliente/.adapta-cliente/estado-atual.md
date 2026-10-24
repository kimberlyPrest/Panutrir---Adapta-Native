# Estado atual — Adapta Cliente

- task_id: T3.1
- champion: Ângelo
- spec: 04_fase-atual/specs/SPEC-1-003.md
- etapa: concluida
- autorizacao_implementacao: confirmada 2026-10-24T15:17-03:00 — mensagem do Alex: "pode"
- teste_humano: aprovado 2026-10-24T17:05-03:00 — mensagem do Alex: "Aprovadp"
- verificacao_automatica: passou — reverificação do zero na conclusão: 1 versão oficial (OUT-2026-v1) com 16 parâmetros e valores conferidos (P-02 13.000.000,00; P-05 1,0319; P-06 22; P-07 0,02591659; P-12 0,055; P-14 300,00); UPDATE em P-07 recusado (23001); DELETE em P-02 recusado (23001); criar versão nova mudando P-07 preserva a oficial e gera rascunho com 16 parâmetros + 5 SKUs + 1 substituição clonados; versão de teste removida e restou apenas a oficial; `set role anon` vê 0; nenhum segredo no diff; nenhum dado real de cliente nos artefatos.
- aprendizado: capturado:06_notas/aprendizado-continuo/AP-2026-10-24-1706-versao-imutavel-trigger-rascunho.md e AP-2026-10-24-1707-resposta-cliente-corrige-leitura-provavel.md
- ultima_acao: T3.1 concluída em 24/10/2026 após teste humano aprovado e Q-10 respondida ("Calculado"). Atualizados matriz, SPEC-1-003 (resposta da Q-10), STATUS (6 de 30 = 20%), changelog e o registro central de perguntas.
- proxima_acao: aguardar decisão do Alex sobre a próxima task — elegíveis: T1.3 (senha exposta, aguardando aval para troca) e T2.2 (carga agregada, depende só da T2.1c concluída)
- atualizado_em: 2026-10-24T17:10:00-03:00
- observacao: a resposta da Q-10 ("G é calculado") NÃO altera a T3.1 — o valor 0,02591659 continua sendo o G oficial de Out/26 e a tabela guarda o valor da versão; quem calcula é o motor (T5.x). Mas abriu uma DÚVIDA real para a Kim: a fórmula de cálculo do G (40% histórico + 60% recente) existe apenas no modelo de ago/26, que a EMENDA 02 superou; o M-11 de Out/26 só fixa o valor e não define como obtê-lo. Sem essa definição, a T5.2 não consegue calcular G para Nov/26 em diante.
