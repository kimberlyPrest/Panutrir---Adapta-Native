# PRD — Intranet Panutrir: Metas Comerciais e Logística

**Versão:** 1.0 — reset do programa (EMENDA 02/2026)  
**Data:** 20/10/2026  
**Patrocinador:** Alex · **Dono do projeto:** Paulo · **Implementação:** Léo · **Champion operacional:** Ângelo  
**Adapta:** Kim (consultora) · Matheus (CSM)  
**Fonte do cálculo:** `06_notas/2026-10-20-metodologia-oficial-out-2026.md` (M-01..M-31, gabarito G-01..G-19, parâmetros P-01..P-16)

## 1. Problema

A meta mensal é montada em planilhas pelo Gerente Nacional, olhando 3 meses e ajustando percentuais à mão. Ela sai até o dia 5 do mês, repete o comportamento de curto prazo (Paulo: "se o curto prazo está ruim, faço metas baixas"), não fecha naturalmente com a ambição da Diretoria e não é explicável linha a linha. A logística tem o mesmo padrão: cada CD monta cargas na sua planilha, sem padrão, com custo de frete alto e entregas deixadas de fazer para economizar.

## 2. Objetivo

Uma intranet modular no mesmo Supabase:

1. **Metas** — o sistema calcula a meta Cliente × SKU pela metodologia oficial, fecha com a Meta Diretoria, consolida até a Empresa, explica cada número e publica para a equipe.
2. **Logística** — montagem de cargas de menor custo respeitando prazo e capacidade, a partir do CD modelo.
3. **Integração** — a meta vira previsão de volume por CD, e a IA explica e sugere com aceite humano.

## 3. Indicadores de sucesso

| KPI | Definição | Baseline | Alvo |
|---|---|---|---|
| K1 — Meta reproduzível | ciclos publicados cuja execução reconcilia (somas em todos os níveis; Out/26 também contra o gabarito) ÷ ciclos publicados | não existe | 100% (zero ciclos = inconclusivo) |
| K2 — Prazo de publicação | data da publicação × início do mês da meta | até o dia 5 do mês | Q-28 (proposta: antes do 1º dia do mês) |
| K3 — Esforço do ciclo | horas humanas para produzir a meta do mês | medir em Nov/26 (paralelo) | combinar após o baseline |
| K4 — Custo logístico | custo logístico ÷ faturamento no CD modelo | SPEC-4-001 | combinar após o baseline |
| K5 — Nível de serviço | entregas realizadas ÷ solicitadas no CD modelo | SPEC-4-001 | combinar após o baseline |

## 4. Usuários

- **Diretoria / Paulo:** define a Meta Diretoria e o crescimento, compara cenários, aprova e publica.
- **Léo / Ângelo (Inteligência de Vendas):** carregam bases, mantêm estrutura e parâmetros, executam o cálculo e explicam.
- **Supervisores e promotores:** consultam a própria meta e o acompanhamento (Fase 2+).
- **Logística (Marcelo e CDs):** planejam cargas (Fase 4+).

## 5. Requisitos funcionais

| ID | Requisito | Fase | SPEC |
|---|---|---|---|
| RF-01 | Autenticação e papéis com matriz papel×operação | 1 | SPEC-1-001 |
| RF-02 | Ciclo mensal (um por mês) com status | 1 | SPEC-1-001 |
| RF-03 | Carga do histórico de vendas agregada por mês × cliente × SKU | 1 | SPEC-1-002 |
| RF-04 | Registro e auditoria de carga e de estrutura (linhas inválidas, clientes sem estrutura, SKU desconhecido) | 1 | SPEC-1-002, SPEC-1-004 |
| RF-05 | Parâmetros da metodologia versionados | 1 | SPEC-1-003 |
| RF-06 | Sortimento restrito, substituição e exclusões como regras por rede | 1–2 | SPEC-1-003, SPEC-2-002 |
| RF-07 | Calendário (dias úteis, IS) e execução versionada reprodutível | 1 | SPEC-1-003 |
| RF-08 | Estrutura comercial atual (DE→PARA) e produtos (linha, Panettone) | 1 | SPEC-1-004 |
| RF-09 | Universo elegível e maturidade dos SKUs | 1 | SPEC-1-005 |
| RF-10 | Motor da Meta Original: 24M, introdução, piso e substituição | 1 | SPEC-1-005 |
| RF-11 | GAP da Diretoria e separação Indireto/Direto | 1 | SPEC-1-006 |
| RF-12 | Mix de linha, convergência dos Especiais e GAP por linha | 1 | SPEC-1-006 |
| RF-13 | Descida do GAP até Cliente × SKU e consolidações | 1 | SPEC-1-006 |
| RF-14 | Teste de reconciliação contra o gabarito | 1 | SPEC-1-007 |
| RF-15 | Painel de controles do ciclo com alertas (REVISAR, auditoria) | 1 | SPEC-1-007 |
| RF-16 | Consulta drill-down com memória de cálculo e exportação | 1 | SPEC-1-007 |
| RF-17 | Criação automática do ciclo seguinte (janelas deslizantes) | 2 | SPEC-2-001 |
| RF-18 | Edição de parâmetros e regras pela interface | 2 | SPEC-2-002 |
| RF-19 | Simulação e comparação de cenários | 2 | SPEC-2-003 |
| RF-20 | Aprovação e publicação com versão imutável | 2 | SPEC-2-004 |
| RF-21 | Consulta por perfil (supervisor, promotor, Diretoria) | 2 | SPEC-2-004 |
| RF-22 | Entrega ao Metabase e medição do prazo (K2) | 2 | SPEC-2-004 |
| RF-23 | Realizado × meta com projeção de fechamento | 3 | SPEC-3-001 |
| RF-24 | Indicadores de trocas e visitas | 3 | SPEC-3-002 |
| RF-25 | Diagnósticos gerenciais (piso por promotor, REVISAR, Key Accounts) | 3 | SPEC-3-003 |
| RF-26 | Simulação de ROI promocional (opcional) | 3 | SPEC-3-004 |
| RF-27 | Descoberta da logística e modelo de referência | 4 (paralelo à 1) | SPEC-4-001 |
| RF-28 | Cadastro logístico | 4 | SPEC-4-002 |
| RF-29 | Montagem de cargas de menor custo | 4 | SPEC-4-003 |
| RF-30 | Meta → volume por CD → capacidade | 5 | SPEC-5-001 |
| RF-31 | IA assistiva para explicar e sugerir | 5 | SPEC-5-002 |

