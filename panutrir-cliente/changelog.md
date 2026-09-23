# Changelog

## 2026-09-14
- Escopo em cinco fases aprovado pela consultora e pelo CSM.
- Supabase definido como arquitetura oficial.
- Seis SPECs e dezoito tasks da Fase 1 geradas e revisadas.
- CSVs reais excluídos da Fase 1; fixtures sintéticas obrigatórias.
- Exportação canônica preparada para o Google Drive.

## 2026-09-16
- [Ângelo] · DEBUG task T1.1: teste humano bloqueado pela ausência de tela → tela autenticada `/permission-test` criada; causa raiz do papel sintético incorreto corrigida com associação explícita a `gestor_dados` → corrigido no Skip v0.0.8.
- [Ângelo] · Task T1.1 concluída: matriz papel×operação versionada em migrations (6 papéis × 7 operações = 42 decisões explícitas, 13 allow / 29 deny), RLS deny-by-default, auditoria append-only com correlation-id; QA do Skip v0.0.8 passou (setup, análise estática, build, integração, testes); teste humano aprovado na tela `/permission-test` — 6/6 resultados corretos e auditados (editar catálogo e fechar snapshot permitidos; criar ciclo, importar, homologar e exportar negados).
- [Ângelo] · Task T2.1 concluída: quatro contratos CSV sintéticos versionados em `contracts/` (vendas, metas_atingimentos, produtos, estrutura_comercial) com colunas, tipos, padrões, limites, encoding UTF-8 e delimitadores vírgula/ponto e vírgula; catálogo `catalogo-schemas.json` v1.0.0; 6 fixtures válidas (incl. reenvio idêntico e variante com ponto e vírgula) e 14 casos inválidos/limítrofes; relatório de casos com RED registrado; nenhum CSV real acessado; QA do Skip v0.0.10 passou (setup, análise estática, build, integração, testes); conteúdo aprovado pelo champion.

## 2026-09-23
- [Kim] · **EMENDA 01/2026 — Metodologia oficial de cálculo da meta** incorporada aos documentos (memória de cálculo do cliente, modelo fechado em ago/2026, 10 blocos). Efeitos: T2.1b criada na SPEC-1-002 (revisão de contratos CSV contra os campos exigidos pela metodologia); T6.2 e CA-1-07a na SPEC-1-006 (simulação passa a reproduzir a fórmula oficial com parâmetros versionados); RF-10 e RN-19 atualizados no PRD; nota da emenda no fase.md. Documento-fonte em `06_notas/2026-09-23-emenda-01-metodologia-meta.md`.