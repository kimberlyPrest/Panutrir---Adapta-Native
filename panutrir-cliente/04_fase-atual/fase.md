# Fase 2 — Ciclo mensal operável

**Estado:** ABERTA — documentação da fase na localização canônica `04_fase-atual/`. **Liberada para execução** pela consultora (Kim, 04/11/2026).
**Janela indicativa:** 17/11 – 05/12/2026 (escopo de 20/10; datas indicativas, Matheus confirma com o cliente)
**Objetivo:** o ciclo do mês acontece dentro do sistema — Nov/26 roda em paralelo com a planilha do Paulo e é reconciliado, e Dez/26 é aprovado, publicado e consultado pela equipe sem a planilha.

## Situação documental — 04/11/2026

Publicação documental autorizada pela Kim em 04/11/2026 e reorganizada para a localização canônica no mesmo dia. **A execução da Fase 2 foi liberada expressamente pela consultora (Kim) em 04/11/2026.** A Fase 1 foi aceita em 02/11/2026 e está arquivada em `05_entregas/fase-1/` (caminho relativo à raiz desta pasta), com T1.3 e T5.1/CA-1-13 abertas como pendência carregada; seus registros são preservados. Critérios, testes e evidências abaixo são requisitos a cumprir, não resultados alcançados.

A situação de partida descrita em 03/11 é um retrato daquela data. O commit `9f4354c` de 04/11 registra a conferência Q-21 e a correção do GAP Indireto; consulte `../changelog.md` e o registro central antes de executar. A Q-21 não deve ser solicitada novamente como se essa conferência não existisse; sua suficiência para cada critério ainda precisa ser verificada. Demais decisões não são presumidas resolvidas.

As correções de segurança no código do app em 03/11 não equivalem ao fechamento de G-SEG: rotação, convites, privacidade dos repositórios e isolamento real exigem evidências próprias. Nenhum gate é encerrado por esta publicação.

## Entrega demonstrável

Ângelo cria o ciclo de Nov/26 e carrega o mês fechado sem apoio técnico. Paulo confere Nov/26 contra o processo atual e vê cada diferença explicada. Depois, para Dez/26: Paulo simula dois cenários e compara, aprova a execução reconciliada, publica a meta (imutável) e cada supervisor consulta apenas a própria equipe. Ao final, a meta publicada está no Metabase no layout combinado.

## Situação de partida (medida, não presumida)

- **Fase 1 ACEITA pelo cliente em 02/11/2026** (T7.5/CA-1-25), matriz em **28/30 tasks (93%)**.
- **Duas tasks da Fase 1 seguem abertas** e são carregadas como pendência: **T1.3** (convites de Léo e Ângelo, privatização dos repositórios) e **T5.1/CA-1-13** (universo — D2/D3 na Kim).
- **O gate interno de fechamento da Fase 1 não está satisfeito** por essas duas pendências. Esta fase é preparada **sem simular aprovação nem check fechado**: gerar a minuta não fecha a Fase 1, e nenhum critério desta fase é dado por cumprido por antecipação.
- **A reconciliação da Fase 1 tem dois modos, e eles não se confundem:** VALIDAÇÃO DA REGRA **19/19 BATEM** (a regra reproduz o modelo do cliente no universo do gabarito) e EXECUÇÃO **15/19 BATEM** (G-03 e G-07 divergem por D2/D3; G-09 e G-10 ficam sem medida porque o mix depende da carteira do gabarito). **19/19 no modo regra não significa execução reconciliada** e não autoriza aprovação — é o que o CA-2-16 desta fase exige.
- **Bloqueios externos que atravessam a fase:** o BI ainda não exportou as vendas de **Out/26** fechadas (afeta CA-2-02, CA-2-03 e o controle CA-1-12 da Fase 1); a **Q-22** (layout do Metabase) segue sem resposta; **D1/D2/D3, Q-42, Q-10b e Q-20** seguem abertas.

## SPECs

