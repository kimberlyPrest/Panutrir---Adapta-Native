# Perguntas ao cliente — registro central

**Critério:** só entra aqui pergunta cuja resposta **muda o que é implementado**: uma regra de cálculo, o mapeamento de um dado ou o formato de uma saída. Se a resposta já está na metodologia, nos dados ou nos papéis definidos, ou se não altera o sistema, não se pergunta.

As perguntas **não bloqueiam o início** das SPECs. A task indicada pergunta quando chega na parte que depende da resposta, registra a resposta aqui e na SPEC e implementa conforme ela (protocolo em `AGENTS.md`). A leitura provável serve para o cliente confirmar ou corrigir; ela **não é implementada sem confirmação**.

**Status:** `aberta` → `perguntada` (data) → `respondida` (data, quem, resposta literal).

## Fase 1 — motor de meta

| ID | SPEC / task | Para | Pergunta (enviar como está) | Leitura provável | Status | Resposta |
|---|---|---|---|---|---|---|
| Q-04 | SPEC-1-004 / T4.2 | Ângelo | Pode enviar o DE→PARA atual (cliente → supervisor, promotor, canal e rede)? A rede (ex.: Assaí SP) vem desse arquivo, e cada loja é um código de cliente? | Sim; rede vazia ou "Clientes" = cliente avulso. | aberta | |
| Q-07 | SPEC-1-004 / T4.3 | Ângelo | O que torna um supervisor "válido" (M-27)? Existe uma lista de supervisores ativos? | Supervisor presente na lista ativa; código vazio ou desligado é inválido. | aberta | |
| Q-08 | SPEC-1-003 / T3.2 | Paulo | Como se calcula o Índice Sazonal: um índice por mês para a empresa toda, ou por linha/cliente? Qual janela e método? Pode enviar a tabela de IS dos 12 meses? | Um IS por mês-calendário para a empresa, enviado pronto (Out = 1,0319). | aberta | |
| Q-09 | SPEC-1-003 / T3.2 | Paulo | Os 22 dias úteis de Out/26 são seg–sex sem descontar feriados? Os meses do histórico usam a mesma regra? | Seg–sex sem feriados (Out/26 tem 22 dias de seg–sex, e o feriado de 12/10 não foi descontado). | aberta | |
| Q-10 | SPEC-1-003 / T3.1 | Paulo | O G de 2,591659% é informado pela Diretoria a cada mês ou calculado? Se calculado, como? | **Calculado** — a leitura provável anterior ("informado a cada ciclo") foi corrigida pelo cliente | respondida (24/10/2026, Alex) | "Calculado" |
| Q-12 | SPEC-1-005 / T5.2 | Paulo | Na dessazonalização (M-08), cada mês histórico é dividido pelo IS do seu próprio mês-calendário? | Sim. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — IS do próprio mês-calendário; motor reproduz o gabarito (T3.2 calcula o IS histórico) |
| Q-13 | SPEC-1-005 / T5.2 | Paulo | A média de cada bloco (M-09) é simples sobre todos os meses (6, 6 e 12), com mês sem venda contando como zero? Meses negativos entram? | Sim, zero incluído e negativo mantido. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — média simples, zero incluído e negativo mantido; motor com 895/2157 clientes batendo no centavo |
| Q-14 | SPEC-1-005 / T5.3 | Paulo | Os 12 meses (M-12) contam da primeira venda do SKU na rede (ou no cliente, se avulso)? O primeiro mês de meta é o seguinte à primeira venda? | Sim nas duas. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — 12 meses da 1ª venda na REDE (cliente se avulso), híbrido M-12: 2.618/2.739 introduções idênticas ao gabarito |
| Q-15 | SPEC-1-005 / T5.2 | Paulo | Meta Teórica negativa é zerada? | Sim. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — zerada; o piso dispara quando meta_teorica ≤ 0 (prova CA-1-16) |
| Q-16 | SPEC-1-005 / T5.5 | Paulo | Se a loja Assaí SP não tem Pão de Leite elegível, a transferência cria a combinação ou se perde? O Pão de Leite é o SKU 5? | Cria a combinação no SKU 5. | aberta | |
| Q-17 | SPEC-1-006 / T6.1 | Paulo | Em M-20, "responsável" é o supervisor? | Sim. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — supervisor; e o canal Indireto é responsável próprio (6 clientes); GAP Direto reproduz 16/16 supervisores no centavo |
| Q-18 | SPEC-1-006 / T6.2 | Paulo | Na convergência (M-22), a "unidade" é o responsável, com o share calculado pela venda líquida Abr–Set? | Sim nas duas. | respondida (02/11/2026, Alex — aprovado pelos dados) | Sim — unidade = promotor (cliente sem promotor é unidade própria), share pela VL líquida Abr–Set; M-22/M-23 reproduzem 123/123 no centavo |
| Q-19 | SPEC-1-006 / T6.2 | Paulo | Como o GAP do Indireto (R$279.624,72) se divide entre Branca e Especiais? | Pelo share atual do próprio Indireto, sem convergência. | respondida (02/11/2026, Alex — aprovado pelos dados) | Share próprio do Indireto, SEM convergência — confirmado: os 6 clientes Indireto do gabarito não convergem (share_GAP = share) |
| Q-20 | SPEC-1-006 / T6.1 | Paulo | O GAP Direto da planilha é R$1.018.571,54, mas a conta dá ,55. Onde arredondar e para onde vai o resíduo? | Arredonda em centavos no Cliente × SKU; o resíduo vai para a maior combinação. | aberta | |
| Q-21 | SPEC-1-007 / T7.1 | Paulo | Pode enviar a planilha de resultado Out/26 linha a linha (Cliente × SKU)? O que é o "benchmark corporativo" do +0,157%? | A planilha existe; o benchmark é a média recente da empresa projetada. | aberta | |
| Q-22 | SPEC-1-007 / T7.4 | Paulo | Em que layout a meta precisa sair para o Metabase e para os supervisores? | O mesmo da "Meta 07-2026" (aba por promotor + resumo por supervisor). | aberta | |
| Q-39 | SPEC-1-005 / T5.4 | Paulo | O piso técnico (M-14) entra só quando a Meta Teórica fica ≤ 0, ou sempre que ela é menor que o piso? | Só quando ≤ 0. | aberta | |
| Q-40 | SPEC-1-006 / T6.3 | Paulo | Se um responsável recebe GAP numa linha em que todas as suas combinações têm Meta Original zero, para onde vai esse GAP? | Para a outra linha do mesmo responsável. | aberta | |
| Q-41 | SPEC-1-005 / T5.1 | Paulo | Os 27 clientes sem estrutura ficam fora das 29.003 combinações e da Meta Original, ou só fora da distribuição do GAP? | Fora de tudo. | aberta | |
| Q-42 | SPEC-1-006 / T6.2 | Paulo | A média de 29,4832% é o share Especial da empresa (só Direto?) ou a média simples dos shares dos responsáveis? | Share da empresa no Direto, Abr–Set/26. | aberta | |

### Desdobramento da Q-10 (aberta, não bloqueia a T3.1)

| ID | SPEC / task | Para | Pergunta | Situação |
|---|---|---|---|---|
| Q-10b | SPEC-1-005 / T5.2 | Paulo / Kim | **Como** o G é calculado? A fórmula 40% × G histórico + 60% × G últimos 6 meses existe só no modelo de **ago/26** (itens 4.1–4.3), que a EMENDA 02 superou. O `M-11` de Out/26 apenas fixa o valor do mês e não define o cálculo. | aberta — sem essa resposta a T5.2 usaria G fixo, que só serve para Out/26 |

## Fase 3
