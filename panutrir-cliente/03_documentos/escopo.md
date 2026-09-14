# Escopo definitivo — Panutrir

**Produto:** Sistema Inteligente de Metas Comerciais  
**Estado:** APROVADO pela consultora e pelo CSM em 14/09/2026.  
**Direção:** núcleo determinístico e explicável, com IA assistiva e decisão humana.

## 1. Resultado contratado

Ao final das cinco fases, a Panutrir terá um processo único para importar e governar dados comerciais, construir cenários de metas, reconciliar ambição financeira com histórico, aprovar/publicar uma versão oficial e acompanhar atingimento e efetividade de campanhas. Toda meta será reproduzível e explicável.

## 2. Entregas por capacidade

1. **Dados e baseline confiáveis:** carga controlada, quarentena, catálogo, snapshot e painel inicial.
2. **Motor e cenários:** cálculo determinístico, exceções, abertura/lançamentos, visitas planejadas e reconciliação.
3. **Governança da meta:** workflow, alçadas, versionamento, publicação imutável e consulta por perfil.
4. **Acompanhamento comercial:** atingimento, trocas, visitas homologadas e análise de campanhas.
5. **Inteligência assistiva:** recomendações explicáveis, aceite humano, monitoramento e estabilização.

## 3. Requisitos vinculantes

São vinculantes os RF-01 a RF-26, RN-01 a RN-18 e RNF-01 a RNF-11 definidos no PRD. Nenhuma fase pode reduzir rastreabilidade, explicabilidade ou decisão humana.

## 4. Estratégia de implementação

- Fase 1 usa exclusivamente fixtures sintéticas para demonstrar o fluxo; os CSVs reais já recebidos não serão usados nem compartilhados nesta fase.
- A carga produtiva e o baseline oficial ficam para revalidação posterior contra o schema real e a fonte oficial.
- O cálculo começa determinístico; IA não é dependência do caminho crítico.
- Integrações e fontes externas entram somente após prova de contrato, qualidade e permissão.
- SPECs são geradas em onda: somente a Fase 1 está detalhada neste corte.

## 5. Critérios globais

- **CG-01:** 100% das metas publicadas reais têm trilha completa; zero metas publicadas produz resultado inconclusivo.
- **CG-02:** uma versão publicada pode ser reproduzida com o snapshot e parâmetros preservados.
- **CG-03:** lote com erro grave mantém o estado anterior e gera pendência visível e log correlacionado; carga parcial é proibida.
- **CG-04:** nenhuma recomendação de IA altera meta sem decisão humana registrada.
- **CG-05:** cada KPI informa numerador, denominador, período, exclusões e fonte.

## 6. Fronteiras

O projeto não otimiza logística, não substitui ERP/BI, não redefine remuneração e não executa campanhas. Potencial externo e visitas realizadas dependem de fontes homologadas. O sistema pode preparar contratos de integração, mas não simular acesso inexistente.

## 7. Gates de execução

- **G0 — Arquitetura:** APROVADO — Supabase é a plataforma oficial da Fase 1. Auth, Postgres, RLS, Storage e migrations devem ser versionados e testados.
- **G1 — Dados (dono: Ângelo/cliente):** CSV completo recebido, schema e vigências conferidos, uso autorizado e volume representativo validado. O prazo original de 31/08 venceu. Plano B: avaliar a junção controlada das bases de vendas detalhadas e metas/atingimentos; se não preservar chaves e vigências, o baseline real permanece bloqueado. Revalidação das SPECs contra o schema real é obrigatória.
- **G2 — Fonte oficial (dono: Paulo/cliente):** decisão documentada entre fonte atual e futura, incluindo período de transição.
- **G3 — Segurança (donos: cliente + Adapta):** papéis, política de retenção e responsáveis aprovados.
- **G4 — Ciclo-piloto (donos: Ângelo + substituto a nomear pelo cliente):** mês, equipes, recortes, SLA de aprovação, substitutos e escalação definidos. O baseline provisório só é substituído após ciclo real elegível.
- **G5 — Visitas (dono: Gerência Comercial):** confirmar existência do roteiro estruturado, política do calendário e fonte do realizado antes de usar esse indicador; sem isso, RF-14 fica desligado.
- **G6 — Potencial externo (dono: cliente):** contrato/licença, acesso, granularidade, atualização, denominador e qualidade Nielsen/Scanntech comprovados. Sem G6, K3 oficial fica explicitamente inconclusivo e os proxies não o substituem.
- **G7 — Campanhas (donos: cliente + Adapta):** contrato mínimo define fonte de exposição, granularidade, período, produto/região, custo, chave de junção, cobertura mínima e regra analítica. Sem contrato suficiente, F4 entrega cadastro + acompanhamento e adia análise de efetividade.

## 8. Arquitetura aprovada

Supabase: Auth, Postgres, RLS, Storage e migrations versionadas. A Fase 1 usa exclusivamente fixtures sintéticas e não recebe os CSVs reais já disponíveis.