| SPEC | Tema | Requisitos |
|---|---|---|
| SPEC-2-001 | Ciclo do mês seguinte: janelas derivadas, herança de parâmetros com confirmação e validação paralela | RF-17 |
| SPEC-2-002 | Parâmetros e regras pela interface, versionados, com diff e vigência por ciclo | RF-06, RF-18 |
| SPEC-2-003 | Simulação e comparação de cenários, com o oficial isolado | RF-19 |
| SPEC-2-004 | Aprovação por reconciliação, publicação imutável e medição do prazo (K2) | RF-20, RF-22 (K2) |
| SPEC-2-005 | Consulta por perfil com isolamento real por carteira (RLS) | RF-21 |
| SPEC-2-006 | Entrega da meta publicada ao Metabase | RF-22 |

São **6 SPECs** — dentro do range saudável de 3 a 7. A divisão difere da versão planejada em 20/10 (4 SPECs): as unidades separadas para provar de forma independente **permissão** (SPEC-2-005) e **integração** (SPEC-2-006) saíram da SPEC-2-004, que fica com aprovação e publicação. O motivo está registrado em cada SPEC, na seção `## Emendas`.

## Critérios de aceite da fase

**CA-2-01 a CA-2-31**, detalhados nas SPECs. Os bloqueantes são:

- **CA-2-03** — Nov/26 reconciliado com o processo atual, toda diferença com causa declarada e o aceite do Paulo. É a liberação L2 do escopo (desliga a planilha).
- **CA-2-16** — só execução reconciliada **no modo EXECUÇÃO** é aprovada; o 19/19 do modo regra não aprova.
- **CA-2-21** — Dez/26 publicado antes de 01/12/2026, com o prazo do K2 medido (os quatro marcos que o medem são o CA-2-20).
- **CA-2-27** — isolamento provado com contas convidadas, sem credencial exposta. Depende do gate de segurança G-SEG.

## Tasks

| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência esperada | Pré-condições | Status | Leva |
|---|---|---|---|---|---|---|---|---|---|
| T2.1.1 | Derivar as janelas do ciclo do mês de referência (elegibilidade T−3, motor T−24, mix T−6 e idade do SKU em meses) e gravá-las no registro do ciclo | Léo | SPEC-2-001 | CA-2-01 | RED 'motor com Jul–Set/26 fixo' → GREEN com dois ciclos (2026-11 e 2026-12) | relatório com as 4 janelas dos dois ciclos + busca sem mês literal no caminho do cálculo | Fase 1 aceita (02/11/2026) | ☐ | A |
| T2.2.1 | Entregar a tela de parâmetros versionados (P-01..P-18) com criação de versão e autor e motivo obrigatórios, aceitando valor PENDENTE explícito | Léo | SPEC-2-002 | CA-2-06 | GREEN 'editar P-02 pela tela cria versão nova com autor e motivo' + RED 'UPDATE direto na versão é recusado' | captura da tela + registro de versão com autor, motivo e os campos marcados PENDENTE | Fase 1 aceita (02/11/2026) | ☐ | A |
| T2.4.1 | Apurar a reconciliação por modo (VALIDAÇÃO DA REGRA e EXECUÇÃO) e exigir, em cada divergência, causa declarada, dono e referência da pendência que a resolve | Léo | SPEC-2-004 | CA-2-16, CA-2-19 | RED 'execução 15/19 aprovada porque a regra dá 19/19' → GREEN 'modo EXECUÇÃO não reconciliado bloqueia' | tabela dos dois modos por ciclo + bloqueio provado + causa, dono e referência em cada divergência | Fase 1 aceita (02/11/2026) | ☐ | A |
| T2.5.1 | Criar os papéis de consulta e o vínculo usuário→carteira por papel (supervisor, promotor, diretoria), sem inferir vínculo por código ambíguo entre papéis | Léo | SPEC-2-005 | CA-2-23 | RED 'usuário sem vínculo lê a empresa inteira' → GREEN 'sem vínculo não lê nada (fail-closed)' | tabela de vínculos + fixture sintética com 2 supervisores, 2 promotores, 1 diretoria e 1 sem vínculo | Fase 1 aceita (02/11/2026) | ☐ | A |
| T2.6.1 | Extrair a meta publicada numa consulta de saída com o layout lido de parâmetro (P-18), recusando layout fixo no código | Léo | SPEC-2-006 | CA-2-28, CA-2-31 | RED 'layout fixo no código, troca exige deploy' → GREEN 'layout lido da versão, com PENDENTE declarado' | consulta de saída + fixture sintética nos layouts A e B, sem nenhum dado real | Fase 1 aceita (02/11/2026) | ☐ | A |
| T2.1.2 | Herdar a versão de parâmetros do ciclo anterior gravando Meta Diretoria, IS, dias úteis e G como requer_confirmação e forçar não reconciliada a execução que usar parâmetro não confirmado | Léo | SPEC-2-001 | CA-2-05 | RED 'G herdado de Out/26 executa como reconciliado' → GREEN 'parâmetro não confirmado impede reconciliar' | versão 2026-11 com os 4 campos marcados + execução saindo não reconciliada com a lista de pendências | T2.1.1 | ☐ | B |
| T2.1.3 | Construir a rotina operacional de carga mensal sem SQL, com registro e idempotência por mês; entregar fluxo para operação do Ângelo | Léo | SPEC-2-001 | CA-2-02 | GREEN 'carregar um mês pelo fluxo operacional' + REGRESSÃO 'recarregar o mesmo mês não duplica nem altera os outros' | fluxo implementado e prova automática de carga/reenvio sem duplicação; operação do Ângelo validada no teste humano da SPEC | Fase 1 aceita (02/11/2026) | ☐ | B |
| T2.1.4 | Provar que o ciclo 2026-10 aceito continua idêntico depois da derivação das janelas, comparando insumos e totais por regime | Léo | SPEC-2-001 | CA-2-04 | REGRESSÃO 'reexecutar 2026-10 e comparar com o estado aceito em 02/11' | hash da execução aceita × hash da reexecução + totais por regime lado a lado, diferença zero | T2.1.1 | ☐ | B |
| T2.2.2 | Mostrar o diff campo a campo entre duas versões de parâmetros e quais execuções usaram cada versão | Léo | SPEC-2-002 | CA-2-09 | GREEN 'comparar duas versões existentes' + REGRESSÃO 'execução aponta a versão que a gerou' | captura do diff + consulta execução → versão com o mesmo resultado | T2.2.1 | ☐ | B |
| T2.2.3 | Dar vigência por ciclo às regras por rede (sortimento restrito, substituição e exclusões) e recusar vigência retroativa | Léo | SPEC-2-002 | CA-2-07 | RED 'regra nova muda o resultado do ciclo anterior' → GREEN 'vale só no ciclo de vigência' | dois ciclos com regras diferentes + resultado de cada um antes e depois da regra nova | Fase 1 aceita (02/11/2026) | ☐ | B |
| T2.3.1 | Criar execução de cenário a partir de versão derivada marcada simulacao, sem tocar a execução oficial | Léo | SPEC-2-003 | CA-2-11 | RED 'cenário sobrescreve o resultado oficial' → GREEN 'hash do oficial idêntico antes e depois' | hash do oficial antes e depois + execução de cenário separada e marcada como simulacao | Fase 1 aceita (02/11/2026) | ☐ | B |
| T2.4.2 | Executar aprovar e publicar com trilha append-only (ator, operação, alvo, motivo, timestamp UTC) e recusa auditada | Léo | SPEC-2-004 | CA-2-17 | GREEN 'aprovar execução reconciliada no modo EXECUÇÃO e publicar' + Falha 'aprovar execução não reconciliada' | trilha de aprovação e publicação + duas negativas auditadas | T2.4.1 | ☐ | B |
| T2.5.2 | Entregar a consulta por perfil: supervisor vê a própria equipe, promotor a própria carteira e Diretoria a empresa | Léo | SPEC-2-005 | CA-2-24 | GREEN '2 supervisores e 2 promotores consultando' + 'Diretoria vê o total da empresa' | capturas por perfil + conferência de que nenhum perfil alcança carteira alheia | T2.5.1 | ☐ | B |
| T2.6.2 | Refrescar a meta publicada para o Metabase de forma idempotente e conferir no destino o total publicado | Léo | SPEC-2-006 | CA-2-29 | GREEN 'dois refreshes seguidos dão o mesmo total' + REGRESSÃO 'total no destino igual ao publicado' | comparação destino × publicado com diferença zero + registro de cada refresh | T2.6.1; Q-22 respondida; acesso e autorização do destino Metabase verificados | 🔒 | B |
| T2.2.4 | Bloquear criação de versão em ciclo aprovado ou publicado e recusar oficializar versão com parâmetro pendente, auditando as duas negativas | Léo | SPEC-2-002 | CA-2-08, CA-2-10 | Falha 'criar versão em ciclo publicado' e 'oficializar com P-16 pendente' → duas negações auditadas | log das 2 negações + versão anterior intacta e ainda utilizável | T2.2.1 | ☐ | C |
| T2.3.2 | Aplicar o limite de cenários por ciclo (P-17) com recusa auditada ao exceder e alerta registrado enquanto o valor estiver pendente | Léo | SPEC-2-003 | CA-2-14 | Falha 'criar o cenário N+1 com P-17 definido' → recusa auditada; com P-17 pendente → alerta e uso acumulado | log da recusa + contagem de cenários do ciclo + alerta registrado no caso pendente | T2.3.1 | ☐ | C |
| T2.3.3 | Comparar dois cenários por canal, supervisor e linha, com diferença absoluta e percentual, somas fechando e o parâmetro causador identificado | Léo | SPEC-2-003 | CA-2-12, CA-2-15 | GREEN 'comparação com somas por nível' + REGRESSÃO 'soma dos filhos igual ao pai em cada nível' | tela da comparação com as somas conferidas em cada nível e o parâmetro apontado por diferença | T2.3.1 | ☐ | C |
| T2.4.3 | Congelar a publicação e obrigar a correção por nova execução publicada como versão 2 com motivo, preservando a versão 1 consultável | Léo | SPEC-2-004 | CA-2-18 | RED 'UPDATE direto na meta publicada' → GREEN 'negado; versão 2 com motivo e v1 preservada' | negativa do UPDATE + versão 2 publicada com motivo + versão 1 ainda consultável | T2.4.2 | ☐ | C |
| T2.5.3 | Aplicar RLS por carteira nas tabelas de resultado e provar a negativa em três frentes: consulta pela interface, RPC e acesso direto à tabela | Léo | SPEC-2-005 | CA-2-25 | Falha 'promotor acessando carteira alheia pelas 3 frentes' → negado nas 3 e auditado | matriz de 5 perfis × 3 frentes com resultado e auditoria da negação | T2.5.1; T2.5.2 | ☐ | C |
| T2.5.4 | Fazer a consulta exibir somente a meta publicada, com o ciclo declarado e a memória de cálculo disponível | Léo | SPEC-2-005 | CA-2-26 | RED 'consulta mostra execução em rascunho e cenário' → GREEN 'só a publicada, com ciclo e memória' | capturas antes e depois + conferência do ciclo declarado e da memória de cálculo | T2.4.2; T2.5.2 | ☐ | C |
| T2.6.3 | Restringir o extrato à meta publicada, incluir o campo de perfil necessário à permissão no destino e registrar a responsabilidade do cliente pela configuração do Metabase | Léo | SPEC-2-006 | CA-2-30 | RED 'rascunho e cenário aparecem no extrato' → GREEN 'só publicado, com campo de perfil' | extrato conferido coluna a coluna + nota de responsabilidade assinada pelo cliente | T2.6.2 | ☐ | C |
| T2.1.5 | Rodar Nov/26 pelo sistema e pelo processo atual do Paulo e reconciliar as diferenças uma a uma até o aceite | Ângelo | SPEC-2-001 | CA-2-03 | GREEN 'Nov/26 dos dois processos' + REGRESSÃO 'nenhuma diferença sem causa declarada' | parecer de reconciliação item a item + aceite do Paulo registrado | T2.1.2; T2.1.3; T2.4.2; D1, D2, D3 e Q-42 respondidas | 🔒 | D |
| T2.3.4 | Promover um cenário a candidato oficial registrando autor, motivo e versão derivada, sem publicar | Léo | SPEC-2-003 | CA-2-13 | RED 'promoção sem motivo' → GREEN 'exige autor e motivo e não publica' | trilha da promoção + estado do ciclo antes e depois, sem publicação | T2.3.3 | ☐ | D |
| T2.4.4 | Registrar os quatro marcos do ciclo (mês fechado carregado, execução, aprovação e publicação) com timestamp UTC e calcular o prazo do K2 | Léo | SPEC-2-004 | CA-2-20 | GREEN 'prazo calculado a partir dos 4 marcos' + REGRESSÃO 'marco ausente não vira zero' | relatório de tempos do ciclo + cálculo do prazo conferido à mão | T2.4.2 | ☐ | D |
| T2.4.5 | Recusar ajuste manual do número final em qualquer nível e exigir que a exceção entre por regra ou por parâmetro versionado | Léo | SPEC-2-004 | CA-2-22 | Falha 'editar a Meta Final de um Cliente × SKU direto na tabela' → negado; a mesma mudança por parâmetro é aceita no ciclo seguinte | log da negativa + prova de que a via por parâmetro produz o efeito esperado no ciclo seguinte | T2.4.2 | ☐ | D |
| T2.4.6 | Publicar o ciclo Dez/26 antes do primeiro dia de dezembro e medir o prazo do K2 no ciclo real | Ângelo | SPEC-2-004 | CA-2-21 | GREEN 'publicação de Dez/26 antes de 01/12' + REGRESSÃO 'prazo do K2 medido e comparável ao baseline de até o dia 5' | registro da publicação com data e hora + medição do prazo do ciclo | T2.1.5; T2.4.4; T2.4.5; T2.6.2; T2.5.4 | ☐ | E |
| T2.5.5 | Provar o isolamento real com contas convidadas (2 supervisores, 2 promotores e diretoria) e nenhuma credencial exposta em tela, front, migration ou endpoint | Léo | SPEC-2-005 | CA-2-27 | Falha 'login com credencial preenchida, endpoint de troca de senha acessível e conta compartilhada' → negado nas 3 frentes | captura do login sem credencial + resposta do endpoint removido + 5 contas convidadas entrando com senha própria | T2.5.3; Gate G-SEG satisfeito; Convites e privatização dos repositórios concluídos pelo cliente | 🔒 | E |