## 6. Regras de negócio

- **RN-01:** a metodologia oficial vigente (hoje Out/26) é a fonte do cálculo. Todo número dela é parâmetro versionado; nenhum fica escrito no código.
- **RN-02:** toda execução registra versão de parâmetros, versão do motor, cargas usadas e autor.
- **RN-03:** a estrutura comercial atual vale para todo o histórico (M-04).
- **RN-04:** só uma execução reconciliada pode ser aprovada e publicada.
- **RN-05:** versão publicada é imutável; correção gera nova versão com motivo.
- **RN-06:** a IA não altera, aprova nem publica metas.
- **RN-07:** sem ajuste manual do número final em nenhum nível (M-31). Mudanças entram por parâmetro ou regra, salvo decisão diferente em Q-27.
- **RN-08:** não inferir responsável nem criar promotor fictício (M-25, M-27).
- **RN-09:** REVISAR (< R$300) é alerta, não altera a meta (M-26).
- **RN-10:** a regra de introdução é literal, inclusive meta zero quando o último mês é zero (M-13). Revoga a antiga RN-12.
- **RN-11:** dados reais ficam só no Supabase do projeto. Nenhuma base, extrato ou amostra real em repositório.
- **RN-12:** dúvida de regra é perguntada ao cliente e a resposta é registrada **antes** de implementar a parte que depende dela. Nunca presumir.
- **RN-13:** visitas realizadas não são inferidas do roteiro.
- **RN-14:** resultado de campanha é associação, não causalidade.
- **RN-15:** o sistema não calcula remuneração variável.

## 7. Requisitos não funcionais

- **RNF-01 Segurança:** menor privilégio, RLS deny-by-default, nenhuma senha ou segredo em código.
- **RNF-02 Privacidade:** dados de clientes e colaboradores protegidos; exportações sanitizadas.
- **RNF-03 Auditoria:** append-only para carga, parâmetro, execução, aprovação, publicação, exportação e IA.
- **RNF-04 Integridade:** cargas idempotentes por mês; execuções nunca sobrescritas.
- **RNF-05 Explicabilidade:** todo número publicado tem memória de cálculo até a venda mensal de origem.
- **RNF-06 Portabilidade:** dados, schema e migrations exportáveis em formato aberto.
- **RNF-07 Desempenho:** execução completa de um ciclo em menos de 15 minutos; consultas do painel em menos de 3 segundos.
- **RNF-08 Disponibilidade:** falha da IA não impede cálculo, aprovação ou consulta.
- **RNF-09 Infraestrutura:** Supabase sem pausa por inatividade e com espaço para o histórico (Q-25).

## 8. Fora do escopo

Substituir SAP ou Metabase; calcular remuneração; potencial externo (Nielsen/Scanntech), que só reabre por decisão do cliente; CRM e funil comercial (frente com a V4); S&OP e planejamento de produção.

## 9. Dependências e riscos

| Risco | Efeito | Mitigação |
|---|---|---|
| Perguntas Q-xx sem resposta | parte da regra não implementada | perguntas já prontas, com leitura provável; o gabarito ajuda a decidir |
| Gabarito não reproduzido | Fase 1 não fecha | testar regime a regime (G-11..G-16) antes do total |
| Supabase gratuito (pausa, 500 MB) | perda de disponibilidade; carga não cabe | agregar por mês; Pro (Q-25) |
| Repositórios públicos no GitHub | exposição de dados e regras do cliente | tornar privados antes do próximo push |
| Logística sem definição | Fase 4 atrasa | descoberta começa já, em paralelo à Fase 1 |
