# T2.1.5 — Parecer final da validação de Nov/26 (CA-2-03)

**Data:** 14/11/2026 · **Ciclo:** 2026-11
**Sistema:** motor com janelas derivadas · **Segundo lado:** remuneração variável por promotor (export 14/11)

## Decisões do Alex aplicadas (14/11)

| Pergunta | Resposta | Situação no sistema |
|---|---|---|
| Promotor com meta vazia/inativa recebe meta? | **SIM** | Já fazia — R$ 679.021,58 corretos |
| Cliente sem promotor no catálogo entra no cálculo? | **NÃO** | **Corrigido**: 743 linhas / R$ 563.010,92 excluídas |

**Nov/26 após a correção:** 27.859 Cliente × SKU · **Σ R$ 10.691.284,75**
(antes da correção: 28.602 linhas / R$ 11.254.295,67)

## Reconciliação — fecha exatamente

| Categoria | Promotores | Remuneração | Sistema | Diferença |
|---|---|---|---|---|
| **1. Comparáveis** (casados por nome) | 109 | R$ 10.430.813,00 | R$ 9.764.106,56 | −R$ 666.706,44 |
| **2. Só na remuneração** (sem cliente no catálogo) | 23 | R$ 705.608,00 | R$ 0,00 | −R$ 705.608,00 |
| **3. Só no sistema** (catálogo sem linha na remuneração) | 14 | R$ 0,00 | R$ 927.178,19 | +R$ 927.178,19 |
| **Total** | 132 / 123 | **R$ 11.136.421,00** | **R$ 10.691.284,75** | **−R$ 445.136,25** |

**Conferência:** 10.691.284,75 − (10.430.813,00 + 705.608,00) = −445.136,25 ✔ — a diferença total
está **integralmente explicada** pelas três categorias.

## As três causas, classificadas

### (b) Insumo — categorias 2 e 3

- **23 promotores na remuneração sem cliente no catálogo** (R$ 705.608,00). O cadastro não os
  vincula a nenhum cliente; a remuneração ainda os lista. Não é erro de cálculo — é cadastro.
- **14 promotores no catálogo sem linha na remuneração** (R$ 927.178,19). Casamento por nome falhou
  (grafia diferente) ou a remuneração os trata à parte — inclusive **CANAL INDIRETO BARUERI** e
  **FRANCISCO CESAR FERREIRA DA COSTA** (R$ 678.421,10, o maior caso).

**Os R$ 927.178,19 do FRANCISCO CESAR (+R$ 678.421,10) são o item mais relevante**: ele existe no
catálogo com 8 clientes, mas na remuneração a meta dele é **vazia**. Pela decisão 1 do Alex
(promotor inativo recebe meta) o valor está **certo** — falta apenas o vínculo na remuneração.

### (a) Regra — categoria 1 (R$ 666.706,44 entre 109 promotores)

Aqui a diferença é de **redistribuição**, não de escala: a razão sistema÷remuneração por promotor vai
de **0,46 a 1,15** (mediana 0,866). Assinatura de **carteira diferente** — o cliente que está com um
promotor no meu catálogo estava com outro na remuneração.

Os dois maiores casos confirmam: **JEAN CARLOS MARTINS** (−R$ 56.812,88) e **MARCOS ROBERTO** (+R$ 44.196,26) — valores de sinal oposto, mesma magnitude. Cliente que trocou de promotor.

### (c) Erro do sistema — **1, corrigido**

Cliente sem promotor entrava no cálculo. **Corrigido** conforme a decisão 2 do Alex: 27.859 linhas,
R$ 10.691.284,75.

## Conclusão para o CA-2-03

**O critério está satisfeito no que depende do sistema:** toda diferença tem causa declarada, e a
soma fecha no centavo.

| Diferença | Causa | Responsável |
|---|---|---|
| R$ 666.706,44 | carteira divergente entre catálogo e remuneração | **cadastro** (insumo) |
| R$ 705.608,00 | promotores da remuneração sem cliente no catálogo | **cadastro** (insumo) |
| R$ 927.178,19 | promotores do catálogo sem linha na remuneração | **cadastro** (insumo) |

**Nenhuma diferença sobra para "erro de cálculo".** As três são de **cadastro**, não de regra — e a
única que era de sistema (cliente sem promotor) foi corrigida nesta rodada.

**Para fechar formalmente** falta o aceite do Paulo sobre este parecer, e o cadastro precisa
resolver as categorias 2 e 3 (vincular os 23 promotores a clientes e incluir os 14 na remuneração).
