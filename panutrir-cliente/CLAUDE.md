# Panutrir — contexto do cliente

**Projeto:** Intranet Panutrir — Metas Comerciais (módulo 1) e Logística (módulo 2)  
**Consultora:** Kim · **CSM:** Matheus  
**Dono do projeto:** Paulo · **Implementação:** Léo · **Champion operacional:** Ângelo  
**Arquitetura:** Supabase + front React no Skip  
**Fase ativa:** 1 — Motor de meta Cliente × SKU com dados reais (EMENDA 02/2026)

## Resultado esperado da fase
O sistema calcula a meta de Out/26 com dados reais pela metodologia oficial e reproduz a planilha do Paulo: R$13.000.000,00 fechados, gabarito batendo, cada número explicado.

## Fonte da verdade
- Cálculo: `06_notas/2026-10-20-metodologia-oficial-out-2026.md` (regras M-xx, gabarito G-xx, parâmetros P-xx).
- Ordem e status das tasks: `04_fase-atual/matriz-specs-fases.md`.
- Perguntas ao cliente: `03_documentos/perguntas-ao-cliente.md`.

## Ritmo
Tasks em sequência, sem pedir autorização nem teste entre elas. O teste do cliente é por SPEC: na Fase 1, só o login com contas convidadas (T1.3) e o aceite de Out/26 no painel (SPEC-1-007). Regra completa em `AGENTS.md`.

## Limites da Fase 1
- Dados reais **permitidos** no Supabase do projeto. Nunca em repositório (os repositórios são públicos).
- Sem aprovação/publicação, consulta pela equipe, cenários, logística ou IA.
- A EMENDA 01 (ago/26) está superada; não usar `2026-09-23-metodologia-oficial-ago-2026.md`.
