# 2026-10-20 — EMENDA 02/2026: reset do programa e metodologia Out/26

**Origem:** reunião de alinhamento de 06/10/2026 (Paulo, Léo, Erik, Matheus) e planilha `Metodologia Meta Sku x Cliente.xlsx` enviada por Paulo em 20/10/2026.
**Substitui:** EMENDA 01/2026 (23/09) por completo.

## Por que

1. Em 06/10 o cliente avaliou que o plano construía plataforma e governança, mas nenhuma meta. Léo: "montar a plataforma é o menor dos problemas; precisamos da inteligência que monta a meta". O prazo de 4 meses foi reiniciado a partir de 06/10.
2. A metodologia Out/26 especifica o motor inteiro (31 regras) com valores fechados. A EMENDA 01 tinha transcrito mal a de agosto (pesos por mês em vez de blocos, "G 40/60" e "IS por mediana" sem definição, blocos 9–10 ausentes).
3. O escopo passa a ser uma **intranet modular**: Metas primeiro, Logística depois, e uma camada de integração entre os dois.

## O que muda

| Antes | Depois |
|---|---|
| Fase 1 com fixtures sintéticas e CSV real bloqueado | Fase 1 roda **com dados reais** e reproduz a meta de Out/26 |
| Catálogo temporal (vigência na data da venda, RN-18) | DE→PARA **atual** aplicado a todo o histórico (M-04) |
| "Ausência de histórico nunca gera meta zero" (RN-12) | Introdução segue M-12/M-13 literalmente, inclusive meta zero |
| Granularidade linha × responsável × região | **Cliente × SKU** consolidado até Empresa (M-01, M-31) |
| Snapshot imutável com SHA-256, quarentena e exportação blindada no caminho crítico | Execução versionada simples (parâmetros + contagens + versão do motor); a governança pesada sai do caminho crítico |
| Logística fora do projeto | Módulo Logística na Fase 4 (descoberta começa em paralelo) |
| Potencial externo (Nielsen/Scanntech) como KPI | Fora do escopo atual; reabrir só por decisão do cliente |

## Tasks já concluídas e o destino de cada uma

| Task | Destino |
|---|---|
| T1.1 matriz papel×operação | **Aproveitada.** As operações são renomeadas na T1.2 (ver SPEC-1-001). |
| T2.1 contratos CSV sintéticos | **Aproveitada** como base dos contratos; os campos são revistos na T2.1c contra o dicionário real. |
| T2.1b contratos × metodologia ago/26 | **Aproveitada parcialmente.** `parametros_calculo` vira a tabela de parâmetros (SPEC-1-003). A regra "origem OFICIAL bloqueada" é retirada: dados e parâmetros oficiais agora são permitidos. |
| T4.1 catálogo temporal | **Aproveitada.** Tabelas de produtos, clientes e responsáveis são reaproveitadas; a vigência fica com um único período aberto (estrutura atual). As constraints não precisam ser removidas. |

## Tasks antigas canceladas

T1.3 (antiga), T2.2/T2.3 (staging com SHA), T3.1–T3.3 (quarentena e exportação), T4.2/T4.3 (resolução por vigência), T5.1–T5.3 (snapshot), T6.1–T6.3 (painel sintético). O que tinha valor foi absorvido nas novas tasks.

## Dúvidas de 02/10 — resolvidas por esta emenda

- **Sequência da T6.2 e fonte de verdade:** passa a valer apenas `04_fase-atual/matriz-specs-fases.md`, com nova ordem de levas.
- **Blocos 9–10 da metodologia:** resolvido pela metodologia Out/26 completa (M-01..M-31).
- **origem=OFICIAL em `parametros_calculo`:** a restrição deixa de existir.
- **T1.2 — campos e unicidade do ciclo:** definidos na SPEC-1-001. Ambiente e contas viram as perguntas Q-24/Q-25.

## Como as perguntas ao cliente funcionam

As perguntas em aberto **não bloqueiam o início das SPECs**. Cada SPEC lista as suas perguntas (`Q-xx`), já formuladas como confirmação de uma leitura provável. A task que depende de uma pergunta faz a pergunta, registra a resposta e implementa conforme ela. O protocolo está em `AGENTS.md`; o registro central fica em `03_documentos/perguntas-ao-cliente.md`.
