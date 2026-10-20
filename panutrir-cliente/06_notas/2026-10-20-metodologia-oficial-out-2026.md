# Metodologia oficial — Meta Comercial Cliente × SKU (Out/2026)

> Transcrição integral da planilha `Metodologia Meta Sku x Cliente.xlsx` enviada por Paulo em 20/10/2026.
> **Fonte da verdade do cálculo.** Substitui `2026-09-23-metodologia-oficial-ago-2026.md` (EMENDA 01, superada).
> Os IDs `M-01..M-31` são usados em todas as SPECs. A coluna "Aplicação Out/26" e "Controle" formam o **gabarito** de aceite.

| ID | Seção | Regra | Fórmula / procedimento | Aplicação Out/26 | Controle |
|---|---|---|---|---|---|
| M-01 | Objetivo | Construir a meta no menor nível gerencial relevante. | Cliente × SKU → Linha → Cliente → Promotor → Supervisor/Responsável → Canal → Empresa. | Modelo bottom-up. | Σ Meta Final = R$13MM |
| M-02 | Métrica | Meta em R$ de venda líquida. | Venda Líquida = vlritens − vlrdesc − vlrtroca. | Aplicado em todo o histórico. | — |
| M-03 | Exclusões | Panettones fora do modelo. | Excluir SKUs cujo produto/linha identifique Panettone. | Aplicado. | — |
| M-04 | Estrutura | Usar estrutura comercial atual pelo código do cliente. | Supervisor/responsável e promotor vêm do DE→PARA atual. | Aplicado. | 27 clientes ativos auditados sem estrutura válida. |
| M-05 | Elegibilidade SKU | Os últimos 3 meses definem somente quais SKUs recebem meta. | Cliente × SKU entra quando teve venda bruta positiva em Jul–Set/26. | Jul–Set/26. | 29.003 combinações no modelo final. |
| M-06 | Assaí SP | Usar apenas o sortimento vigente. | SKUs válidos: 5, 6, 1224, 69251 e 82051. PlufiNut é apenas origem da substituição. | Somente Assaí SP. | — |
| M-07 | SKU regular | Usar 24 meses completos. | M-1:M-6 = 35%; M-7:M-12 = 30%; M-13:M-24 = 35%. | Out/24–Set/26. | — |
| M-08 | Produtividade | Corrigir venda por dias úteis e sazonalidade. | Produtividade = Venda Líquida ÷ dias úteis; Prod. Dessazonalizada = Produtividade ÷ Índice Sazonal. | Aplicado mês a mês. | — |
| M-09 | Pbase | Ponderar os três blocos. | Pbase = 35%×Média B1 + 30%×Média B2 + 35%×Média B3. | Cliente × SKU. | — |
| M-10 | Baseline | Projetar para outubro. | Baseline = Pbase × IS Outubro × 22 dias úteis. | IS Outubro = 1,0319. | — |
| M-11 | Crescimento | Aplicar crescimento esperado já validado. | Meta Teórica = Baseline × (1 + 2,591659%). | +2,591659%. | — |
| M-12 | Introdução <12m | Enquanto o SKU não completa 12 meses na rede/cliente, não usar motor 24M. | Primeiro mês de meta: realizado do último mês × 1,25. Do 2º ao 12º mês: realizado do último mês × 1,10. | 2.739 combinações. | Rede identificada; cliente quando rede = 'Clientes'/em branco. |
| M-13 | Introdução sem venda no mês | A regra usa literalmente o último realizado. | Se Set/26 = 0, a Meta Própria Out/26 = 0. | 442 combinações. | Mantidas conforme regra aprovada. |
| M-14 | Piso técnico maduro | SKU maduro com venda recente não pode ficar com meta zero por efeito do motor 24M. | Piso = média dos meses com venda líquida positiva Jul–Set × (1 + G esperado). | 246 combinações. | Somente maduros; não substitui regra de introdução. |
| M-15 | Substituição | PlufiNut → Pão de Leite somente Assaí SP. | Transferência = Meta Teórica PlufiNut × 59%; PlufiNut Assaí recebe zero; transferência vai ao Pão de Leite da mesma loja. | 118 lojas; R$305.758,74. | 41% = demanda não recuperada. |
| M-16 | PlufiNut fora Assaí | Sem substituição. | Se elegível, segue introdução ou motor 24M/piso como qualquer SKU. | 749 combinações ativas. | — |
| M-17 | Meta Original | Somar meta própria + eventual transferência. | Meta Original Ajustada Cliente × SKU = Meta Própria + Transferência. | R$11.701.803,73. | +0,157% vs benchmark corporativo. |
| M-18 | GAP total | Reconciliar com a Meta Diretoria. | GAP = R$13.000.000 − Meta Original Bottom-up. | R$1.298.196,27. | — |
| M-19 | Indireto | Fixar participação final em 5,5%. | Meta Final Indireto = R$715.000. | Meta Original = R$435.375,28. | GAP Indireto = R$279.624,72. |
| M-20 | Direto | Receber o restante do GAP. | GAP Direto = GAP Total − GAP Indireto. | R$1.018.571,54. | Proporcional à Meta Original por responsável. |
| M-21 | Mix de linha | Usar os últimos 6 meses completos. | Share Especial = Especial ÷ (Branca + Especial). | Abr–Set/26; média = 29,4832%. | — |
| M-22 | Convergência Especiais | Unidades abaixo da média aproximam 50% da distância. | Se Share Esp. < média: Share GAP = Share atual + 50%×(média − atual). Se ≥ média, mantém share. | Somente GAP Direto. | — |
| M-23 | GAP por linha | Separar GAP Branca e Especiais. | Soma dos GAPs Responsável × Linha. | Branca R$888.938,14; Especiais R$409.258,13. | Total R$1.298.196,27. |
| M-24 | Descida do GAP | Levar GAP até Cliente × SKU. | Dentro de Responsável × Linha, distribuir proporcionalmente à Meta Original Ajustada. | Aplicado. | Meta Original zero não recebe GAP. |
| M-25 | Promotor em branco | Não criar promotor fictício. | Meta do cliente permanece somente no supervisor/responsável. | Aplicado. | — |
| M-26 | Baixa relevância | Sinalizar sem alterar meta. | Meta Final Cliente × SKU < R$300 → REVISAR. | 20.955 combinações. | Somente alerta gerencial. |
| M-27 | Auditoria estrutura | Não inferir responsável. | Clientes sem supervisor válido ficam fora da distribuição e na auditoria. | 27 clientes. | — |
| M-28 | Reconciliação Original | Fechamento da Meta Original. | Σ Meta Original Cliente × SKU. | R$11.701.803,73. | Fechado. |
| M-29 | Reconciliação GAP | Fechamento do GAP. | Σ GAP Cliente × SKU. | R$1.298.196,27. | Fechado. |
| M-30 | Reconciliação Final | Fechamento da Meta Final. | Σ Meta Final Cliente × SKU. | R$13.000.000,00. | Fechado. |
| M-31 | Consolidações | Todas as visões derivam do mesmo Cliente × SKU. | Σ SKU = Cliente; Σ Clientes = Promotor; promotores + clientes sem promotor = Supervisor; Σ Supervisores = Empresa. | Aplicado. | Sem ajuste manual. |

