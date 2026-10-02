# STATUS

- **Escopo:** aprovado pela consultora e pelo CSM em 14/09/2026.
- **Arquitetura:** Supabase.
- **Fase ativa:** Fase 1 — Base confiável e primeira simulação.
- **SPECs:** 6 aprovadas.
- **Tasks:** 19 em 7 levas — 4 concluídas (T1.1, T2.1, T2.1b e T4.1); T1.2 está bloqueada após análise; T6.2 continua bloqueada por divergências de sequência e metodologia.
- **T1.2 / SPEC-1-001:** T1.1 confirmada concluída em `fase.md` (embora a matriz de rastreabilidade ainda esteja desatualizada). Leitura do banco: 6 papéis, 7 operações, 42 decisões; somente uma atribuição ativa de papel, `gestor_dados`; nenhuma tabela de ciclos. O Supabase tem um único projeto listado e nenhuma branch de desenvolvimento. Antes de implementar, Kim deve confirmar campos do ciclo e semântica de repetição/duplicidade; cliente/infra deve confirmar ambiente seguro e provisionamento de contas sintéticas `operador` e `consulta`.
- **Emenda ativa:** EMENDA 01/2026 (metodologia oficial de cálculo da meta, memória de cálculo ago/2026) — T2.1b concluída em 02/10/2026; T6.2 requer definição completa, ordem de dependências e provas esperadas antes de prosseguir; CA-1-07a continua bloqueante.
- **Dados:** somente fixtures sintéticas na Fase 1; CSVs reais não foram usados.
- **Skip:** versão 0.0.14 (hash 4cb3d8b) criada por engano ao acionar QA durante consulta; a ferramenta reportou setup, análise estática, build, integrações e testes sem erros. Não houve chamada de publicação. O projeto está marcado como publicado; `.skip.config.json` permanece como alteração pendente.
- **Primeira leva:** T1.1 ✔ · T2.1 ✔ · T2.1b ✔ · T4.1 ✔.
