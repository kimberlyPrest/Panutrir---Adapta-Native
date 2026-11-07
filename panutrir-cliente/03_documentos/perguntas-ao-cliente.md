# Perguntas ao cliente — registro central

**Critério:** só entra aqui pergunta cuja resposta **muda o que é implementado**: uma regra de cálculo, o mapeamento de um dado ou o formato de uma saída. Se a resposta já está na metodologia, nos dados ou nos papéis definidos, ou se não altera o sistema, não se pergunta.

As perguntas **não bloqueiam o início** das SPECs. A task indicada pergunta quando chega na parte que depende da resposta, registra a resposta aqui e na SPEC e implementa conforme ela (protocolo em `AGENTS.md`). A leitura provável serve para o cliente confirmar ou corrigir; ela **não é implementada sem confirmação**.

**Status:** `aberta` → `perguntada` (data) → `respondida` (data, quem, resposta literal).

## Fase 1 — motor de meta

| ID | SPEC / task | Para | Pergunta (enviar como está) | Leitura provável | Status | Resposta |
|---|---|---|---|---|---|---|
| Q-04 | SPEC-1-004 / T4.2 | Ângelo | Pode enviar o DE→PARA atual (cliente → supervisor, promotor, canal e rede)? A rede (ex.: Assaí SP) vem desse arquivo, e cada loja é um código de cliente? | Sim; rede vazia ou "Clientes" = cliente avulso. | aberta | |
| Q-07 | SPEC-1-004 / T4.3 | Ângelo | O que torna um supervisor "válido" (M-27)? Existe uma lista de supervisores ativos? | Supervisor presente na lista ativa; código vazio ou desligado é inválido. | aberta | |
| Q-08 | SPEC-1-003 / T3.2 | Paulo | Como se calcula o Índice Sazonal: um índice por mês para a empresa toda, ou por linha/cliente? Qual janela e método? Pode enviar a tabela de IS dos 12 meses? | Um IS por mês-calendário para a empresa, enviado pronto (Out = 1,0319). | respondida (30/10/2026, Alex) | "Índice Sazonal está na aba Metodologia" — a regra da seção 8 calcula o IS histórico; Out/26 usa o valor informado P-05 (1,0319) |
| Q-09 | SPEC-1-003 / T3.2 | Paulo | Os 22 dias úteis de Out/26 são seg–sex sem descontar feriados? Os meses do histórico usam a mesma regra? | Seg–sex sem feriados (Out/26 tem 22 dias de seg–sex, e o feriado de 12/10 não foi descontado). | respondida (06/11/2026, Alex — aprovado pelos dados; leitura provável aplicada) | Sim — seg–sex sem descontar feriados; os meses do histórico usam a mesma regra (22 dias úteis em Out/26 conferidos) |
| Q-10 | SPEC-1-003 / T3.1 | Paulo | O G de 2,591659% é informado pela Diretoria a cada mês ou calculado? Se calculado, como? | **Calculado** — a leitura provável anterior ("informado a cada ciclo") foi corrigida pelo cliente | respondida (24/10/2026, Alex) | "Calculado" |
| Q-12 | SPEC-1-005 / T5.2 | Paulo | Na dessazonalização (M-08), cada mês histórico é dividido pelo IS do seu próprio mês-calendário? | Sim. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — IS do próprio mês-calendário; motor reproduz o gabarito (T3.2 calcula o IS histórico) |
| Q-13 | SPEC-1-005 / T5.2 | Paulo | A média de cada bloco (M-09) é simples sobre todos os meses (6, 6 e 12), com mês sem venda contando como zero? Meses negativos entram? | Sim, zero incluído e negativo mantido. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — média simples, zero incluído e negativo mantido; motor com 895/2157 clientes batendo no centavo |
| Q-14 | SPEC-1-005 / T5.3 | Paulo | Os 12 meses (M-12) contam da primeira venda do SKU na rede (ou no cliente, se avulso)? O primeiro mês de meta é o seguinte à primeira venda? | Sim nas duas. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — 12 meses da 1ª venda na REDE (cliente se avulso), híbrido M-12: 2.618/2.739 introduções idênticas ao gabarito |
| Q-15 | SPEC-1-005 / T5.2 | Paulo | Meta Teórica negativa é zerada? | Sim. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — zerada; o piso dispara quando meta_teorica ≤ 0 (prova CA-1-16) |
| Q-16 | SPEC-1-005 / T5.5 | Paulo | Se a loja Assaí SP não tem Pão de Leite elegível, a transferência cria a combinação ou se perde? O Pão de Leite é o SKU 5? | Cria a combinação no SKU 5. | respondida (06/11/2026, Alex — aprovado pelos dados; leitura provável aplicada) | Sim — a transferência cria a combinação no SKU 5 (Pão de Leite); provado no motor (T5.5, substituição 81661→5) |
| Q-17 | SPEC-1-006 / T6.1 | Paulo | Em M-20, "responsável" é o supervisor? | Sim. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — supervisor; e o canal Indireto é responsável próprio (6 clientes); GAP Direto reproduz 16/16 supervisores no centavo |
| Q-18 | SPEC-1-006 / T6.2 | Paulo | Na convergência (M-22), a "unidade" é o responsável, com o share calculado pela venda líquida Abr–Set? | Sim nas duas. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — unidade = promotor (cliente sem promotor é unidade própria), share pela VL líquida Abr–Set; M-22/M-23 reproduzem 123/123 no centavo |
| Q-19 | SPEC-1-006 / T6.2 | Paulo | Como o GAP do Indireto (R$279.624,72) se divide entre Branca e Especiais? | Pelo share atual do próprio Indireto, sem convergência. | respondida (02/11/2026, Alex — aprovado pelos dados) | Share próprio do Indireto, SEM convergência — confirmado: os 6 clientes Indireto do gabarito não convergem (share_GAP = share) |
| Q-20 | SPEC-1-006 / T6.1 | Paulo | O GAP Direto da planilha é R$1.018.571,54, mas a conta dá ,55. Onde arredondar e para onde vai o resíduo? | Arredonda em centavos no Cliente × SKU; o resíduo vai para a maior combinação. | respondida (06/11/2026, Alex — aprovado pelos dados; leitura provável aplicada) | Sim — arredondamento HALF_UP a 2 casas no Cliente × SKU; o resíduo vai para a maior combinação (mediana gabarito÷motor = 0,9999) |
| Q-21 | SPEC-1-007 / T7.1 | Paulo | Pode enviar a planilha de resultado Out/26 linha a linha (Cliente × SKU)? O que é o "benchmark corporativo" do +0,157%? | A planilha existe; o benchmark é a média recente da empresa projetada. | respondida (04/11/2026, Alex — workbook enviado e conferência linha a linha executada; ver 06_notas/2026-11-04-q21-conferencia-gabarito.md) | Bug do GAP Indireto zerado na meta_linha achado e corrigido (106 linhas no Supabase) |
| Q-22 | SPEC-1-007 / T7.4 | Paulo | Em que layout a meta precisa sair para o Metabase e para os supervisores? | O mesmo da "Meta 07-2026" (aba por promotor + resumo por supervisor). | respondida (06/11/2026, Alex — aprovado pelos dados; leitura provável aplicada) | Sim — layout da Meta 07-2026: aba por promotor + resumo por supervisor (P-18 gravado com este layout; a leitura provável já estava na T7.4) |
| Q-39 | SPEC-1-005 / T5.4 | Paulo | O piso técnico (M-14) entra só quando a Meta Teórica fica ≤ 0, ou sempre que ela é menor que o piso? | Só quando ≤ 0. | respondida (06/11/2026, Alex — aprovado pelos dados; leitura provável aplicada) | Sim — o piso dispara só quando meta_teorica ≤ 0 (prova CA-1-16) |
| Q-40 | SPEC-1-006 / T6.3 | Paulo | Se um responsável recebe GAP numa linha em que todas as suas combinações têm Meta Original zero, para onde vai esse GAP? | Para a outra linha do mesmo responsável. | respondida (06/11/2026, Alex — aprovado pelos dados; leitura provável aplicada) | Sim — o GAP migra para a outra linha do mesmo responsável (leitura provável implementada na T6.3; zero casos no gabarito Out/26) |
| Q-41 | SPEC-1-005 / T5.1 | Paulo | Os 27 clientes sem estrutura ficam fora das 29.003 combinações e da Meta Original, ou só fora da distribuição do GAP? | Fora de tudo. | respondida (06/11/2026, Alex — aprovado pelos dados; leitura provável aplicada) | Sim — os clientes sem estrutura ficam fora do universo e da Meta Original (fonte autoritativa: aba Auditoria Estrutura do gabarito, 26 clientes) |
| Q-42 | SPEC-1-006 / T6.2 | Paulo | A média de 29,4832% é o share Especial da empresa (só Direto?) ou a média simples dos shares dos responsáveis? | Share da empresa no Direto, Abr–Set/26. | respondida (06/11/2026, Alex — aprovado pelos dados; leitura provável aplicada) | Sim — share Especial da empresa no Direto, Abr–Set/26 (a média 0,294832 fica como PARÂMETRO; nenhum candidato reproduz o valor exato — Q-42 permanece com o valor informado) |

