# AP-2026-10-24-1706 — "Versão não se edita" precisa distinguir rascunho de oficial

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T3.1 / SPEC-1-003 (CA-1-07)
- Sinal: ao implementar imutabilidade de versão com trigger `before update`, a primeira versão recusava UPDATE em **qualquer** status — inclusive no rascunho recém-criado. Como a função que cria a versão nova clona os parâmetros e depois **atualiza** as linhas clonadas para aplicar as alterações pedidas, ela falhava contra o próprio trigger. O teste do critério pegou o defeito; a mensagem apontava a linha exata do `UPDATE`.
- Evidência: `criar_versao_parametros` devolveu `ERROR 23001: parametros_valor e imutavel...` ao tentar mudar P-07. Após a correção (rascunho editável, oficial congelada), a mesma chamada devolve a versão nova e a v1 permanece com 0,02591659. Provas de fechamento todas aprovadas.
- Regra reutilizável: em entidade versionada, a imutabilidade vale para o estado **publicado**, não para o ciclo de vida inteiro. O rascunho precisa ser editável, senão o próprio fluxo de "criar versão a partir da anterior" se auto-bloqueia. Modele o status e consulte-o no trigger antes de recusar.
- Quando aplicar: qualquer tabela com versionamento + workflow (parâmetros, especificações, metas publicadas, snapshots).
- Quando não aplicar: entidade append-only de verdade, onde nem o rascunho pode mudar depois de gravado.
- Confiança: alta — o defeito foi reproduzido, corrigido e re-provado do zero.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
