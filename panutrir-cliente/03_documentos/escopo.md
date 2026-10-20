# Escopo — Intranet Panutrir (Metas + Logística)

**Estado:** REVISADO pela EMENDA 02/2026 em 20/10/2026 — aguardando aceite de Paulo e Matheus  
**Prazo:** 4 meses reiniciados a partir de 06/10/2026 (combinado com Erik) → **até 06/02/2027**  
**Direção:** primeiro a meta calculada com dados reais; governança só o necessário; logística como segundo módulo.

## 1. Resultado contratado

Ao final, a Panutrir gera, aprova e publica a meta mensal Cliente × SKU pela própria metodologia, sem planilha, fechando com a Meta Diretoria e explicando cada número. Acompanha o realizado. O CD modelo monta cargas com proposta de menor custo, e a meta alimenta a previsão de volume logístico.

## 2. Fases

| Fase | Entrega demonstrável | SPECs | Janela indicativa |
|---|---|---|---|
| **1 — Motor de meta Cliente × SKU com dados reais** | Out/26 reproduzido no sistema: R$13MM fechados, gabarito batendo, consulta com memória de cálculo | SPEC-1-001..007 | 20/10 – 14/11/2026 |
| **2 — Ciclo mensal operável** | Nov/26 em paralelo com a planilha; Dez/26 publicado pelo sistema, com cenários e consulta da equipe | SPEC-2-001..004 | 17/11 – 05/12/2026 |
| **3 — Acompanhamento e indicadores** | realizado × meta, trocas, visitas, diagnósticos (ROI promocional opcional) | SPEC-3-001..004 | 08/12 – 19/12/2026 |
| **4 — Módulo Logística** | CD modelo com proposta de cargas comparada ao plano manual | SPEC-4-001..003 (descoberta começa em 21/10) | 05/01 – 23/01/2027 |
| **5 — Integração e IA assistiva** | meta → volume por CD; IA explica e sugere; KPIs finais e passagem | SPEC-5-001..003 | 26/01 – 06/02/2027 |

As datas são indicativas; Matheus confirma com o cliente. A Fase 3 é a primeira a ser enxugada se a Fase 1 atrasar (a SPEC-3-004 é opcional).

## 3. Marcos de liberação

- **L1 — Out/26 reproduzido:** CA-1-21 e aceite do Paulo. Encerra a Fase 1.
- **L2 — Nov/26 paralelo aceito:** CA-2-03. Libera o desligamento da planilha.
- **L3 — Descoberta logística aprovada:** CA-4-04. Libera a construção da Fase 4.

## 4. Requisitos vinculantes

RF-01..RF-31, RN-01..RN-15 e RNF-01..RNF-09 do PRD v1.0.

## 5. Perguntas em aberto

Não bloqueiam o início das SPECs. Cada task pergunta quando precisa e implementa conforme a resposta (`03_documentos/perguntas-ao-cliente.md`, protocolo em `AGENTS.md`).

## 6. Fronteiras

Não substitui SAP/Metabase, não calcula remuneração, não usa potencial externo e não executa campanhas. Logística limitada ao CD modelo; expandir para os demais CDs é evolução posterior.

## 7. Arquitetura

Supabase (Auth, Postgres, RLS, Edge Functions, migrations) + front React no Skip, um único projeto para os dois módulos. Cálculo determinístico no banco/Edge Function; IA só na Fase 5 e fora do caminho crítico.
