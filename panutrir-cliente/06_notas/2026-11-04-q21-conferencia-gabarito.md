# Q-21 — Conferência linha a linha do gabarito Out/26 (04/11/2026)

**Fonte:** workbook `Meta_Outubro_2026_Modelo_Final_Consolidado.xlsx` (gabarito vivo, 13 abas) × motor (meta_linha do app, 28.936 linhas Cliente × SKU).

**Referência da pergunta:** Q-21 no registro central (SPEC-1-007 / T7.1) — "Pode enviar a planilha de resultado Out/26 linha a linha?" O CSV citado na aba Detalhe do gabarito (`Meta_Outubro_2026_Cliente_SKU_Detalhado_Final.csv`) **não existe** (já registrado em 30/10); a conferência usou as abas Meta Cliente (2.201 linhas + TOTAL) e Meta Cliente Linha (4.197 linhas).

## Bug achado e corrigido: GAP Indireto zerado na meta_linha

Os 6 clientes do canal Indireto (80353 DISTRIBUIDOR MARCOS, 80398 JPS DISTRIBUIDORA, 84136 RICARDO DISTRIBUIDOR, 75948 OCTAGON DISTRIBUIDOR SP, 82978 DISTRIBUIDORA ABBA, 83780 GAMACAISA) estavam com `gap_linha = 0` na `meta_linha` do app: a descida do GAP Indireto (R$ 279.624,72 = G-06) não tinha sido gravada na carga da T7.3 — o `via_gap` dizia "proporcional à Meta Original", mas o valor nunca foi aplicado (106 linhas afetadas).

**Regra provada 12/12 contra o gabarito** (aba Meta Cliente Linha): `gap_linha = GAP do canal × Meta Original da linha ÷ Meta Original do canal` — CANAL INDIRETO: GAP 144.420,15 / MO 224.861,95; CANAL INDIRETO BARUERI: GAP 135.204,58 / MO 210.513,33 (razão idêntica 0,642261 nos dois canais).

**Correção aplicada no Supabase real** (UPDATE nas 106 linhas, ciclo 2026-10, com nota na memória JSONB): Σ GAP R$ 1.308.616,18 · Σ Meta Final R$ 12.988.257,86 (28.936 linhas). O painel `/controles` e o drill-down `/consulta` passam a mostrar o GAP Indireto.

## Divergências restantes (explicadas, nenhuma é erro de fórmula)

| Grandeza | Gabarito | Motor | Diferença | Causa |
|---|---|---|---|---|
| Meta Original | 11.701.803,73 | 11.679.641,68 | −22.162,05 | universo −0,19% (SKUs sem produto 141951/2279 + auditoria do gabarito — D2/D3 na Kim) + arredondamento por linha |
| GAP | 1.298.196,27 | 1.308.616,18 | +10.419,91 | GAP Direto maior porque a Meta Original do universo é menor (mesma causa) |
| Meta Final | 13.000.000,00 | 12.988.257,86 | −11.742,14 | resíduo do universo |

Mediana da razão gabarito÷motor por cliente = **0,9999** — as divergências linha a linha são dominadas por arredondamento: o gabarito grava cada linha a 2 casas e o motor soma cru e arredonda o total. Q-20 (resíduo na maior combinação) e D2/D3 (Kim) explicam o resíduo; seguem pendências.

## Entregável

`artifacts/q21_conferencia_gabarito_out26.xlsx` — 3 abas: Meta Cliente (2.157 linhas, gabarito × motor com as 3 diferenças e status), Meta Cliente Linha (4.142 pares) e Resumo (diagnóstico completo).

## Registro

- Changelog: entrada [ETHOS] · 2026-11-04 · Q-21 executada (+ incidente de push do changelog documentado).
- Registro central: Q-21 marcada `respondida (04/11/2026, Alex)`.
- Correção no banco: UPDATE nas 106 linhas Indireto da `meta_linha` (ciclo 2026-10).