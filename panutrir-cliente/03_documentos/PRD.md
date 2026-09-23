# PRD — Panutrir

> Documento de requisitos do produto. Versão corrente inclui EMENDA 01/2026
> (metodologia oficial de cálculo da meta, ago/2026).

## 1. Contexto

A Panutrir (Nutri e Equilíbrio Panificação LTDA) é uma indústria regional de pães
que atende PR/SC/MS/SP. O projeto estabelece o sistema inteligente de definição
e distribuição de metas comerciais, primeiro de vários projetos contratados.

## 2. Problema

A definição de metas comerciais hoje é manual, pouco rastreável e não considera
de forma sistemática a sazonalidade histórica nem o potencial de cada região,
supervisor e promotor.

## 3. Objetivo de sucesso

Metas comerciais rastreáveis, definidas com metodologia oficial reproduzível
e distribuídas por supervisor/promotor/região, com reconciliação bloqueante
contra a memória de cálculo oficial.

## 4. Requisitos funcionais (síntese)

- RF-01..RF-09: conforme escopo definitivo (importação de bases, catálogo de
  produtos, hierarquia comercial, cálculo de potencial, distribuição de metas,
  acompanhamento, painéis, exportações, auditoria).
- **RF-10 (EMENDA 01/2026)**: o cálculo da meta segue a metodologia oficial
  documentada em `06_notas/2026-09-23-metodologia-oficial-ago-2026.md`
  (venda líquida, IS sazonal por mediana, baseline 24 meses com pesos 35/30/35,
  G 40/60, GAP Diretoria, mix 5,5% indireto, Branco/Especial com convergência 50%).

## 5. Regras de negócio (síntese)

- RN-01..RN-18: conforme escopo definitivo.
- **RN-19 (EMENDA 01/2026)**: a reconciliação entre o resultado calculado pelo
  sistema e a memória de cálculo oficial é BLOQUEANTE — divergência impede a
  publicação da meta até resolução.

## 6. Fora de escopo (Fase 1)

- Integração Nielsen/Scanntech (condicionada a decisão posterior)
- Política de remuneração
- Logística/rotas (frente futura do cliente)

## 7. Dependências

- CSV histórico de vendas (gate de execução G1–G3)
- Metodologia oficial: DISPONÍVEL (ago/2026) — ver EMENDA 01/2026
