# Estado atual — Adapta Cliente

- task_id: T1.2
- champion: Ângelo
- spec: 04_fase-atual/specs/SPEC-1-001.md
- etapa: bloqueada
- autorizacao_implementacao: ausente
- teste_humano: pendente
- verificacao_automatica: pendente
- aprendizado: pendente
- ultima_acao: análise da T1.2 concluída em 22/10/2026 e três DÚVIDAS de escopo registradas para a Kim em `06_notas/2026-10-22-duvidas-t12-para-kim.md` (com opções e leitura provável): (1) mapeamento das 7 operações antigas → 7 novas não é 1:1 — `gerenciar_papeis` some sem sucessor e sustenta 11 políticas de RLS, `fechar_snapshot` refere o snapshot cancelado pela EMENDA 02, `homologar` não tem par; 27 das 37 políticas referenciam operação antiga. (2) papel `aprovador` não existe (papéis: administrador, auditor, consulta, gestor_dados, operador, revisor) e só há a conta paulo.ferreira@panutrir.com.br com `gestor_dados`; Léo e Ângelo não têm conta, e CA-1-01 exige os três. (3) `ciclo_meta.parametros_versao_id` depende de `parametros_versao`, criada só na T3.1, sem dependência na matriz. Achado extra: migrations da T1.1/T4.1 não estão em nenhum repositório (o repo público tem só a de auth; o banco tem 21 versões) — restauração do zero não é reproduzível a partir do Git. Banco restaurado de INACTIVE para ACTIVE_HEALTHY e inspecionado em leitura; nenhuma alteração de schema, código ou dado.
- proxima_acao: aguardar a decisão da Kim sobre as três DÚVIDAS antes de qualquer código
- atualizado_em: 2026-10-22T20:42:00-03:00
