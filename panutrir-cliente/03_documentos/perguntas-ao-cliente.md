# Perguntas ao cliente — registro central

As perguntas **não bloqueiam o início** das SPECs. A task indicada faz a pergunta no momento em que precisa dela, registra a resposta aqui e na SPEC e implementa conforme a resposta (protocolo em `AGENTS.md`).

Cada pergunta traz uma **leitura provável** para o cliente confirmar ou corrigir. A leitura provável **não pode ser implementada sem confirmação**.

**Status:** `aberta` → `perguntada` (data) → `respondida` (data, quem, resposta literal).

## Fase 1

| ID | SPEC / task | Para | Pergunta (enviar como está) | Leitura provável | Status | Resposta |
|---|---|---|---|---|---|---|
| Q-01 | SPEC-1-002 / T2.1c | Paulo | Confirma que podemos carregar as bases reais de vendas (congeladas 2024–2026) no Supabase do projeto e que só usuários Panutrir autorizados terão acesso? | Sim, foi para isso que as bases foram enviadas. | aberta | |
| Q-02 | SPEC-1-002 / T2.1c | Ângelo ou Léo | Nas congeladas: quais colunas são código do cliente, código do SKU, data, `vlritens`, `vlrdesc`, `vlrtroca`, canal e rede? "Venda bruta positiva" (M-05) é `vlritens > 0`? | Venda bruta = `vlritens`; venda líquida = `vlritens − vlrdesc − vlrtroca`. | aberta | |
| Q-03 | SPEC-1-002 / T2.2 | Paulo | Como chega o mês fechado daqui para frente: quem exporta, de qual sistema (SAP?), em que formato e até que dia? | Exportação mensal do SAP em planilha, até o dia 2. | aberta | |
| Q-04 | SPEC-1-004 / T4.2 | Ângelo | Qual arquivo é o DE→PARA atual (cliente → supervisor/responsável, promotor, canal, rede) e quem o mantém? | Planilha mantida pela Inteligência de Vendas, atualizada até o dia 25. | aberta | |
| Q-05 | SPEC-1-004 / T4.2 | Ângelo | Como identificamos a rede e a loja (ex.: Assaí SP)? A "rede" vem do DE→PARA? "Loja" é o próprio código do cliente? | Rede vem do DE→PARA; cada loja é um código de cliente; rede vazia ou "Clientes" = cliente avulso. | aberta | |
| Q-06 | SPEC-1-004 / T4.2 | Ângelo | Como identificar Panettone: pela linha/categoria do produto ou por uma lista fixa de SKUs? | Pela descrição/categoria do produto contendo "PANETTONE". | aberta | |
| Q-07 | SPEC-1-004 / T4.3 | Ângelo | O que é "supervisor válido" (M-27)? Existe uma lista de supervisores ativos? | Supervisor presente na lista ativa da estrutura atual; código vazio ou desligado é inválido. | aberta | |
| Q-08 | SPEC-1-003 / T3.2 | Paulo | Como se calcula o Índice Sazonal (IS)? Um índice por mês do ano para a empresa toda, ou por linha/cliente? Qual janela e método (média ou mediana)? Pode mandar a tabela de IS dos 12 meses usada? | Um IS por mês-calendário para a empresa, mediana de 24 meses, enviado pronto em tabela (Out = 1,0319). | aberta | |
| Q-09 | SPEC-1-003 / T3.2 | Paulo | Dias úteis: seg–sex menos feriados nacionais? Feriados regionais contam? O histórico usa os dias úteis reais de cada mês? | Seg–sex menos feriados nacionais, um calendário único (Out/26 = 22). | aberta | |
| Q-10 | SPEC-1-003 / T3.1 | Paulo | O crescimento G (2,591659% em Out/26) é informado pela Diretoria a cada mês ou calculado? Se calculado, como? | Informado a cada ciclo como parâmetro. | aberta | |
| Q-11 | SPEC-1-003 / T3.1 | Paulo | Quem informa a Meta Diretoria do mês e até quando? | Paulo/Diretoria informa até o dia 20 do mês anterior. | aberta | |
| Q-12 | SPEC-1-005 / T5.2 | Paulo | Na dessazonalização (M-08), cada mês histórico é dividido pelo IS do seu próprio mês-calendário? | Sim: produtividade de Mar/25 ÷ IS de março. | aberta | |
| Q-13 | SPEC-1-005 / T5.2 | Paulo | A média de cada bloco (M-09) é simples sobre todos os meses do bloco (6, 6 e 12), contando meses sem venda como zero? Meses negativos entram? | Média simples de todos os meses do bloco, zero incluído, negativo mantido. | aberta | |
| Q-14 | SPEC-1-005 / T5.3 | Paulo | Os "12 meses na rede/cliente" (M-12) contam a partir da primeira venda do SKU na rede (ou no cliente, se avulso)? O "primeiro mês de meta" é o mês seguinte à primeira venda? | Sim nas duas. | aberta | |
| Q-15 | SPEC-1-005 / T5.2 | Paulo | Se a Meta Teórica de um Cliente×SKU sair negativa, ela é zerada? | Sim, piso em zero antes do piso técnico. | aberta | |
| Q-16 | SPEC-1-005 / T5.5 | Paulo | Substituição: se a loja Assaí SP não tiver Pão de Leite elegível, a transferência cria a combinação ou se perde? "Pão de Leite" é qual SKU? | Cria a combinação Pão de Leite (SKU 5) na loja. | aberta | |
| Q-17 | SPEC-1-006 / T6.1 | Paulo | M-20 "proporcional à Meta Original por responsável": responsável é o supervisor? | Sim, supervisor/responsável do DE→PARA. | aberta | |
| Q-18 | SPEC-1-006 / T6.2 | Paulo | Na convergência (M-22), a "unidade" é o responsável? O share de cada unidade usa a venda líquida Abr–Set? | Sim nas duas. | aberta | |
| Q-19 | SPEC-1-006 / T6.2 | Paulo | Como o GAP do Indireto (R$279.624,72) é dividido entre Branca e Especiais, já que a convergência vale só para o Direto? | Pelo share atual (Abr–Set) do próprio Indireto, sem convergência. | aberta | |
| Q-20 | SPEC-1-006 / T6.1 | Paulo | Arredondamento: a planilha mostra GAP Direto R$1.018.571,54, mas a conta dá ,55. Arredondamos em centavos só no Cliente×SKU e jogamos o resíduo no maior item? Qual diferença aceitamos? | Cálculo sem arredondar; arredonda em centavos no Cliente×SKU; resíduo vai para a maior combinação; tolerância de R$0,01 por total. | aberta | |
| Q-21 | SPEC-1-007 / T7.1 | Paulo | Pode mandar a planilha de resultado Out/26 linha a linha (Cliente × SKU com Meta Própria, Transferência, GAP e Meta Final)? E o que é o "benchmark corporativo" do +0,157%? | Planilha existe; benchmark = venda líquida média recente da empresa projetada. | aberta | |
| Q-22 | SPEC-1-007 / T7.4 | Paulo | Em que formato a meta precisa sair para o Metabase e para os supervisores (colunas, níveis, arquivo ou tabela)? | Planilha nos moldes de "Meta 07-2026" (aba por promotor e resumo por supervisor). | aberta | |
| Q-23 | SPEC-1-007 / T7.5 | Paulo | Quem dá o aceite final de que Out/26 foi reproduzido? | Paulo, com Léo. | aberta | |
| Q-24 | SPEC-1-001 / T1.2 | Paulo | Quem opera, quem aprova e quem só consulta? Nomes e e-mails para os papéis operador, aprovador e consulta. | Operador: Léo/Ângelo; aprovador: Paulo; consulta: supervisores (Fase 2). | aberta | |
| Q-25 | SPEC-1-001 / T1.2 | Paulo | O Supabase está no plano gratuito, que pausa por inatividade e tem limite de 500 MB. Podemos migrar para o Pro (≈US$25/mês) antes de carregar os dados reais? | Sim. | aberta | |
| Q-39 | SPEC-1-005 / T5.4 | Paulo | O piso técnico (M-14) entra só quando a Meta Teórica do motor fica ≤ 0, ou sempre que ela é menor que o piso? | Só quando a Meta Teórica ≤ 0 ("não pode ficar com meta zero"). | aberta | |
| Q-40 | SPEC-1-006 / T6.3 | Paulo | Se um responsável recebe GAP numa linha em que todos os seus Cliente × SKU têm Meta Original zero, para onde vai esse GAP? | Vai para a outra linha do mesmo responsável. | aberta | |
| Q-41 | SPEC-1-005 / T5.1 | Paulo | Os 27 clientes sem estrutura válida ficam fora das 29.003 combinações e da Meta Original, ou só fora da distribuição do GAP? | Ficam fora de tudo. | aberta | |
| Q-42 | SPEC-1-006 / T6.2 | Paulo | A média de 29,4832% é o share Especial da empresa (só Direto?) ou a média simples dos shares dos responsáveis? | Share da empresa no canal Direto, Abr–Set/26. | aberta | |

