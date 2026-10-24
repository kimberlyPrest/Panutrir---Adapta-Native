# AP-2026-10-24-1445 — Congeladas do BI: a coluna `tipo` esconde a troca

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T2.1c / SPEC-1-002 (metodologia M-02)
- Sinal: nas congeladas de venda exportadas do BI, os valores não estão na mesma linha por natureza do lançamento. `Soma de vlritens` só vem preenchido em `tipo='Venda'` e `tipo='Bonificação'`; `Soma de vlrtroca` é **sempre 0** nas linhas `tipo='Venda'` e só vem preenchido em `Troca`, `Devoluções Diversas`, `Qualidade`, `Falta de Produtos`, `Divergências` e `Fora do Padrão`. A mesma chave (mês, cliente, SKU) aparece de 1 a 5 vezes, uma por tipo.
- Evidência: arquivos reais de 2024/2025/2026 (427.788 / 484.691 / 373.103 linhas). Em 2026: 241.520 linhas `Venda` com vlrtroca = R$ 0,00 e 122.096 linhas `Troca` com vlritens = R$ 0,00 e vlrtroca = R$ 7.167.408,26. Provado no teste RED de `contracts/testes_t21c.py`: filtrar `tipo='Venda'` devolve venda líquida inflada.
- Regra reutilizável: ao agregar venda das congeladas, **somar todos os tipos** e só então calcular `venda_liquida = Σvlritens − Σvlrdesc − Σvlrtroca`. Nunca filtrar `tipo='Venda'`: em 2026 isso descarta R$ 7,9 M de trocas e infla a venda líquida na mesma medida.
- Quando aplicar: qualquer carga ou cálculo que leia as congeladas do BI (T2.2, T2.3, T5.x, Fase 3).
- Quando não aplicar: se uma fonte futura trouxer a venda já líquida por linha (uma linha por chave, sem coluna `tipo`) — aí não há o que somar entre tipos.
- Confiança: alta — medido nos três arquivos completos e travado por teste automatizado.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
