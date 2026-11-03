# Revalidação das SPECs da Fase 2 contra o aprendizado da Fase 1

**Data:** 02/11/2026 · **Autor:** Paulo (assistente) · **Pedido:** Alex · **Natureza:** análise de preparação — NÃO implementa nada (AGENTS.md: não avançar de fase sem liberação da consultora).

Cada SPEC da Fase 2 manda "revalidar contra o aprendizado da Fase 1 ao abrir a fase". Este documento faz essa revalidação ANTES da liberação, para que a fase comece no dia do ok da Kim sem estudo inicial. O que a Fase 1 já entrega é listado como **OK**; o que falta vira **GAP** (com o tamanho estimado).

---

## SPEC-2-001 — Ciclo do mês seguinte, automático (F2-T1.1..T1.3)

| Item da SPEC | Estado após a Fase 1 | Ação na Fase 2 |
|---|---|---|
| Janelas avançam sozinhas (elegibilidade 3m, motor 24m, mix 6m, idade +1) | **PARCIAL** — o motor T5.x roda com janelas, mas `motor_oficial.py` tem a elegibilidade (linha 139: `("2026-07","2026-08","2026-09")`) e a janela do piso **fixas no código**; `CICLO`/`HIST_INI`/`HIST_FIM`/`M1` são constantes de topo | F2-T1.1: tornar as janelas derivadas do `CICLO` (T−3, T−24, T−6) e gravar no `ciclo_meta`; prova CA-2-01 com teste de datas |
| Idade dos SKUs avança sozinha | **OK** — `idade_de()` deriva de `data_N` e avança quando o histórico avança | Nada a fazer |
| Herança de parâmetros (cópia da versão anterior + IS/DU do novo mês) | **OK** — `criar_versao_parametros` (T3.1) já clona versão oficial com novo IS/DU; imutabilidade provada | F2-T1.1: chamar o RPC na criação do ciclo |
| Carga recorrente do mês fechado | **OK** — `carga_vendas.py` (T2.2) é idempotente, opera por mês, com `carga_registro` e verificação 0,00 provada (T2.3) | F2-T1.2: empacotar para operação pelo Ângelo (sem SQL); gatilho operacional a definir |
| Validação paralela Nov/26 × processo atual | **BLOQUEIO EXTERNO** — depende do BI exportar Out/26 fechado (mesmo bloqueio do CA-1-12) | F2-T1.3 só roda com o BI de Out/26; registrar dependência na matriz |

**Aprendizado da Fase 1 aplicado:** o bug dos 31 promotores (SQL redigitado) e o bug das 2 linhas SUBSTITUICAO_DESTINO (agregação por chave) reforçam: o avanço de janelas deve ser **derivado do ciclo, nunca digitado** — prova CA-2-01 com datas, não com números.

## SPEC-2-002 — Gestão de parâmetros pela interface (F2-T2.1..T2.2)

| Item | Estado | Ação |
|---|---|---|
| P-01..P-16 editáveis sem SQL | **OK** — tudo em `parametros_versao`/`parametros_valor` (T3.1); versão oficial imutável por trigger | F2-T2.1: tela React + RPC de nova versão (rascunho → oficial) |
| Autor e motivo em cada alteração | **OK** — `criar_versao_parametros` já exige motivo e registra autor | Nada |
| Papel `editar_parametros` | **OK** — operação existe na matriz 7×8 (T1.2) | Nada |
| Ciclo aprovado/publicado bloqueia edição | **OK** — `ciclo_meta.status` (T1.2) tem a máquina de estados; a regra de bloqueio é checagem na RPC | CA-2-06 |
| Diff entre versões na tela | **NOVO** — comparação de `parametros_valor` entre 2 versões; front + consulta simples | F2-T2.1 |
| Sortimento/substituição **por rede com vigência por ciclo** | **GAP MENOR** — as tabelas existem (T3.1) mas não têm vínculo com ciclo/vigência | F2-T2.2: avaliar coluna de vigência (migration pequena); atenção ao aprendizado de que regras mudam por ciclo (EMENDA 02) |

## SPEC-2-003 — Simulação e comparação de cenários (F2-T3.1..T3.2)

