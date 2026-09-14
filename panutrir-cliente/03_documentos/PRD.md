# PRD — Sistema Inteligente de Metas Comerciais Panutrir

**Versão:** 0.1 — minuta para aprovação  
**Data:** 2026-09-14  
**Champion operacional:** Ângelo (tema metas)  
**Patrocinadores e usuários-chave:** Diretoria, Inteligência de Vendas, Gerência Nacional, Supervisores e Key Accounts.

## 1. Problema

O ciclo mensal de metas depende de planilhas, cruzamentos manuais, versões paralelas e decisões pouco rastreáveis. O histórico de vendas, metas, atingimentos, produtos, responsáveis e regiões não está consolidado em uma base governada. Isso atrasa a liberação, dificulta explicar a origem da meta e impede medir com segurança a efetividade de campanhas.

## 2. Objetivo do produto

Disponibilizar um sistema que transforme dados comerciais homologados em ciclos de metas simuláveis, explicáveis, aprováveis e acompanháveis, preservando decisão humana e trilha de auditoria.

## 3. Critérios de sucesso

| KPI | Definição operacional proposta | Regra de medição |
|---|---|---|
| K1 — Metas rastreáveis | Percentual de metas publicadas reais com versão, fonte, fórmula, parâmetros, ajustes, justificativa e aprovador identificáveis. | metas publicadas reais rastreáveis ÷ total de metas publicadas reais; alvo: 100%. Se o denominador for zero, resultado é **inconclusivo**, nunca 100%. Fixture prova capacidade, não o KPI. |
| K2 — Meta disponível até D-1 | Percentual de ciclos elegíveis cuja versão oficial foi publicada até 23:59 do último dia anterior ao início do ciclo. | ciclos publicados até D-1 ÷ ciclos elegíveis iniciados no período. Todo ciclo iniciado entra no denominador, independentemente de encerramento. A F1 registra baseline provisório do processo; baseline oficial exige G1/G2 e operação real. Atraso técnico e atraso de aprovação humana são medidos separadamente. |
| K3 — Captura de potencial | Critério do briefing condicionado ao G6. Com fonte externa homologada: potencial incorporado ao cenário ÷ potencial elegível da fonte, com granularidade e exclusões congeladas. | Sem G6, K3 oficial permanece **inconclusivo** e não pode ser substituído silenciosamente. Proxies internos são indicadores separados: histórico por janela, clientes sem compra por janela, abertura e lançamentos, cada um com fórmula homologada. |
| K4 — Efetividade de campanhas | Indicador exploratório sem meta contratada até G7. Mede campanhas analisáveis e associação observada segundo desenho aprovado. | Não usar “incremental” ou causalidade sem contrafactual válido. Exibir método, cobertura de chaves, comparação, limitações e classificação conclusiva/inconclusiva; “confiança” só aparece com método estatístico declarado. |

## 4. Usuários e necessidades

- **Diretoria:** informar ambição financeira, comparar cenários e aprovar a versão oficial.
- **Inteligência de Vendas:** carregar e sanear dados, parametrizar regras, simular e explicar resultados.
- **Gerência/Supervisão:** revisar metas por território/equipe, registrar exceções e justificar ajustes.
- **Key Accounts:** consultar metas e desempenho por rede/carteira.
- **Ângelo/champion:** operar o ciclo, coordenar pendências e validar evidências.

## 5. Fluxo crítico

1. Criar ciclo mensal em preparação.
2. Importar bases homologadas e emitir diagnóstico de qualidade.
3. Congelar snapshot histórico e parâmetros do ciclo.
4. Calcular cenário base determinístico e consolidar hierarquias.
5. Registrar exceções e simular cenários top-down x bottom-up.
6. Submeter, devolver, aprovar e publicar versão imutável.
7. Acompanhar atingimento, visitas homologadas, trocas e campanhas.
8. Gerar recomendações assistivas com explicação, sempre sujeitas a aceite humano.

