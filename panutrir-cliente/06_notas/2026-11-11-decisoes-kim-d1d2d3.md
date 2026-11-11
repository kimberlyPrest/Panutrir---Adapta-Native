# Decisões da Kim — D1, D2 e D3 (11/11/2026)

**Responde:** `06_notas/2026-10-31-duvidas-para-kim.md` e `06_notas/2026-11-06-mensagem-kim-d1d2d3.md`.
**Decidido por:** Kim (consultora), 11/11/2026.
**Destrava:** T2.1.5 (validação paralela de Nov/26) e, por consequência, T2.4.6 (publicação de Dez/26 antes do dia 1º). Também a T5.1/CA-1-13, pendência carregada da Fase 1.

---

## D1: métrica por regime — **CONFIRMADA**

- **PISO e INTRODUÇÃO:** `vlritens − vlrdesc` (sem a troca).
- **REGULAR_24M:** líquida de 3 termos (`vlritens − vlrdesc − vlrtroca`).
- **Carrefour:** maturidade **por loja**. Muffato e São Francisco continuam **por rede**, porque por loja o resultado piora (+2,04%).

**Por quê:** os dados respondem. O piso fecha em 244/246 linhas com `vlritens − vlrdesc`. Nos 1.237 clientes puro-REGULAR, a mediana fica em 1,0009 com 3 termos contra 0,9306 com 2. O Carrefour por loja leva o total a −0,22% e bate com a `Meta Cliente Linha`, em que a linha do Carrefour é a loja. A regra 2 da metodologia descreve a fórmula do REGULAR e o gabarito é a execução real do modelo, então vale o que o gabarito faz.

**Efeito:** o motor híbrido deixa de ser leitura provável e passa a ser regra. Pode ser publicado como fechado.

## D2: SKUs sem produto (141951 e 2279) — **FICAM FORA do universo**

- Ficam fora do universo e da Meta Original e continuam visíveis na **auditoria**, como hoje.
- O resíduo de **−15 pares (−0,05%)** contra o G-11 fica **aceito como divergência explicada**. O CA-1-13 pode fechar com essa ressalva registrada.
- **Revisitar só se** a validação paralela de Nov/26 (T2.1.5) mostrar que o processo atual do cliente distribui meta para esses SKUs. Nesse caso, a pergunta vai ao Alex com o número de Nov/26 em mãos.

**Por quê:** seis hipóteses foram testadas e nenhuma reproduz a regra do gabarito, então não há leitura que os dados confirmem. O critério que já existe no programa é o da Q-41, respondida pelo Alex em 06/11: o que não tem cadastro fica fora de tudo. Aplicar o mesmo critério ao produto mantém a regra coerente e não inventa uma fórmula. O caminho certo, do lado do cliente, é cadastrar esses SKUs na BASE_PRODUTOS. Quando entrarem, passam a contar normalmente.

## D3: clientes "0" e "vazio" — **ENTRAM no universo (confirmada)**

- As 60 linhas (30 com `codcli=0`, R$ 50.002,93, e 30 com `codcli` vazio, R$ 41.931,62) entram no universo como clientes, conforme a leitura provável já aplicada.
- O contrato `vendas` (regra V-02) deixa de rejeitar essas linhas; a forma de tratá-las na carga fica como já implementado.

**Por quê:** a aba `Auditoria Estrutura` do gabarito traz o código 0 como cliente real, com exatamente R$ 50.002,93 de venda. Os dados respondem.

---

## Próximos passos (agente do projeto)

1. Registrar estas respostas na seção **Respostas** das SPECs correspondentes (motor/universo da Fase 1 e contrato `vendas`), com data e autor (Kim, 11/11/2026).
2. Retirar `PENDENTE` dos parâmetros que dependiam de D1/D2/D3 e seguir para a **T2.1.5**.
3. Sincronizar o `04_fase-atual/tasks.json` com o andamento real: hoje ele marca as 27 tasks como `planejada`/`bloqueada`, enquanto o STATUS registra 23 concluídas.

Continuam abertas e fora destas decisões: **Q-07** (Ângelo), **Q-10b** (fórmula do G nos próximos ciclos), **T2.5.5** (convites e privatização) e **T2.6.2** (acesso ao Metabase).
