# Panutrir — Intranet de Metas e Logística

## Objetivo
Implementar a fase atual conforme as SPECs e tasks aprovadas, sem alterar o escopo por baixo.

## Stack
Supabase (Auth, Postgres, RLS, Edge Functions, migrations versionadas) + front React no Skip. Dependência nova exige justificativa e aceite da consultora.

## Antes de cada task
1. Ler `CLAUDE.md`, `STATUS.md`, `04_fase-atual/matriz-specs-fases.md` e a SPEC da task.
2. Conferir na matriz se as dependências estão ✔. A matriz é a fonte única de ordem e status.
3. Listar as perguntas `Q-xx` da task e o status de cada uma em `03_documentos/perguntas-ao-cliente.md`.

## Protocolo de perguntas ao cliente
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
- Não publique, migre produção ou integre fonte externa sem autorização explícita.
- Antes de reativar o Supabase pausado, siga o runbook `06_notas/aprendizado-continuo/AP-2026-10-01-1335-runbook-pausa-supabase.md`.
