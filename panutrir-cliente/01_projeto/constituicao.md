# Constituição do projeto

## Papéis
- **Consultora (Kim):** governa escopo, SPECs, emendas e liberação de fases.
- **CSM (Matheus):** valida alinhamento, prazos e aceite do escopo.
- **Dono do projeto (Paulo):** dono da metodologia e dos parâmetros; responde as perguntas de regra; dá o aceite das fases.
- **Champion (Ângelo):** valida semântica comercial, estrutura e números.
- **Implementação (Léo):** executa uma task por vez conforme a SPEC, o TDD e o protocolo de perguntas.

## Stack permitida
Supabase (Auth, Postgres, RLS, Edge Functions, migrations versionadas) e front React no Skip. Dependência adicional exige justificativa e aceite.

## Linha vermelha
- Nenhuma task altera resultado, limite ou CA da SPEC; mudança de regra entra por resposta registrada do cliente ou por emenda.
- Nenhuma regra presumida: dúvida vira pergunta registrada (protocolo no `AGENTS.md`).
- Dados reais só no Supabase do projeto, nunca em repositório; nenhum segredo em código.
- Publicação produtiva, integração externa e ações irreversíveis exigem autorização explícita.

## Dívida
Toda dívida registra origem, impacto, responsável, fase-alvo e evidência para encerramento.
