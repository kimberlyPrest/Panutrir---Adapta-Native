# 2026-10-30 — Maturidade: a regra do modelo do cliente e o limite do dado-fonte

**Contexto.** A T5.1/T5.2 depende de saber quando um par cliente×SKU é *introdução* (regime de
1,25× / 1,10×) e quando é *maduro* (35/30/35 sobre produtividade). A M-12 fala em "rede
identificada; cliente quando rede = 'Clientes'/em branco", mas não diz como tratar o histórico
anterior à janela. Alex autorizou testar o histórico anterior à janela de 24 meses.

**Método de prova.** O arquivo `Meta_Outubro_2026_Modelo_Final_Consolidado.xlsx` traz, na aba
`Novas Introducoes`, as 2.739 combinações que o próprio modelo classificou — com escopo,
primeira venda, taxa e meta. Comparar a minha classificação com a dele é prova direta, não
interpretação da metodologia.

## Resultados medidos

| Leitura da maturidade | Datas iguais ao cliente | Σ Meta Original | vs gabarito |
|---|---|---|---|
| 1ª venda na janela de 24 m (out/24–set/26) | 2.597/2.739 — 94,8 % | R$ 11.631.176,17 | −0,60 % |
| 1ª venda no histórico completo (33 m, jan/24–set/26) | 2.594/2.739 — 94,7 % | R$ 11.621.672,67 | −0,69 % |
| **Regra R** (abaixo) | **2.651/2.739 — 96,8 %** | R$ 11.993.389,12 | **+2,49 %** |

A autorização do Alex foi testada e **descartada**: usar o histórico completo piora o resultado
em R$ 9,5 mil e não corrige os casos divergentes.

## A regra que o modelo realmente usa (regra R)

> A 1ª venda **da rede** só vale se tiver acontecido **dentro da janela de 24 meses** (≥ out/24).
> Se a rede já vendia o SKU antes disso, o modelo não enxerga — e a introdução reportada é a 1ª
> venda do **próprio cliente** (em qualquer momento do histórico).

Evidência: 2.681 das 2.722 taxas declaradas (98,5 %) batem exatamente com 1,25×/1,10× calculados
por essa regra. O cliente aplica 1,10× em 2.125 casos e 1,25× em 172.

## O paradoxo — e a sua causa

A regra R acerta as datas e as taxas, mas **infla** o total em 2,49 %. Causa medida: ela
classifica 3.420 combinações como introdução, contra as 2.739 que o cliente lista. Ou seja, meu
universo contém cerca de 681 pares que o cliente **não tem** na lista. Dentro das 2.739 que
existem, minhas metas somam R$ 38.611 a **menos** que as dele.

Não é problema de regra — é de **fonte**. Exemplo limpo: cliente 75772 (Grupo São Francisco).
Os dados congelados mostram vendas dos SKUs 2, 5, 6, 11 e 16 desde janeiro de 2024; o cliente
declara primeira venda em setembro de 2026, com escopo próprio. Nenhuma regra de janela explica
essa diferença.

**Hipótese descartada:** "a maturidade considera só `tipo='Venda'` (bonificação não inaugura o
item)". Nos 138 pares divergentes, **0** têm alguma linha com `tipo='Venda'`; em 86 deles a 1ª
linha de qualquer tipo bate exatamente com a data declarada. O tipo, portanto, não é o critério.

## Consequência para a T5.1/T5.2

O motor fica com a leitura da janela de 24 m (a mais próxima do gabarito, −0,60 %) e a regra R
documentada como a regra do cliente, para ser ativada quando a divergência de fonte for resolvida.
Fechar os R$ 70,7 mil restantes exige o CSV linha a linha
`Meta_Outubro_2026_Cliente_SKU_Detalhado_Final.csv` (citado na aba `Detalhe Cliente SKU`, ausente
do pacote). Sem ele, qualquer ajuste seria chute calibrado contra o próprio gabarito — o que
transformaria a prova em ajuste.

## Controles do motor nesta rodada

| Controle | Meu motor | Gabarito | Diferença |
|---|---|---|---|
| G-15 substituição Assaí SP | 118 lojas / R$ 306.113,26 | 118 / R$ 305.758,74 | +R$ 354,52 (0,1 %) |
| G-16 PlufiNut fora Assaí | 746 | 749 | −3 |
| G-11 universo | 28.936 | 29.003 | −67 |
