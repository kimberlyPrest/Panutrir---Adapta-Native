# Constituição do projeto

## Papéis
- **Consultora (Kim):** governa escopo, SPECs, gates e liberação de fases.
- **CSM:** valida alinhamento e aceite do escopo.
- **Champion (Ângelo):** valida semântica comercial e evidências operacionais.
- **Equipe de implementação:** executa uma task por vez conforme SPEC/TDD.

## Stack permitida
Supabase Auth, Postgres, RLS, Storage e migrations versionadas. Dependência adicional exige justificativa e aceite.

## Linha vermelha
Nenhuma task pode alterar resultado, limite ou CA da SPEC. Dados reais, integrações, publicação produtiva e ações irreversíveis exigem novo gate.

## Dívida
Toda dívida deve registrar origem, impacto, responsável, fase-alvo e evidência para encerramento.