## 6. Requisitos funcionais

- **RF-01:** autenticar usuários e aplicar papéis mínimos de operação, revisão, aprovação e consulta.
- **RF-02:** criar e gerir ciclos mensais com estados preparação, revisão, aprovado, publicado e encerrado.
- **RF-03:** importar CSVs de vendas, metas/atingimentos, produtos e estrutura comercial com mapeamento de colunas.
- **RF-04:** validar schema, tipos, duplicidades, chaves, períodos e consistência referencial antes da carga.
- **RF-05:** emitir relatório de qualidade e quarentena sem alterar silenciosamente dados inválidos.
- **RF-06:** manter catálogo canônico e temporal de produtos, linhas, clientes, redes, regiões, supervisores, promotores/vendedores e Key Accounts, preservando vigência das atribuições no período da venda.
- **RF-07:** versionar arquivos, transformações, snapshots e parâmetros usados em cada ciclo.
- **RF-08:** apresentar painel de baseline com cobertura temporal, qualidade e tempos do processo atual.
- **RF-09:** gerar simulação demonstrável usando dados sintéticos quando o CSV real não estiver homologado.
- **RF-10:** calcular meta base determinística com fórmula e parâmetros versionados.
- **RF-11:** consolidar metas por produto, linha, cliente/rede, promotor, supervisor, região, Key Account e total.
- **RF-12:** registrar exceções de mix, deslistagem, abertura/fechamento, férias, vacância, mudança de carteira e ausência de histórico.
- **RF-13:** modelar abertura de clientes e lançamentos como dimensões configuráveis, sem fórmula presumida.
- **RF-14:** calcular visitas planejadas a partir de calendário e roteiro homologados.
- **RF-15:** reconciliar cenário bottom-up com meta financeira top-down, expondo gap absoluto e percentual.
- **RF-16:** comparar cenários e explicar contribuição de cada ajuste.
- **RF-17:** alertar metas inviáveis, dados incompletos, inconsistências hierárquicas e valores fora de política.
- **RF-18:** implementar workflow de submissão, devolução, aprovação e publicação, com SLA por etapa, responsável substituto e escalação; atraso técnico e atraso humano ficam separados.
- **RF-19:** tornar versão publicada imutável; revisão exige nova versão e vigência.
- **RF-20:** disponibilizar consulta da meta oficial conforme o perfil.
- **RF-21:** acompanhar vendas, atingimento, trocas e visitas quando suas fontes estiverem homologadas.
- **RF-22:** cadastrar campanhas com hipótese, período, público, produtos, regiões e custo quando disponível.
- **RF-23:** comparar desempenho de campanhas com baseline/regra de atribuição homologada e explicitar limitações.
- **RF-24:** gerar recomendações assistivas de cenário e justificativas com fontes, premissas e confiança.
- **RF-25:** permitir aceitar, editar ou rejeitar recomendação de IA, exigindo justificativa, antes/depois e decisão humana auditada.
- **RF-26:** exportar versão, memória de cálculo, pendências e evidências em formato auditável.

## 7. Regras de negócio

