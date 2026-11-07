# Mensagem para a Kim — D1/D2/D3 (com as respostas do Alex anexadas)

**Para:** Kim
**De:** Paulo (via Alex)
**Assunto:** Fase 2 executada até onde não depende de você — faltam D1, D2 e D3

---

Kim, bom dia.

A Fase 2 foi liberada em 04/11 e já executamos **23 das 27 tasks** com prova automática (suíte 152/152). As levas A, B, C e a D estão implementadas e publicadas; as migrations estão aplicadas no Supabase do projeto. O registro completo está no changelog do repositório.

**Restam 4 tasks, e 3 delas dependem de você** — as dúvidas D1, D2 e D3 que abrimos em 31/10 e 01/11 durante o motor:

**D1 — A métrica do modelo VARIA POR REGIME (confirmar).**
A metodologia (regra 2) escreve uma única fórmula de venda líquida, mas o gabarito executa **duas**:
- PISO e INTRODUÇÃO usam `vlritens − vlrdesc` (sem troca);
- REGULAR_24M usa a líquida de **3 termos** (`vlritens − vlrdesc − vlrtroca`).

Prova: isolando 1.237 clientes puro-REGULAR, a mediana gabarito÷motor é **1,0009** com a líquida de 3 termos (398 clientes batem no centavo) contra **0,9306** com 2 termos (72 batem; viés sistemático de +7%). É isso mesmo, ou há uma terceira leitura? (E o Carrefour tem maturidade por loja? Medimos −0,22% por loja contra −0,33% por rede.)

**D2 — SKUs sem produto no universo.**
Os SKUs 141951 (131 pares no universo) e 2279 (1 par) são vendidos mas não existem na BASE_PRODUTOS. O gabarito parece contar só parte deles. Como o modelo trata: entram no universo ou ficam fora?

**D3 — Clientes "0" e "vazio" (confirmar).**
As 60 linhas que o contrato rejeita por V-02 (30 com `codcli=0` = R$ 50.002,93 e 30 com `codcli` vazio = R$ 41.931,62) **não são lixo**: a aba Auditoria Estrutura do gabarito traz o código 0 como cliente real com venda de exatamente R$ 50.002,93. Confirmamos que entram no universo? (A leitura provável já está aplicada: entram.)

---

**Para agilizar, o Alex já respondeu as 8 perguntas que estavam no nome dele (06/11, aprovado pelos dados — leituras prováveis aplicadas):**

- **Q-09**: dias úteis = seg–sex **sem** descontar feriados (Out/26 = 22);
- **Q-16**: Assaí sem Pão de Leite elegível → **cria a combinação no SKU 5**;
- **Q-20**: arredonda **HALF_UP a 2 casas no Cliente × SKU**; o resíduo vai para a maior combinação;
- **Q-22**: layout da exportação = **o mesmo da Meta 07-2026** (aba por promotor + resumo por supervisor) — já gravado no P-18;
- **Q-39**: piso técnico **só quando a Meta Teórica ≤ 0**;
- **Q-40**: GAP sem combinação válida **migra para a outra linha** do mesmo responsável;
- **Q-41**: os clientes sem estrutura ficam **fora de tudo** (universo e Meta Original);
- **Q-42**: a média 29,4832% é o **share Especial da empresa no Direto, Abr–Set/26** — e fica como **parâmetro** (nenhum candidato reproduz o valor exato).

Com D1/D2/D3 respondidas, destravamos a T2.1.5 (validação paralela de Nov/26 — sistema × processo atual) e a T2.4.6 (publicação de Dez/26 antes do dia 1º, que é o critério bloqueante da fase).

Fico à disposição para qualquer detalhe.