## Levas

- **A:** T2.1.1, T2.2.1, T2.4.1, T2.5.1, T2.6.1
- **B:** T2.1.2, T2.1.3, T2.1.4, T2.2.2, T2.2.3, T2.3.1, T2.4.2, T2.5.2, T2.6.2
- **C:** T2.2.4, T2.3.2, T2.3.3, T2.4.3, T2.5.3, T2.5.4, T2.6.3
- **D:** T2.1.5, T2.3.4, T2.4.4, T2.4.5
- **E:** T2.4.6, T2.5.5

## Teste do cliente

Por SPEC, não por task (regra de `AGENTS.md`, desde 30/10). Na Fase 2 são **seis** testes humanos:

1. **SPEC-2-001** — Ângelo cria o ciclo, carrega o mês fechado e confirma os parâmetros herdados; **Paulo dá o aceite da validação paralela** de Nov/26 (é a liberação L2 do escopo).
2. **SPEC-2-002** — Ângelo e Paulo alteram parâmetros com motivo, comparam versões e cadastram uma regra por rede.
3. **SPEC-2-003** — Paulo simula dois cenários, compara e promove o escolhido.
4. **SPEC-2-004** — Paulo aprova e publica o ciclo Dez/26 antes de 01/12; mede-se o prazo do K2.
5. **SPEC-2-005** — 2 supervisores e 2 promotores entram com a própria conta e veem só a própria carteira (depende de T1.3, do cliente).
6. **SPEC-2-006** — Ângelo roda o refresh e Paulo confere layout e total no Metabase (depende de Q-22).