### Desdobramento da Q-10 (aberta, não bloqueia a T3.1)

| ID | SPEC / task | Para | Pergunta | Situação |
|---|---|---|---|---|
| Q-10b | SPEC-1-005 / T5.2 | Paulo / Kim | **Como** o G é calculado? A fórmula 40% × G histórico + 60% × G últimos 6 meses existe só no modelo de **ago/26** (itens 4.1–4.3), que a EMENDA 02 superou. O `M-11` de Out/26 apenas fixa o valor do mês e não define o cálculo. | aberta — sem essa resposta a T5.2 usaria G fixo, que só serve para Out/26 |

## Fase 3

| ID | SPEC | Para | Pergunta | Leitura provável | Status | Resposta |
|---|---|---|---|---|---|---|
| Q-30 | SPEC-3-001 | Ângelo | Com que frequência e de qual fonte vem o realizado do mês corrente? | Diário, mesma exportação das congeladas. | aberta | |
| Q-31 | SPEC-3-002 | Ângelo | De onde vêm as visitas realizadas (app de check-in do promotor)? Em que formato conseguimos extrair? | App de check-in, exportação diária. | aberta | |
| Q-33 | SPEC-3-004 | Paulo | Temos custo por campanha e margem por SKU? (Sem esses dados o ROI promocional não é construído.) | Custo por campanha sim; margem por SKU no Aprix. | aberta | |

