# DÚVIDAS — T1.2 (ciclo de meta) para decisão da Kim

**Data:** 22/10/2026
**Task:** T1.2 — Ciclo de meta (tabela/RPC), operações renomeadas, papéis reais
**SPEC:** `04_fase-atual/specs/SPEC-1-001.md`
**Estado:** analisada, **nada implementado** — aguardando as decisões abaixo
**Quem decide:** Kim (escopo/metodologia) · cliente (contas e papéis reais)

---

## Resumo

A T1.2 é elegível (T1.1 concluída) e o banco foi inspecionado em leitura. A parte nova
— tabela de ciclo, unicidade por mês, status — está clara na SPEC e não depende de ninguém.

O que trava são **três pontos de escopo** que a SPEC e a matriz não resolvem sozinhas:
o mapeamento das operações, os papéis reais e a dependência com a T3.1.

Nenhum deles é técnico difícil; todos são de decisão. Implementar por conta própria
significaria reescrever 27 políticas de RLS com base em suposição — exatamente o que o
método proíbe.

---

## DÚVIDA 1 — O mapeamento das 7 operações antigas para as 7 novas não é 1:1

### O que a SPEC diz

A T1.2 manda **renomear** as operações da matriz da T1.1 para esta lista:

`criar_ciclo` · `importar_bases` · `editar_estrutura` · `editar_parametros` ·
`executar_calculo` · `aprovar_publicar` · `exportar`

### O que existe hoje no banco

`criar_configurar_ciclo` · `importar` · `editar_catalogo` · `homologar` ·
`fechar_snapshot` · `gerenciar_papeis` · `exportar`

### Por que não é renomeação direta

Quatro operações antigas **não têm par óbvio** na lista nova, e três delas sustentam
políticas de RLS — renomear sem sucessor deixa a política apontando para uma operação
que não existe mais:

| Operação antiga | Usada em políticas RLS | Par na lista nova | Situação |
|---|---|---|---|
| `editar_catalogo` | **16 políticas** (6 tabelas do catálogo) | `editar_estrutura`? | provável, mas não declarado |
| `gerenciar_papeis` | **11 políticas** (papéis, perfis, matriz, auditoria) | **nenhum** | ⚠️ some sem sucessor |
| `exportar` | 2 políticas (auditoria) | `exportar` | idêntica, ok |
| `criar_configurar_ciclo` | 0 | `criar_ciclo` + `editar_parametros` | 1 antiga vira **2** novas |
| `importar` | 0 | `importar_bases` | provável |
| `fechar_snapshot` | 0 | `executar_calculo`? | ⚠️ snapshot foi **cancelado** pela EMENDA 02 |
| `homologar` | 0 | ? | ⚠️ sem par |

Total: **27 políticas de RLS** referenciam alguma operação antiga, de 37 existentes.

### Os três casos que travam

**(a) `gerenciar_papeis` desaparece.** Não está na lista da SPEC, mas é o que autoriza
escrever em `profile_role_assignments` e `role_operation_matrix`, e ler a auditoria
completa. Sem sucessor, essas 11 políticas ficam órfãs — e ninguém consegue mais
administrar papéis pela aplicação (hoje só o `administrador` tem essa operação `allow`).

**(b) `fechar_snapshot` perdeu o objeto.** O snapshot imutável foi cancelado pela
EMENDA 02, então a operação deveria morrer junto. A SPEC oferece `executar_calculo` como
substituto natural — mas lista `executar_calculo` como operação **nova**. Renomeação ou
operação adicional? Muda a matriz (7×7 = 42 células vira 7×8 ou 6×8).

**(c) `homologar`** (hoje só do papel `revisor`) não tem correspondente. Sumir com ela,
ou manter?

### Opções

**Opção A — Mapeamento declarado (recomendada).** A Kim fixa a tabela de-para explícita,
mantendo a lista de 7 operações da SPEC e encaixando `gerenciar_papeis` nela.

**Opção B — Lista de 8 operações.** Acrescentar `gerenciar_papeis` à lista (é
administração de acesso, não operação de meta). A matriz vira 6 ou 7 papéis × 8.

**Opção C — Manter as antigas e só acrescentar as novas.** Foge do "renomear" da SPEC e
deixa duas nomenclaturas convivendo — não recomendo.

### Minha leitura provável (a confirmar, não implementada)

| Antiga | Nova |
|---|---|
| `criar_configurar_ciclo` | `criar_ciclo` + `editar_parametros` |
| `importar` | `importar_bases` |
| `editar_catalogo` | `editar_estrutura` |
| `fechar_snapshot` | `executar_calculo` |
| `homologar` | *(absorvida? confirmar)* |
| `gerenciar_papeis` | *(manter — Opção B)* |
| `exportar` | `exportar` |

**Se a Kim não responder:** não implemento a renomeação; entrego a tabela de ciclo e o
RPC usando as operações existentes, e a renomeação fica pendente.

---

## DÚVIDA 2 — O papel `aprovador` não existe, e as contas de Léo e Ângelo também não

### O que a SPEC diz

> **Papéis reais:** Léo e Ângelo → `operador` (…); Paulo → `aprovador`
> **CA-1-01:** a matriz papel×operação cobre as 7 operações; Léo, Ângelo e Paulo têm
> atribuição explícita

### O que existe hoje

Papéis cadastrados: `administrador`, `auditor`, `consulta`, `gestor_dados`, `operador`,
`revisor`. **Não existe `aprovador`.**

