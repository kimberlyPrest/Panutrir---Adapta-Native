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
