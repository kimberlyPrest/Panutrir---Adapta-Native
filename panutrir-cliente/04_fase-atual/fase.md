# Fase 1 — Tasks

> Projeto: Panutrir — Sistema de Metas Comerciais
> Contrato documental v0.9.3 + EMENDA 01/2026 (23/09)

## Tasks

| ID | Task | SPEC | Leva | Status |
|----|------|------|------|--------|
| T1.1 | Bootstrap Supabase + RLS + papéis | SPEC-1-001 | A | ✔ concluída (QA v0.0.8, teste humano 6/6) |
| T1.2 | Implementar criação do ciclo-piloto protegida por RLS | SPEC-1-001 | B | 🔒 bloqueada na análise — confirmar regras do ciclo, ambiente e contas sintéticas; ver DÚVIDA no changelog |
| T2.1 | Importação de bases + catálogo | SPEC-1-002 | B | ✔ concluída (QA v0.0.10, teste humano 6/6) |
| T2.1b | **Revisão de contratos com a metodologia oficial (EMENDA 01/2026)** | SPEC-1-002 | B | ✔ concluída (QA v0.0.13, teste humano aprovado 02/10; DÚVIDA de rastreabilidade em changelog) |
| T4.1 | Cálculo de potencial | SPEC-1-004 | D | ✔ concluída (QA v0.0.12, teste humano aprovado 01/10) |
| T6.2 | Distribuição de metas com fórmula oficial | SPEC-1-006 | F | 🔒 bloqueada — divergência de dependências, metodologia e responsável (ver DÚVIDA no changelog) |
| T6.x | Demais tasks da leva F | SPEC-1-006 | F | ⏸ pendentes — elegibilidade depende da reconciliação da matriz e da sequência |

## Bloqueios

- **T1.2 — análise 02/10/2026:** T1.1 está concluída no `fase.md`, portanto a pré-condição técnica principal está atendida; porém, `matriz-specs-fases.md` ainda marca T1.1 como ☐. O Supabase disponível está ACTIVE_HEALTHY, mas é o único projeto listado e não há branches de desenvolvimento; o app Skip está publicado e mantém `.skip.config.json` como alteração pendente. No banco consultado há uma atribuição sintética ativa (`gestor_dados`), nenhuma conta atribuída a `operador` ou `consulta` e nenhuma tabela de ciclos. Antes de implementar, confirmar com Kim os campos do ciclo e a regra para repetição/duplicidade; confirmar com o cliente/infra qual ambiente pode receber migration e como provisionar as contas sintéticas sem credenciais fixas no repositório. A análise não alterou código, configuração, banco ou publicação.
- **DÚVIDA — Kim (02/10/2026):** `fase.md`/`STATUS.md` indicavam T6.2 elegível após T2.1b, enquanto `matriz-specs-fases.md` lista T6.1 e T5.2 como pré-condições; ambas dependem de tasks anteriores ainda não marcadas como concluídas. SPEC-1-006 lista apenas T2.1b como dependência. Consultora deve confirmar a fonte de verdade, a ordem, o estado das tasks e a atribuição individual; não iniciar T6.2 antes.
- **Metodologia:** a nota disponível só detalha os blocos 1–8 e remete os blocos 9–10 a `Metodologia_1_.xlsx`, que não está na documentação operacional disponível. Completar/confirmar a fórmula oficial e valores esperados antes de implementar/reconciliar.
- **Contrato de parâmetros (T2.1b):** `parametros_calculo.json` permite `origem=OFICIAL`, mas uma fixture classifica origem oficial pré-Gates como inválida sem regra de contrato que imponha essa condição. Consultora deve confirmar se é uma regra condicionada aos Gates G1–G3 ou se a fixture deve ser tratada de outra forma; ver changelog.
- CSV histórico do cliente continua sujeito aos Gates G1–G3; nenhum CSV real deve ser usado nesta fase.

## Histórico

- 02/10: T1.2 analisada a pedido de Alex; fluxo previsto: criação do ciclo em preparação somente para papel autorizado, negação auditada para papel sem permissão e prova da barreira no banco. Análise bloqueada antes de autorização/implementação por falta de definição dos campos/duplicidade, ambiente Supabase de desenvolvimento e contas sintéticas operador/consulta; evidências e DÚVIDA registradas no changelog.
- 02/10: T2.1b concluída — contratos revisados contra a metodologia oficial de cálculo da meta: vendas v1.1.0 (venda líquida + canal direto/indireto), produtos v1.1.0 (linha Branco/Especial), novo contrato `parametros_calculo` v1.0.0 (parâmetros versionados, valores sintéticos), catálogo v1.1.0 com rastreabilidade bloco a bloco; QA v0.0.13; leva F inicialmente indicada como liberada, depois bloqueada para seleção por divergências documentais registradas acima.
- 02/10: análise da candidata T6.2 interrompida antes de plano/autorização; nenhuma alteração de produto foi feita.
- 01/10: T4.1 concluída — modelo temporal do catálogo canônico (6 tabelas com RLS, 5 constraints EXCLUDE anti-sobreposição, pendências de resolução); QA v0.0.12; banco restaurado após pausa do Supabase e revalidado.
- 23/09: EMENDA 01/2026 aplicada — TASK-2.1b aberta; T6.2 passa a usar a fórmula oficial da memória de cálculo ago/2026.
- 17/09: T4.1 movida para verificação humana.
- 16/09: T1.1 e T2.1 concluídas com teste humano 6/6.
