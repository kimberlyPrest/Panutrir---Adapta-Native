# Panutrir — Intranet de Metas e Logística

## Objetivo
Implementar a fase atual conforme as SPECs e tasks aprovadas, sem alterar o escopo por baixo.

## Stack
Supabase (Auth, Postgres, RLS, Edge Functions, migrations versionadas) + front React no Skip. Dependência nova exige justificativa e aceite da consultora.

## Antes de cada task
1. Ler `CLAUDE.md`, `STATUS.md`, `04_fase-atual/matriz-specs-fases.md` e a SPEC da task.
2. Conferir na matriz se as dependências estão ✔. A matriz é a fonte única de ordem e status.
3. Listar as perguntas `Q-xx` da task e o status de cada uma em `03_documentos/perguntas-ao-cliente.md`.

## Ritmo e teste do cliente
Vale desde 30/10/2026 e substitui o ritmo antigo, em que cada task pedia autorização e teste.

- Construa as tasks da matriz em sequência, uma por vez, sem pedir autorização nem teste entre elas. Cada task fecha pelas provas automáticas da SPEC: RED, GREEN, REGRESSÃO e conferência contra a fonte ou o gabarito.
- O teste do cliente é por SPEC e segue a seção `## Teste humano do cliente` de cada uma. Na Fase 1 são dois:
  1. **SPEC-1-001, na T1.3:** cada pessoa entra com a própria conta convidada, porque a troca de senha muda o login que a equipe já usa.
  2. **SPEC-1-007, no fim da fase:** Paulo confere o painel, a consulta e a exportação de Out/26. É o aceite da fase (T7.5).
- As SPECs 1-002 a 1-006 não têm nada para o cliente ver e fecham pela prova automática contra a fonte e o gabarito G-xx. Paulo e Ângelo veem esses números no painel da SPEC-1-007.
- Continuam sendo paradas: pergunta `Q-xx` que muda a implementação (protocolo abaixo), acesso que só o cliente tem (como a conexão do banco), divergência que a SPEC manda revisar com o cliente (CA-1-12) e as autorizações listadas em Regras.

## Protocolo de perguntas ao cliente
**Só pergunte o que muda a implementação:** uma regra de cálculo, o mapeamento de um dado ou o formato de uma saída. Não pergunte o que a metodologia, os dados (cabeçalhos, base de produtos) ou o gabarito já respondem, nem decisões que não alteram o sistema (quem opera, quem aprova, plano de infraestrutura, prazos). Em vez disso, verifique contra o gabarito e siga.

As perguntas **não bloqueiam o início** da task. Quando a task chegar na parte que depende de uma `Q-xx` aberta:

1. **Perguntar:** enviar ao destinatário indicado o texto da pergunta como está no registro, junto com a leitura provável ("confirma ou corrige?"). Marcar `perguntada (data)`.
2. **Enquanto aguarda:** implementar e testar o resto da task. A parte dependente fica atrás de um parâmetro com valor `PENDENTE`, que faz a execução sair como **não reconciliada**. Nunca implementar a leitura provável como se fosse resposta.
3. **Se houver duas leituras plausíveis:** implementar as duas atrás do parâmetro, rodar Out/26 e levar ao cliente qual delas bate com o gabarito. A escolha é do cliente.
4. **Registrar a resposta:** texto literal, data e autor na tabela "Respostas do cliente" da SPEC e no registro central; marcar `respondida`.
5. **Implementar conforme a resposta:** escrever primeiro o teste com o exemplo da resposta (RED), depois implementar (GREEN).
6. **Se a resposta mudar uma regra M-xx ou um valor do gabarito:** registrar no changelog como `[DECISÃO — cliente]` e avisar Kim antes de concluir a task.

## Regras
- Execute RED, GREEN e REGRESSÃO definidos na SPEC.
- Nenhum número da metodologia escrito no código: tudo vem da versão de parâmetros (SPEC-1-003).
- Dados reais só no Supabase do projeto; nunca commitar planilha, extrato, amostra ou print com dados reais. Fixtures de teste são sintéticas.
- Nenhuma senha ou segredo em migration ou código; contas são criadas por convite.
- Não marque task concluída sem evidência objetiva e sem todas as `Q-xx` da task respondidas.
- Não avance para outra fase sem liberação da consultora.
- Aplicar no Supabase do projeto a migration e a carga da própria task, e fazer o merge dela no repositório do app, faz parte da task e não pede autorização.
- Pedem autorização explícita: integrar fonte externa (como o DW), migration que apaga ou reescreve dado real já carregado fora da recarga por mês, e qualquer mudança no que a equipe já usa.
- Antes de reativar o Supabase pausado, siga o runbook `06_notas/aprendizado-continuo/AP-2026-10-01-1335-runbook-pausa-supabase.md`.
