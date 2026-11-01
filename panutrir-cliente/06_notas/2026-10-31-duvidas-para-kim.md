# DÚVIDAS para a Kim — 31/10/2026 (métrica do motor e universo da T5.1)

**Contexto:** três DÚVIDAS acumuladas em 31/10, todas já registradas no changelog. Nenhuma bloqueia o andamento geral da Fase 1 (12/30 tasks concluídas), mas cada uma trava a parte dependente. Cada uma traz evidência e leitura provável; a decisão final fica registrada em **Respostas** na SPEC correspondente.

---

## D1 — A métrica do modelo varia por regime? (motor — T5.2/T5.3/T5.4)

**A dúvida:** a metodologia (regra 2) escreve UMA fórmula de venda líquida (`vlritens − vlrdesc − vlrtroca`), mas o gabarito executa DUAS:

- **PISO e INTRODUÇÃO** usam `vlritens − vlrdesc` (sem a troca);
- **REGULAR_24M** usa a líquida de 3 termos (com a troca).

**Evidência (provas v17–v19, banco local):**

- Piso: `vlritens−vlrdesc` reproduz **244/246** linhas da aba `Piso Tecnico Maduros`; com a líquida de 3 termos, só 107/246.
- REGULAR: isolando 1.237 clientes puro-REGULAR (sem nenhum SKU de introdução/piso/substituição), a mediana da razão gabarito÷meu é **1,0009** com a líquida (398 clientes batem no centavo) contra **0,9306** com `vlritens−vlrdesc` (72 batem; viés sistemático de +7%, o peso das trocas).
- Prova pontual do piso: par 63421×69251 ago/26 — gabarito 24,25 = 26,36 − 2,11 (a líquida com troca daria 12,12).

**Efeito no total:** motor híbrido (piso/intro com `vlritens−vlrdesc`, regular com líquida) dá **Σ R$ 11.662.784,32 (−0,33% do gabarito)**; com uma métrica só, fica +5,84% ou −0,68%.

**Sub-questão:** o Carrefour tem maturidade por LOJA (não pela rede "GRUPO CARREFOUR")? Com Carrefour por loja, o total melhora para **−0,22%** e as introduções sobem para 2641/2739 — consistente com `Meta Cliente Linha`, onde a "linha" do Carrefour é a loja. Muffato e São Francisco por LOJA pioram (+2,04%) e ficam por rede.

**Leitura provável:** é isso mesmo — métrica por regime, e Carrefour por loja. **O que trava:** o motor não é publicado como fechado até a confirmação.

---

## D2 — SKUs sem produto no universo G-11 (T5.1)

**A dúvida:** como o modelo trata SKUs vendidos sem produto cadastrado? Dois casos em jul–set/26: **141951 (131 pares no universo)** e **2279 (1 par)**.

**Evidência:** o gabarito G-11 = 29.003 combinações. Minhas medidas do universo: 28.936 (catálogo de 53 SKUs + auditoria de 27 clientes) · 28.988 (+ clientes 0/vazio, ver D3) · 29.057 (+ SKUs sem produto só com líquida>0) · 29.068 (sem filtro de catálogo) · 29.120 (+ 141951 fora do Assaí e 2279). Seis hipóteses testadas; nenhuma fecha exatamente os 15 pares que restam após somar os clientes da D3.

**Leitura provável:** o gabarito conta parte dos pares dos SKUs sem produto — mas com qual regra? **O que trava:** o CA-1-13 (universo = 29.003) não fecha; a T5.1 fica a −15 pares (−0,05%).

---

## D3 — Os clientes "0" e "vazio" entram no universo? (T5.1 e contrato `vendas` v2)

**A dúvida:** a carga rejeita 60 linhas de 2026 por V-02 (código de cliente ausente/zero): 30 com `codcli=0` (R$ 50.002,93) e 30 com `codcli` vazio (R$ 41.931,62). Mas a aba `Auditoria Estrutura` do gabarito traz o **código 0 como cliente real, com venda bruta de exatamente R$ 50.002,93** — ou seja, o modelo trata esses códigos como clientes.

**Evidência:** `codcli=0` tem 30 SKUs distintos (29 válidos, fora o 141951); `codcli` vazio tem 23 SKUs válidos. Somando os dois ao universo: 28.988 (faltam 15 para o G-11).

**Leitura provável:** entram — e o contrato `vendas` v2 (regra V-02) precisa de exceção, ou o BI passa a exportar esses códigos resolvidos. **O que trava:** o universo da T5.1 e a regra de carga; a decisão muda o contrato.

---

**Resumo do que pedimos:** resposta à D1 (confirmação da métrica por regime e do Carrefour por loja), à D2 (a regra dos SKUs sem produto) e à D3 (se 0/vazio entram e como tratar na carga). Com as três, a T5.1 fecha e o motor é publicado como fechado.