## Fase 2

| ID | SPEC | Para | Pergunta | Leitura provável | Status | Resposta |
|---|---|---|---|---|---|---|
| Q-26 | SPEC-2-002 | Paulo | Substituições e sortimentos restritos (como Assaí SP) vão se repetir em outras redes? | Sim; o sistema precisa cadastrar regras por rede. | aberta | |
| Q-27 | SPEC-2-004 | Paulo | M-31 diz "sem ajuste manual". Algum ajuste por exceção será permitido (férias, loja nova, vacância)? Com aprovação de quem? | Só por parâmetro/regra, nunca editando o número; exceção aprovada pelo Paulo. | aberta | |
| Q-28 | SPEC-2-004 | Paulo | Hoje a meta sai até o dia 5. Qual o prazo desejado? D-1? | Publicada até o último dia útil do mês anterior. | aberta | |
| Q-29 | SPEC-2-001 | Paulo | Podemos rodar Nov/26 em paralelo (sistema × planilha atual) para comparar? | Sim. | aberta | |

## Fase 3

| ID | SPEC | Para | Pergunta | Leitura provável | Status | Resposta |
|---|---|---|---|---|---|---|
| Q-30 | SPEC-3-001 | Ângelo | Com que frequência temos o realizado (diário/semanal) e de qual fonte? | Diário, mesma fonte das congeladas. | aberta | |
| Q-31 | SPEC-3-002 | Paulo | A regra de trocas (> 7% zera a variável) e a de visitas (≥ 80%) continuam valendo? Qual é a fonte das visitas realizadas (app do promotor)? | Continuam; visitas vêm do app de check-in. | aberta | |
| Q-32 | SPEC-3-003 | Paulo | O piso de R$50 mil por promotor e a visão de Key Accounts continuam relevantes? | Sim, como diagnóstico, sem alterar a meta. | aberta | |
| Q-33 | SPEC-3-004 | Paulo | A simulação de ROI promocional entra? Temos o custo da promoção por item/região/período? | Entra se houver custo por campanha; senão fica fora. | aberta | |

