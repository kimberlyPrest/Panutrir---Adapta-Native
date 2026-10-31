# 2026-10-31 — Cadastro do RAIZER e a lacuna de promotores no catálogo

## 1) O 84207 (RAIZER LOJA 3) — o que falta

| Campo | Situação | Como resolver |
|---|---|---|
| `cliente_codigo` | **84207** | — |
| `cliente_nome` | **RAIZER LOJA 3** (nome do gabarito) | — |
| `supervisor_codigo` | **167 — CIRO ROLIM MORAES** ✅ | — |
| `promotor_codigo` | **vazio** ❌ | o gabarito diz LEANDRO MORAES PULIDO, que é o **vendedor 183** |
| `rede` | **vazio** ❌ | a fonte (congelada de vendas) não traz rede para este cliente |
| `uf` | **vazio** ❌ | idem |
| `canal` | **vazio** (por decisão) | depende da lista de redes indiretas (Q-04) |
| `rede_codigo_sap` | **vazio** | idem rede |
| vigência | 2026-10-01, sem fim | — |

**Duas linhas ficaram de fora** (registradas em `carga_rede_pendente`): C04501 (T J BARBOSA)
é outro estabelecimento usando o mesmo código 84207, e C04432 é a mesma loja sem estrutura.

## 2) A lacuna real: promotores não estão no catálogo

Isto **não é um problema do RAIZER**, é do catálogo inteiro:

- `catalog_responsaveis` tem **19 registros, todos `supervisor`**.
- **Zero promotores cadastrados.**
- Mas **624 clientes têm `promotor_codigo` preenchido**, apontando para **31 códigos distintos**.
- Não existe FK dessa coluna para os responsáveis, então a inconsistência passa silenciosa.

A fonte (`estrutura_comercial_atual.xlsx`, 3.319 linhas) tem **128 vendedores distintos, todos com
nome preenchido** — o dado existe; só não foi carregado.

### 2.1 Consequência grave: 294 clientes têm promotor = supervisor

| Situação | Clientes |
|---|---|
| `promotor_codigo` preenchido | 624 |
| `promotor_codigo` **igual** a `supervisor_codigo` | **294** |
| — código 167 (CIRO ROLIM MORAES, supervisor) usado como promotor | 293 |
| — código 174 (LUAN DA SILVA CARNEIRO, supervisor) | 1 |

O código **167 é supervisor**, não vendedor: na fonte ele não aparece na coluna `cod_vendedor`.
Ele entrou em `promotor_codigo` porque o DE→PARA usa o mesmo campo para as duas coisas em
alguns registros. Efeito prático: a visão por promotor mostra o CIRO como promotor de 293
clientes — quando ele é o **supervisor** deles.

### 2.2 Códigos ambíguos entre papéis

Sete códigos aparecem nos dois papéis: **165, 167, 169, 170, 171, 174, 179**. São códigos de
supervisor usados também como vendedor em alguma linha. Sem uma chave por papel
(`tipo` + `codigo`), a hierarquia fica ambígua.

## 3) Impacto no gabarito

A aba `Meta Promotor` do cliente tem **123 promotores** e a `Meta Supervisor` mostra
**R$ 563.066,71 em "Orig. sem Promotor"**. Ou seja: o gabarito separa quem tem promotor de quem
não tem — e essa separação **não pode ser reproduzida** hoje, porque o catálogo não sabe quem é
promotor.

## 4) O que eu preciso para fechar

1. **Confirmar a chave de papel**: promotor e supervisor podem compartilhar código, ou o
   `cod_vendedor` é sempre distinto do `cod_supervisor`? Os 7 códigos ambíguos sugerem que
   compartilham — então a chave tem de ser (papel, código).
2. **Confirmar a regra de preenchimento**: quando `cod_vendedor` vem vazio ou igual ao
   supervisor, o cliente é "sem promotor" (e cai nos R$ 563 mil da aba Meta Supervisor)?
3. **Autorizar a carga dos 128 vendedores** como `responsavel_tipo='promotor'` — o dado está na
   fonte, com nome, e não exige inventar nada.
4. **Decidir o cadastro do 84207**: carregar C04501 (T J BARBOSA) como cliente novo com outro
   código, ou manter fora? Hoje ele está registrado como pendência.

Enquanto (1) e (2) não estiverem claros, carregar os promotores seria adivinhar — e a regra 25
proíbe criar responsável fictício. O que **posso** fazer agora, sem adivinhar: carregar os 128
vendedores com os códigos e nomes exatamente como estão na fonte (nenhum é inventado), deixando
a atribuição aos clientes como está até a confirmação.