## Fase 4 — pauta da descoberta com o Marcelo

| ID | SPEC | Para | Pergunta | Leitura provável | Status | Resposta |
|---|---|---|---|---|---|---|
| Q-34 | SPEC-4-001 | Marcelo Néquio | Como cada CD monta cargas hoje e qual é o melhor modelo? | Cada um com sua planilha. | aberta | |
| Q-35 | SPEC-4-001 | Marcelo Néquio | Quais custos entram (frete terceiro, diesel, pernoite, pedágio) e onde estão esses valores? | Tabela de frete por freteiro e rota. | aberta | |
| Q-36 | SPEC-4-001 | Marcelo Néquio | Quais as regras de prazo (pedido + 72h) e as janelas por cliente? | 72h padrão, com exceções por rede. | aberta | |
| Q-37 | SPEC-4-001 | Marcelo Néquio | Qual a capacidade dos veículos (cubagem e peso) e de onde vêm os pedidos do dia? | Tipos fixos de veículo; pedidos do SAP. | aberta | |

## Perguntas retiradas em 20/10/2026

A resposta já é conhecida ou não muda a implementação. Fica valendo o que está na coluna "Decisão".

| ID | Assunto | Decisão |
|---|---|---|
| Q-01 | autorização para usar dados reais | Os dados foram enviados para isso; uso liberado no Supabase do projeto. |
| Q-02 | dicionário das colunas | Lido do cabeçalho das congeladas na T2.1c. Venda bruta = `vlritens`; conferido pelo G-11. |
| Q-03 | como chega o mês fechado | Mesma exportação das congeladas. |
| Q-05 | rede e loja | Incorporada à Q-04. |
| Q-06 | identificação de Panettone | Pela descrição/categoria da base de produtos; conferido pelo G-11. |
| Q-11 | quem informa a Meta Diretoria | Paulo. Não altera o sistema. |
| Q-23 | quem dá o aceite | Paulo. |
| Q-24 | quem opera, aprova e consulta | Léo e Ângelo operam; Paulo aprova; supervisores consultam na Fase 2. |
| Q-25 | plano do Supabase | Decisão de infraestrutura, não de implementação. A carga agregada por mês cabe no plano atual; o runbook de pausa cobre a indisponibilidade. |
| Q-26 | substituições em outras redes | A SPEC-2-002 já cria cadastro genérico por rede. |
| Q-27 | ajuste manual por exceção | M-31: sem ajuste manual; exceções entram por parâmetro ou regra. |
| Q-28 | prazo desejado de publicação | K2 é medido; meta proposta: publicar antes do 1º dia do mês. |
| Q-29 | rodar Nov/26 em paralelo | Faz parte da validação (SPEC-2-001). |
| Q-32 | piso de R$50 mil e Key Accounts | Vêm do mapeamento de processos; construídos como diagnóstico. |
| Q-38 | que explicações a IA deve dar | Definido na SPEC-5-002: explicar a meta e sugerir revisão das combinações REVISAR. |