## Fase 4 (Logística) — perguntas iniciais da descoberta

| ID | SPEC | Para | Pergunta | Leitura provável | Status | Resposta |
|---|---|---|---|---|---|---|
| Q-34 | SPEC-4-001 | Marcelo Néquio | Como cada CD (Matriz, Barueri, São José, Bauru, Rancharia, Curitiba) monta cargas hoje e qual deles é o melhor modelo? | Cada um com sua planilha; um deles será o modelo. | aberta | |
| Q-35 | SPEC-4-001 | Marcelo Néquio | Quais custos entram: frete terceiro por viagem/km, diesel, pernoite, pedágio? Onde estão esses valores? | Tabela de frete por freteiro e rota. | aberta | |
| Q-36 | SPEC-4-001 | Marcelo Néquio | Regras de prazo: pedido + 72h vale para todos? Quais as janelas por cliente? | 72h padrão, com exceções por rede. | aberta | |
| Q-37 | SPEC-4-001 | Marcelo Néquio | Capacidade dos veículos (cubagem e peso) por tipo, e a origem dos pedidos do dia. | Tipos de veículo fixos; pedidos do SAP. | aberta | |

## Fase 5

| ID | SPEC | Para | Pergunta | Leitura provável | Status | Resposta |
|---|---|---|---|---|---|---|
| Q-38 | SPEC-5-002 | Paulo | Que tipo de explicação ou sugestão da IA seria útil para supervisores e para a Diretoria? | Explicar a meta de um cliente e sugerir revisão das metas REVISAR. | aberta | |