As provas automáticas (RED/GREEN/REGRESSÃO) substituem o teste humano em tudo que não é decisão do cliente.

## Fora desta fase

- **Acompanhamento** (realizado × meta, trocas, visitas, diagnósticos) — Fase 3.
- **Módulo Logística** — Fase 4.
- **Integração e IA assistiva** — Fase 5.
- **Cálculo do G nos ciclos seguintes (Q-10b)**, fechamento do universo (**D2/D3**) e da métrica por regime (**D1**): são decisões da consultora e do cliente. A fase **consome** a resposta como pendência declarada; não a inventa nem a converte em valor presumido.
- **Definir o valor dos parâmetros em aberto** (P-07, P-13, P-16, P-17, P-18, P-19): a fase guarda e exibe; quem define é o cliente.
- **Criar contas por convite e privatizar os repositórios**: é a T1.3 da Fase 1, ainda aberta.
- **Reler o layout do Metabase por conta própria**: é a Q-22.
- **Substituir o Metabase ou modelar o BI**: fora do programa.

## Gates e pendências que atravessam a fase

| Gate / pendência | Efeito na fase | Dono |
|---|---|---|
| **G-SEG** — remover/resetar o endpoint de troca de senha, rotacionar a credencial exposta em 03/11, concluir os convites e provar o isolamento real | bloqueia a T2.5.5 (CA-2-27) e **a publicação operacional e o acesso da equipe, não a publicação documental autorizada** | Léo (técnico) + Kim (aceite) |
| **BI exportar Out/26** fechado | bloqueia CA-2-02, CA-2-03 e o controle CA-1-12 da Fase 1 | Paulo |
| **D1, D2, D3, Q-42** | deixam o modo EXECUÇÃO com divergência declarada; sem elas Nov/26 não é reconciliável | Kim |
| **Q-20** | arredondamento do GAP Direto no centavo | Paulo |
| **Q-22** | layout do Metabase — sem ela, nada vai ao destino | Paulo |
| **Q-10b** | valor de P-07 em Nov/26 sai pendente e a execução não reconcilia | Kim / Paulo |
| **T1.3 (Fase 1)** | convites e privatização; pré-condição da prova de isolamento com contas reais | cliente |
| **T5.1/CA-1-13 (Fase 1)** | universo em −0,23%; carregado como pendência, não como resolvido | Kim |