## Gabarito Out/26 (valores esperados do motor)

| Chave | Valor esperado | Regra |
|---|---|---|
| G-01 Σ Meta Final | R$13.000.000,00 | M-30 |
| G-02 Σ Meta Original Ajustada | R$11.701.803,73 | M-17, M-28 |
| G-03 Σ GAP | R$1.298.196,27 | M-18, M-29 |
| G-04 Meta Final Indireto | R$715.000,00 | M-19 |
| G-05 Meta Original Indireto | R$435.375,28 | M-19 |
| G-06 GAP Indireto | R$279.624,72 | M-19 |
| G-07 GAP Direto | R$1.018.571,54 (aritmética dá R$1.018.571,55 — ver Q-20) | M-20 |
| G-08 Share Especial médio Abr–Set/26 | 29,4832% | M-21 |
| G-09 GAP Branca | R$888.938,14 | M-23 |
| G-10 GAP Especiais | R$409.258,13 | M-23 |
| G-11 Combinações Cliente × SKU | 29.003 | M-05 |
| G-12 Combinações em introdução | 2.739 | M-12 |
| G-13 Introdução com último mês = 0 | 442 | M-13 |
| G-14 Combinações com piso técnico | 246 | M-14 |
| G-15 Lojas com substituição / valor | 118 lojas / R$305.758,74 | M-15 |
| G-16 PlufiNut fora Assaí ativas | 749 | M-16 |
| G-17 Combinações REVISAR (< R$300) | 20.955 | M-26 |
| G-18 Clientes sem estrutura válida | 27 | M-04, M-27 |
| G-19 Meta Original vs benchmark corporativo | +0,157% | M-17 (definição em Q-21) |

## Parâmetros Out/26

| ID | Parâmetro | Valor Out/26 |
|---|---|---|
| P-01 | Mês de referência | 2026-10 |
| P-02 | Meta Diretoria | R$13.000.000,00 |
| P-03 | Janela de elegibilidade | 3 meses (Jul–Set/26), venda bruta > 0 |
| P-04 | Janela e pesos do motor | 24 meses; M-1:M-6 = 0,35; M-7:M-12 = 0,30; M-13:M-24 = 0,35 |
| P-05 | Índice Sazonal do mês | Out = 1,0319 (tabela mensal e método: Q-08) |
| P-06 | Dias úteis do mês | Out = 22 (calendário: Q-09) |
| P-07 | Crescimento esperado G | 2,591659% |
| P-08 | Introdução | maturidade 12 meses; 1º mês ×1,25; 2º–12º ×1,10 |
| P-09 | Piso técnico | média dos meses positivos da janela de 3 meses × (1+G) |
| P-10 | Substituição | PlufiNut → Pão de Leite; escopo Assaí SP; taxa 0,59 |
| P-11 | Sortimento Assaí SP | SKUs 5, 6, 1224, 69251, 82051 |
| P-12 | Share final Indireto | 5,5% da Meta Diretoria |
| P-13 | Mix de linha | janela 6 meses; convergência 0,50; somente GAP Direto |
| P-14 | Limiar de baixa relevância | R$300 |
| P-15 | Exclusão | Panettone (descrição/categoria contém "PANETTONE") |
| P-16 | Tolerância de reconciliação | a definir (Q-20) |
