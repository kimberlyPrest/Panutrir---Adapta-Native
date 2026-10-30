# 2026-10-30 — O CSV citado não existe; o gabarito detalhado está no próprio workbook

## Verificação

A aba `Detalhe Cliente SKU` do `Meta_Outubro_2026_Modelo_Final_Consolidado.xlsx` cita o arquivo
`Meta_Outubro_2026_Cliente_SKU_Detalhado_Final.csv` (29.003 combinações). Ele **não existe**:
- não está nos arquivos enviados (nenhum nome com `Detalhado` ou `Cliente_SKU`);
- não está no repositório de documentação nem no do código (busca de código no GitHub: 0 resultados).

## O que o workbook já entrega — e é melhor que o CSV citado

| Aba | Conteúdo | Cobre |
|---|---|---|
| `Controle SKU` | totais por regime | os 4 regimes + total + GAP |
| `Piso Tecnico Maduros` | as 246 linhas **com o piso calculado** | regime PISO inteiro |
| `Novas Introducoes` | as 2.739 com escopo, 1ª venda, taxa, venda set, meta | regime INTRODUÇÃO inteiro |
| — | — | falta linha a linha só o REGULAR_24M (26.017 pares, o maior) |

### Gabarito por regime (`Controle SKU`)

| Regime | Combinações | Meta Original |
|---|---|---|
| INTRODUÇÃO | 2.739 | R$ 645.489,705 |
| PISO_MADURO | 246 | R$ 7.858,299 |
| REGULAR_24M | 26.017 | R$ 11.047.457,273 |
| SEM HISTÓRICO RECENTE | 1 | R$ 998,456 |
| **TOTAL** | **29.003** | **R$ 11.701.803,732** |

Meta Final R$ 13.000.000; GAP R$ 1.298.196,2678.

## Fórmula do piso — provada 246/246

```
Piso = média(Jul/26, Ago/26, Set/26 considerando SÓ os meses com venda > 0) × (1 + G)
```

Exemplo: vendas [0; 14,68; 29,36] → média dos positivos (14,68+29,36)/2 = 22,02 → × 1,02591659 = **22,5907** (gabarito: 22,590683320853557).

## Achado colateral que muda o motor: é VENDA BRUTA, não líquida

As colunas do gabarito chamam-se "Venda Líq", mas o valor usado é **venda bruta**:

| Base usada na fórmula | Acertos entre as 246 |
|---|---|
| `venda_liquida` do banco | 109/246 |
| `venda_bruta` do banco | 223/246 |
| as próprias colunas do arquivo | **246/246** |

As 23 divergências com a bruta do banco são ICMS/descontos de algumas lojas — questão de conferência
com o BI, não de fórmula. Consequência: o cálculo do cliente usa **venda bruta** (consistente com a
M-06), e não `venda_liquida`.

## Estado do motor com a correção

| Regime | Meu nº | Gabarito | Minha meta | Gabarito |
|---|---|---|---|---|
| INTRODUÇÃO | 3.900 | 2.739 | R$ 1.306.561,03 | R$ 645.489,70 |
| PISO | 209 | 246 | R$ 6.193,70 | R$ 7.858,30 |
| REGULAR | 24.822 | 26.017 | R$ 11.909.664,77 | R$ 11.047.457,27 |
| SEM HISTÓRICO | 5 | 1 | R$ 615,73 | R$ 998,46 |
| **TOTAL** | **28.936** | **29.003** | **R$ 13.223.035,23** | **R$ 11.701.803,73** |

Progresso estrutural medido: com a 1ª venda da rede sobre **venda bruta**, as introduções que o
motor encontra são **subconjunto exato** da lista do cliente — **2.609 de 2.609 estão na lista**
(nenhum falso positivo; faltam 130 do cliente). A diferença de valor concentra-se no REGULAR_24M,
que é justamente o único regime sem gabarito linha a linha.

## O que isso significa para a T5.1

O motor não será fechado por tentativa: falta o detalhamento do REGULAR_24M, e é nele que está
R$ 862 mil de diferença. Duas saídas possíveis, ambas do cliente: (1) exportar a aba/CSV com as
26.017 linhas do REGULAR_24M na mesma estrutura de `Novas Introducoes`; (2) confirmar que o
critério de 1ª venda é o que está documentado. Até então, o número do motor não deve ser
apresentado como fechado.