Contas: **uma só** — `paulo.ferreira@panutrir.com.br`, associada a `gestor_dados`.
Léo e Ângelo não têm conta no Supabase.

### Perguntas

1. `operador` e `aprovador` **substituem** os seis papéis atuais, ou **convivem** com eles?
   (Se convivem, `gestor_dados` do Paulo fica ao lado de `aprovador`?)
2. `aprovador` é papel novo (renomear `revisor`? criar?) ou é o `administrador`?
3. Quais são os e-mails de Léo e Ângelo para o convite? Criar conta é **T1.3**
   (contas por convite), mas **CA-1-01 depende delas aqui**.

### Opções

**Opção A (recomendada).** Criar o papel `aprovador` como novo, atribuir ao Paulo;
atribuir `operador` a Léo e Ângelo quando as contas existirem (T1.3). Nesta task, entregar
a atribuição do Paulo e deixar a de Léo/Ângelo pronta para receber o `profile_id`.

**Opção B.** Mapear `aprovador` → `administrador` e não criar papel novo.

**Se não responder:** implemento a tabela e o RPC; **não** atribuo papéis nem mexo nos seis
existentes. O CA-1-01 fica em aberto e a task não pode ser concluída.

---

## DÚVIDA 3 — O ciclo depende de uma tabela que só nasce na T3.1

### O que a SPEC diz

`ciclo_meta` tem `parametros_versao_id` (FK para `parametros_versao`) entre os campos
mínimos. Mas `parametros_versao` é criada na **T3.1** — mesma leva A, e a matriz diz que
T1.2 depende **só** de T1.1.

### Por que importa

Se eu criar a FK agora, a T1.2 quebra (tabela inexistente). Só funciona se a T3.1 vier
antes.

### Opções

**Opção A (recomendada).** Criar `parametros_versao` na **T3.1 primeiro** e ajustar a
matriz: T1.2 passa a depender de T3.1. A ordem da leva A vira T3.1 → T1.2 → T1.3 → T2.1c.

**Opção B.** Criar `ciclo_meta.parametros_versao_id` **anulável e sem FK** na T1.2, e
aplicar a FK na T3.1. Mantém a T1.2 isolada, ao custo de um campo temporariamente solto.

**Opção C.** A T1.2 cria `parametros_versao` mínima (só a tabela, sem valores) e a T3.1
a preenche. Inverte a responsabilidade entre tasks.

**Se não responder:** uso a Opção B (anulável, sem FK), registro como dívida deliberada
no código com o gatilho de upgrade na T3.1, e sinalizo no changelog.

---

## Achado extra (não bloqueia a T1.2, mas é risco do programa)

**As migrations da T1.1 e da T4.1 não estão em nenhum repositório.**

O repositório público do código (`login-panutrir-ucjxoqmba`) contém **apenas**
`20260915123000_init_panutrir_auth.sql` — o commit `v0.0.1`, de 15/09. O banco tem
**21 versões** aplicadas (7 migrations, com duplicatas das restaurações).

Consequências:

1. A constituição exige "migrations versionadas"; na prática elas vivem só no histórico do
   banco Supabase.
2. **Uma restauração do zero não é reproduzível a partir do Git** — só a primeira migration
   sobrevive ao repositório.
3. A sincronização automática do Skip para o GitHub aparentemente parou no `v0.0.1`,
   embora o changelog registre QA até o `v0.0.14`.

Também vale notar: **não achei o repositório do Skip com as versões 0.0.2–0.0.14**. Se ele
existe e é outro (privado?), preciso do link para o trabalho não ficar sem rastro.

Sugestão: abrir task própria para reconciliar repositório × banco antes que alguém precise
restaurar o ambiente.

---

## O que dá para adiantar sem nenhuma dessas respostas

Se a Kim preferir destravar só a parte segura, isto **não** depende de decisão alguma:

- tabela `ciclo_meta` (`mes_referencia` único, `meta_diretoria` ≥ 0, `status`,
  `criado_por`, timestamps) com RLS deny-by-default
- RPC de criação idempotente (`on conflict do nothing`, devolve o existente)
- validação de `YYYY-MM` e de meta negativa
- auditoria da tentativa (inclusive a repetição e a negação)

Fica pendente apenas: renomeação das operações (Dúvida 1), atribuição de papéis
(Dúvida 2) e a FK de parâmetros (Dúvida 3).

---

## Anexo — evidências da inspeção (22/10/2026)

Banco `ewwjwewjpbqikknjjozb`, restaurado de `INACTIVE` para `ACTIVE_HEALTHY` nesta data.

```
12 tabelas em public, todas com RLS
6 papéis × 7 operações = 42 decisões → 13 allow / 29 deny
37 políticas de RLS; 27 referenciam operação antiga
  editar_catalogo  → 16 políticas (catalog_clientes/pendencias/produtos/responsaveis/
                     territorios/vinculos)
  gerenciar_papeis → 11 políticas (authorization_audit_log, profile_role_assignments,
                     profiles, role_operation_matrix)
  exportar         →  2 políticas (sobrepostas com gerenciar_papeis)
9 eventos de auditoria, todos de 16/09/2026, target_type = human_test
1 conta: paulo.ferreira@panutrir.com.br → gestor_dados
nenhuma tabela de ciclo (ciclo_meta / ciclos = null)
authorize_operation: SECURITY INVOKER (as private.* é que são SECURITY DEFINER)
```
