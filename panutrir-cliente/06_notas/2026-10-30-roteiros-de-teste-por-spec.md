# Roteiros de teste do cliente — Fase 1 (por SPEC)

**Data:** 30/10/2026 · Registrado conforme pedido do Alex ("ao terminar cada SPEC, deixe
registrado o roteiro do meu teste").
**Atualizado 30/10 14:40** após o envio do arquivo `Meta_Outubro_2026_Modelo_Final_Consolidado.xlsx`.

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
**Não aplicável.** Fecha pela prova automática. **T3.2 CONCLUÍDA em 30/10**: o IS veio pela
aba Metodologia (regra da seção 8): Out/26 = 1,0319 informado (P-05) e os 24 meses históricos
calculados pela regra com 2023–2025. 5/5 provas. Ressalva registrada: a regra aplicada aos dados
dá 1,018840 para outubro, então o 1,0319 é **valor informado**, não reproduzido — decisão registrada.

## SPEC-1-004 — Estrutura comercial, produtos e auditoria
**Não aplicável.** Fecha pela prova contra o G-18 (27 clientes).
**Avanço 30/10:** a aba `Auditoria Estrutura` do arquivo do cliente traz exatamente **27 linhas**
com o motivo de cada uma — a Q-07 está respondida na prática por esse arquivo.
**Falta:** a coluna de rede/canal/UF no cadastro (Q-04) para a carga definitiva.

## SPEC-1-005 — Motor da Meta Original
**Não aplicável.** Fecha pela prova contra G-02, G-05 e G-11..G-16.
**Avanço 30/10:** com as 118 lojas Assaí e os 27 da auditoria tirados do próprio arquivo do cliente,
o universo deu **28.936** (contra 29.003) e o PlufiNut fora do Assaí **746** (contra 749) — diferenças
de 67 e 3, contra 95 e 14 antes. O somatório ainda não fecha: **R$ 12.021.940,61** contra
R$ 11.701.803,73 (dif +R$ 320 mil). Causa provável medida: a maturidade do modelo é por **rede**
(1.293 das 2.739 introduções têm escopo REDE) e eu ainda calculo por cliente.

## SPEC-1-006 — GAP da Diretoria e distribuição
**Não aplicável.** Fecha pela prova contra G-03, G-04, G-06..G-10 e pela soma R$ 13.000.000,00.
**Estado:** depende da SPEC-1-005 reconciliada. O arquivo do cliente já traz as abas
`Meta Promotor` e `Meta Supervisor` com os valores esperados — vira a conferência linha a linha.

## SPEC-1-007 — Gabarito, painel e consulta
**Quando:** quando T7.1..T7.4 estiverem no ar. É o teste e o aceite da Fase 1 (T7.5).
**Quem testa:** Paulo, com Léo e Ângelo.
1. Abrir o painel do ciclo Out/26 e conferir os controles ao lado do gabarito (verde quando bate).
2. Escolher 5 combinações Cliente × SKU e abrir a explicação de cada número.
3. Exportar a meta e abrir no Excel.
**Esperado:** todos os controles batem com o gabarito; as 5 explicações se entendem sem a planilha;
a exportação soma R$ 13.000.000,00.
**Evidência:** mensagem do Paulo confirmando que testou e pode seguir.

## O que o arquivo de 30/10 mudou (Q-21)

O envio de `Meta_Outubro_2026_Modelo_Final_Consolidado.xlsx` resolveu parcialmente a **Q-21**:
13 abas, entre elas `Detalhe Cliente SKU` (que aponta para um CSV de detalhe ainda não enviado),
`Meta Cliente Linha` (4.198 linhas), `Meta Cliente` (2.202), `Meta Promotor` (124),
`Meta Supervisor` (19), `Novas Introducoes` (2.739), `Piso Tecnico Maduros` (246),
`Substituicao Assai SP` (118) e `Auditoria Estrutura` (27).
**Falta:** o CSV `Meta_Outubro_2026_Cliente_SKU_Detalhado_Final.csv`, citado na aba
`Detalhe Cliente SKU`. Sem ele a conferência é por agregado (Cliente, Promotor, Supervisor),
não linha a linha de Cliente × SKU.
