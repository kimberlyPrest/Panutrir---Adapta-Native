# Roteiros de teste do cliente — Fase 1 (por SPEC)

**Data:** 30/10/2026 · Registrado conforme pedido do Alex ("ao terminar cada SPEC, deixe
registrado o roteiro do meu teste").

## SPEC-1-001 — Acesso, papéis e ciclo de meta
**Quando:** na T1.3 (troca de senha e contas por convite) — **BLOQUEADO**, faltam os e-mails do Léo e do Ângelo.
**Quem testa:** Paulo, Léo e Ângelo, cada um com a própria conta.
1. Abrir o convite que chegou por e-mail.
2. Definir a senha e entrar no sistema.
**Esperado:** os três entram com a própria conta; a senha antiga (`Skip@Pass`) deixa de funcionar (prova automática).
**Evidência:** uma mensagem de cada um confirmando que entrou.

## SPEC-1-002 — Carga das bases reais de vendas
**Não aplicável.** Fecha pela prova automática: Σ por mês = fonte, 24 meses, tolerância R$ 0,01.
**Estado:** bloqueada na T2.3 — a carga oficial de ~888 mil linhas precisa da conexão do banco (DATABASE_URL).

## SPEC-1-003 — Parâmetros, calendário e execução versionada
**Não aplicável.** Fecha pela prova automática (CA-1-07 já provado; CA-1-08 e CA-1-09 com 19/19 provas locais).
**Ressalva:** o IS de Out/26 usa o valor oficial P-05; os demais meses seguem pendentes da Q-08.

## SPEC-1-004 — Estrutura comercial, produtos e auditoria
**Não aplicável.** Fecha pela prova contra o G-18 (27 clientes).
**Parada real:** se a auditoria de Out/26 não der 27 clientes, a lista é revisada com o Ângelo antes de seguir.
**Estado:** bloqueada na Q-04 (rede, canal, UF) e na Q-07 (supervisor válido).

## SPEC-1-005 — Motor da Meta Original
**Não aplicável.** Fecha pela prova contra G-02, G-05 e G-11..G-16.
**Estado:** bloqueada na Q-04. O protótipo com dados reais deu universo de 28.908 contra 29.003 do gabarito
(dif. 95) e PlufiNut fora do Assaí de 735 contra 749 — a causa medida é a falta de rede/canal/UF no cadastro.

## SPEC-1-006 — GAP da Diretoria e distribuição
**Não aplicável.** Fecha pela prova contra G-03, G-04, G-06..G-10 e pela soma R$ 13.000.000,00.
**Estado:** depende da SPEC-1-005 reconciliada.

## SPEC-1-007 — Gabarito, painel e consulta
**Quando:** quando T7.1..T7.4 estiverem no ar. É o teste e o aceite da Fase 1 (T7.5).
**Quem testa:** Paulo, com Léo e Ângelo.
1. Abrir o painel do ciclo Out/26 e conferir os controles ao lado do gabarito (verde quando bate).
2. Escolher 5 combinações Cliente × SKU e abrir a explicação de cada número.
3. Exportar a meta e abrir no Excel.
**Esperado:** todos os controles batem com o gabarito; as 5 explicações se entendem sem a planilha;
a exportação soma R$ 13.000.000,00.
**Evidência:** mensagem do Paulo confirmando que testou e pode seguir.
