# T2.1.5 — Validação paralela de Nov/26 (estado em 12/11/2026)

**Status:** PREPARADA — a execução aguarda 2 insumos externos.

## O que já está pronto

1. **Ciclo Nov/26 criado pelo sistema** (fluxo da T2.1.2): `criar_ciclo_com_herdanca('2026-11')`
   criou o ciclo com a versão `HERDADA-2026-11` e os 4 parâmetros de negócio
   (P-02 Meta Diretoria, P-05 IS, P-06 dias úteis, P-07 G) marcados
   `REQUER_CONFIRMACAO` — o operador confirma na tela /parametros antes de executar.
2. **Janelas derivadas** (T2.1.1, sem deploy): elegibilidade 2026-08..2026-10 ·
   histórico 2024-11..2026-10 · mix 2026-05..2026-10.
3. **Motor fechado**: D1 confirmada pela Kim (11/11) — métrica por regime
   (PISO/INTRODUÇÃO 2 termos, REGULAR 3 termos; Carrefour por loja).
4. **Universo definido**: D2 — SKUs 141951/2279 fora; D3 — clientes 0/vazio dentro.

## O que falta (insumos externos)

| Insumo | Dono | Uso |
|---|---|---|
| **BI Out/26 fechado** (congelada) | BI/cliente | M1 do motor de Nov/26 + carga pela rotina operacional (T2.1.3) + CA-1-12 da Fase 1 |
| **Planilha do processo atual do Paulo para Nov/26** | Paulo | O outro lado da comparação (validação paralela) |

## Fluxo quando os insumos chegarem

1. Ângelo carrega Out/26 pela rotina operacional (sem SQL): `python3 contracts/carga_operacional.py <congelada.xlsx> --operador "Ângelo"`
2. Ângelo confirma os 4 parâmetros herdados na tela /parametros (informando o motivo)
3. Sistema executa Nov/26 (motor oficial com as janelas de 2026-11)
4. Paulo calcula Nov/26 pelo processo atual (planilha)
5. Reconciliação item a item: toda diferença classificada em (a) regra em aberto,
   (b) insumo de fonte diferente, (c) erro do sistema — só (c) bloqueia
6. Aceite do Paulo registrado no changelog e no CA-2-03
