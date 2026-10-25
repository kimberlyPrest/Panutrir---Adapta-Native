# STATUS

- **Programa:** reiniciado pela EMENDA 02/2026 (20/10/2026). Prazo de 4 meses a partir de 06/10 → até 06/02/2027.
- **Escopo:** Intranet Panutrir — Metas (Fases 1–3), Logística (Fase 4), integração e IA (Fase 5). Escopo revisado aguardando aceite de Paulo e Matheus.
- **Fase ativa:** 1 — Motor de meta Cliente × SKU com dados reais (20/10 – 14/11, indicativo).
- **Fonte do cálculo:** metodologia Out/26 (`06_notas/2026-10-20-metodologia-oficial-out-2026.md`). A EMENDA 01 foi superada.
- **SPECs:** Fase 1 com 7 aprovadas; Fases 2–5 com 14 planejadas em `03_documentos/specs-programa/`.
- **Tasks da Fase 1:** 30, sendo 7 concluídas (T1.1, T2.1, T2.1b, T4.1, T2.1c, T3.1, **T2.2**) e 23 a fazer, em 13 levas (A–M) — 23% da fase.
- **Próxima leva (B/C):** T2.3 pronta para o Ângelo · T3.2 (depende de Q-08/Q-09) · T4.2 (depende de Q-04). T1.2 bloqueada pela Kim.
- **Perguntas ao cliente:** 27, sendo 1 respondida (Q-10) e 26 abertas (19 na Fase 1). Só entram perguntas que mudam a implementação; não bloqueiam o início, e cada task pergunta quando precisa.
- **Bloqueios anteriores (T1.2, T6.2):** resolvidos pela EMENDA 02. A T1.2 voltou a ficar bloqueada em 22/10 por três DÚVIDAS de escopo para a Kim.
- **Dados:** reais permitidos no Supabase do projeto. Nunca em repositório.
- **Repositórios:** documentação/método = `kimberlyPrest/Panutrir---Adapta-Native` (este); **código executável = `paulorobertoferreira-pan/login-panutrir-ucjxoqmba`** — desde 25/10 as migrations de negócio (T3.1/T2.2), contracts e fixtures vivem lá (PR #1 aguardando revisão/merge do Alex). Restauração do zero voltou a ser possível a partir do repo do app.
- **Alertas:** (1) os repositórios de contexto e de código estão **públicos** no GitHub; (2) a migration do repositório de código tem senha fixa de um usuário real e essa senha **ainda funciona** (T1.3, aguardando autorização da troca).
- **Logística:** descoberta (SPEC-4-001) começa em paralelo; reunião com Marcelo Néquio a agendar por Matheus.
