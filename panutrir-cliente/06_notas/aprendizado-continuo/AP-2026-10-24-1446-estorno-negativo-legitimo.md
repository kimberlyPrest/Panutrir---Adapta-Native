# AP-2026-10-24-1446 — Estorno negativo é dado legítimo, não erro de validação

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T2.1c / SPEC-1-002
- Sinal: os arquivos reais das congeladas contêm valores negativos (~0,2% das linhas) que são estornos reais: `Soma de vlritens` negativo com `Soma de qtde` também negativa em linhas `tipo='Venda'` (devolução de venda), e `Soma de vlrtroca` negativo em linhas `tipo='Troca'` (reversão de uma troca anterior). Um contrato que declare `min: 0` nessas colunas rejeita esses estornos e infla todos os totais.
- Evidência: 2024 — 970 linhas com vlritens negativo e 404 com vlrtroca negativo; 2025 — 745 e 42; 2026 — 851 e 6. O validador com `min: 0` (escrito na análise da T2.1c) rejeitou 3 linhas já numa amostra de 20.000; corrigido, os 3 arquivos completos passam sem rejeição. Testes R8 e R9 de `contracts/testes_t21c.py` travam a regra.
- Regra reutilizável: em contrato de dado financeiro de venda, negativo é sinal válido (estorno) e deve ser somado como está — nunca truncar em zero nem rejeitar por sinal. Validar apenas que o valor é numérico.
- Quando aplicar: qualquer contrato ou carga de valor monetário de venda/devolução das congeladas.
- Quando não aplicar: colunas que são grandezas físicas não estornáveis (ex.: dias úteis, contagem de SKUs distintos).
- Confiança: alta — contagem por arquivo completo e teste automatizado.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