## Histórico

- **04/11/2026** — **Execução liberada pela consultora (Kim).** A liberação não fecha gate nem pendência: T2.1.5, T2.5.5 e T2.6.2 seguem 🔒 até suas pré-condições; demais tasks seguem a ordem das levas.
- **04/11/2026** — Pacote documental movido para a localização canônica: fase, seis SPECs, matriz e tasks em
  `04_fase-atual/`; a documentação da Fase 1 passou para `05_entregas/fase-1/`. Mudança de organização:
  não libera execução, não fecha gate e não altera o aceite nem as pendências da Fase 1.
- **03/11/2026** — Minuta gerada por pedido da consultora ("Pode gerar a fase 2"), com as quatro SPECs de 20/10 revalidadas e desdobradas em seis, tasks decompostas, matriz de dependências e parecer de revisão. Nada publicado, nada implementado, nenhum push. Fase 1 **não** é declarada fechada: T1.3 e T5.1 seguem abertas.
- **20/10/2026** — EMENDA 02/2026: fase planejada com quatro SPECs (ciclo, parâmetros, cenários, aprovação/publicação/consulta), sem detalhamento executável.

## Convenção de status e rastreabilidade

☐ planejada: construção/prova sintética após dependências técnicas. 🔒 bloqueada: ação real exige decisão externa, autorização ou segurança pendente (T2.1.5, T2.5.5, T2.6.2). Nenhuma tarefa autoriza uso real sem seus gates.

RF-21 → SPEC-2-005; RF-22 → SPEC-2-006; K2 também em SPEC-2-004. PRD e matriz globais sincronizados nesta publicação.