| Item | Estado | Ação |
|---|---|---|
| Execução versionada | **OK** — `execucao_calculo` + `hash_insumos_execucao` (T3.3), reprodutibilidade provada | Nada |
| Versão de parâmetros marcada `simulacao` | **GAP MENOR** — `parametros_versao` não tem coluna de tipo (oficial/simulação); migration simples + regra "só 1 oficial por mês" já existe (23P01) | F2-T3.1 |
| Motor roda com qualquer versão | **OK** — `motor_oficial.py` lê a versão por ID; trocar o ID roda o cenário (regressão do G já provada: G=0 → −2,578%; G=0,05 → +2,030%) | Nada |
| Comparação por canal/supervisor/linha | **OK** — consolidações M-31 (T6.4, diferença zero em todos os níveis) + views de agregação (T7.3) | F2-T3.2: tela de comparação (front) |
| "Explica qual parâmetro causou a mudança" | **OK** — a memória de cálculo (T5.x/T7.3) já mostra o parâmetro em cada passo | Reusar o painel de memória |
| Limite de cenários por ciclo | **NOVO** — parâmetro novo P-17 (proposta) | F2-T3.1 |

## SPEC-2-004 — Aprovação, publicação e consulta (F2-T4.1..T4.3)

| Item | Estado | Ação |
|---|---|---|
| Só execução reconciliada pode ser aprovada | **OK (base pronta)** — `controle_gabarito` (T7.2) já tem estado por controle; falta a regra "todos BATE → execução reconciliada" gravada na execução | F2-T4.1: derivar o estado e bloquear a RPC de aprovação |
| Papel `aprovador` | **OK** — atribuído ao Paulo (T1.2); `aprovar_publicar` na matriz | Nada |
| Publicação imutável / versão 2 com motivo | **OK** — trigger de imutabilidade da T3.3 congela execução; nova execução = nova versão | CA-2-11 |
| Exceções só por regra/parâmetro (M-31) | **OK** — consolidações provadas sem ajuste manual | Nada |
| Consulta por perfil (supervisor vê a equipe; promotor a carteira) | **GAP** — `meta_linha` já tem `supervisor`/`promotor` em coluna (T7.3), mas o RLS atual é "authenticated lê tudo" | F2-T4.2: RLS por perfil + teste com 2 supervisores (CA-2-12); papéis `consulta` já existem na matriz |
| Metabase | **DISPONÍVEL** — conector Metabase conectado no ambiente; o formato de saída é a **Q-22 (pendente, é pergunta do Paulo)** | F2-T4.3 após Q-22 |
| K2 — medir o prazo até publicar antes do 1º dia | **NOVO** — `execucao_calculo` já tem início/fim; faltam timestamps de carga/aprovação/publicação | F2-T4.3: registrar eventos e calcular o prazo |

---

## Resumo executivo

- **Pronto na Fase 1 (sem trabalho novo):** execução versionada, imutabilidade, matriz de papéis, herança de parâmetros, carga idempotente, consolidações, memória de cálculo, controles de gabarito.
- **GAPs pequenos e conhecidos (estimativa: migrations simples + front):** janelas derivadas do ciclo (única correção de código no motor), coluna de vigência em sortimento/substituição, coluna `simulacao`, RLS por perfil, timestamps do K2, telas React (parâmetros, comparação, consulta por perfil).
- **Dependências externas que atravessam a Fase 2:** (1) BI exportar Out/26 fechado → CA-1-12 e F2-T1.3; (2) Q-22 (layout, pergunta do Paulo) → F2-T4.3; (3) D2/D3 da Kim → universo fechado (afeta a validação paralela Nov/26).
- **Risco revalidado:** a validação paralela (CA-2-03) compara o sistema com o processo atual do Paulo — a métrica por regime (D1) e o universo (D2/D3) precisam estar confirmados até lá, senão as diferenças não serão explicáveis uma a uma.

**Recomendação de ordem quando a Kim liberar:** F2-T1.1 (janelas) → F2-T2.1 (parâmetros, destrava T3.1/T4.1) → F2-T4.1 (aprovar/publicar) → F2-T3.x (simulação) → F2-T4.2/T4.3 (consulta/Metabase). A ordem da matriz já é compatível; a única inversão sugerida é antecipar F2-T4.1 antes de F2-T3.x, porque o fluxo de aprovação é pré-condição de negócio para o ciclo Dez/26 (K2).