- **RN-01:** nenhuma meta produtiva pode ser calculada sobre fonte não homologada.
- **RN-02:** todo cálculo deve registrar fórmula, período, parâmetros, snapshot e versão do catálogo.
- **RN-03:** alteração manual exige autor, data, justificativa, antes/depois e escopo afetado.
- **RN-04:** publicação é bloqueada enquanto houver erro grave de qualidade sem exceção aprovada.
- **RN-05:** versão publicada é imutável; correção gera nova versão.
- **RN-06:** recomendações de IA não aprovam nem publicam metas.
- **RN-07:** Nielsen/Scanntech só entram no cálculo após homologação de acesso, granularidade, atualização e licença de uso.
- **RN-08:** remuneração variável e sua exibição ficam fora do produto inicial até fonte, dono e versão da política serem formalmente homologados.
- **RN-09:** o calendário de visitas é configurável por ciclo e sua política precisa ser aprovada antes do uso produtivo.
- **RN-10:** visitas realizadas não podem ser inferidas de roteiro planejado.
- **RN-11:** campanhas mostram associação/atribuição segundo regra declarada; não afirmar causalidade sem desenho que a sustente.
- **RN-12:** ausência de histórico gera pendência e fluxo humano, nunca meta zero automática.
- **RN-13:** proxies internos de potencial devem ser apresentados separadamente de potencial externo.
- **RN-14:** valores negativos, divisões inválidas, chaves órfãs e duplicidades críticas vão para quarentena.
- **RN-15:** o sistema deve permitir reproduzir qualquer cenário publicado a partir das evidências versionadas.
- **RN-16:** denominador zero torna KPI inconclusivo; nunca aprovado por vacuidade.
- **RN-17:** todo ciclo elegível iniciado entra no denominador de K2; cancelamento exige motivo e permanece visível.
- **RN-18:** associações históricas usam a carteira vigente na data da venda; ausência de vigência vira pendência, não atribuição atual retroativa.

## 8. Requisitos não funcionais

- **RNF-01 Segurança:** menor privilégio, autenticação, controle por papel e segregação entre preparação e aprovação.
- **RNF-02 Privacidade:** proteger dados pessoais comerciais; definir retenção e mascarar evidências compartilhadas.
- **RNF-03 Auditoria:** logs append-only para carga, parâmetro, ajuste, aprovação, publicação, exportação e uso de IA.
- **RNF-04 Integridade:** importações idempotentes e snapshots imutáveis por ciclo.
- **RNF-05 Explicabilidade:** todo número publicado deve ser rastreável até fonte e transformação.
- **RNF-06 Portabilidade:** exportar dados, schema e configurações em formatos abertos; documentar RLS, migrations e dependências específicas do Supabase.
- **RNF-07 Desempenho:** filtros e consolidações do ciclo-piloto devem responder em tempo adequado à operação, com orçamento definido após volume real.
- **RNF-08 Disponibilidade:** falha de IA não pode impedir cálculo, revisão, aprovação ou consulta determinísticos.
- **RNF-09 Observabilidade:** registrar falhas de importação, cálculo e integração com correlação por execução.
- **RNF-10 Recuperação:** permitir reversão de configuração e restauração de snapshot sem apagar histórico.
- **RNF-11 Escala:** o G1 deve validar volume representativo, incluindo a maior base conhecida, com orçamento de tempo/memória e comportamento de falha.

## 9. Fora do escopo

- Otimização logística, roteirização de frota e S&OP.
- Substituição do SAP, Metabase ou sistemas operacionais de venda.
- Definição autônoma de metas ou remuneração pela IA.
- Revisão da política de remuneração.
- Implantação de sensores ou novas fontes pagas de mercado.
- Disparo de campanhas ou automação de marketing; o escopo mede efetividade.

## 10. Dependências e riscos

- CSV histórico mar/2022–ago/2026 com supervisor, promotor/vendedor, região, cliente, produto, data, quantidade/valor e chaves consistentes — **pré-condição da carga real**.
- Fonte oficial de vendas/trocas precisa ser homologada antes do baseline oficial.
- Nielsen/Scanntech podem ser indisponíveis; fallback são proxies internos rotulados.
- Política de visitas e origem de realizado precisam de decisão antes da Fase 3/4.
- Regras de negócio podem mudar durante a construção; devem ser versionadas e nunca embutidas sem trilha.

## 11. Arquitetura de decisão

Supabase é a plataforma oficial aprovada: Postgres para dados, Auth para autenticação, RLS para autorização, Storage para arquivos sintéticos e migrations versionadas para schema/políticas. O núcleo de cálculo será determinístico e independente da IA. A Fase 1 usa apenas fixtures sintéticas; CSVs reais entram somente após revalidação posterior. A portabilidade será provada por migrations, exportação de dados/schema e documentação das políticas.