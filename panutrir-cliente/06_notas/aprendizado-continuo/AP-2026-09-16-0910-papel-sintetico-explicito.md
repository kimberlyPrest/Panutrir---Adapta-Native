# AP-2026-09-16-0910 — Papel de conta sintética deve ser atribuído explicitamente

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T1.1 / SPEC-1-001
- Sinal: o perfil da conta sintética foi criado pelo trigger `handle_new_user` com texto legado livre ("Gestor de Metas" no metadata, "colaborador" na coluna), e a associação automática de papel não reconheceu esse texto — a conta ficou em `consulta` e o teste humano retornou negações incorretas.
- Evidência: consulta em `profile_role_assignments` mostrando `role_key = consulta` antes da correção; tela `/permission-test` exibindo "Papel atual: Consulta"; migration `20260916085000_t11_fix_synthetic_test_role.sql` corrigindo para `gestor_dados`; novo teste exibindo "Papel atual: Gestor de dados" com resultados corretos.
- Regra reutilizável: ao criar conta sintética de teste, atribua o papel na mesma migration que cria a conta, por `profile_role_assignments` explícito; nunca infera autorização de campos de texto legado ou metadata de exibição.
- Quando aplicar: qualquer migration que crie usuários de teste ou associe papéis no projeto Panutrir.
- Quando não aplicar: contas reais provisionadas por administrador pela interface de gestão de papéis.
- Confiança: alta — causa raiz confirmada por reprodução antes/depois com o mesmo fluxo.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
