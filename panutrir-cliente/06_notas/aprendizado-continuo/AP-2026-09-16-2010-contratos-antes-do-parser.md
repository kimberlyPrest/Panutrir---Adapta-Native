# AP-2026-09-16-2010 — Contratos e fixtures antes do parser

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T2.1 / SPEC-1-002
- Sinal: a Fase 1 não tinha schema real aprovado nos documentos públicos (a revalidação depende do Gate G1), mas a task exigia contratos definidos. Definir primeiro os contratos e as fixtures sintéticas, com casos inválidos catalogados, deu à T2.2 (upload/staging) uma base de teste pronta e evitou que o parser fosse escrito contra um formato inventado na hora.
- Evidência: `contracts/catalogo-schemas.json` v1.0.0, quatro contratos versionados, 6 fixtures válidas (incl. reenvio idêntico e delimitador `;`) e 14 casos inválidos/limítrofes em `fixtures/synthetic/`; relatório `fixtures/cases-relatorio.md` com RED registrado; QA do Skip v0.0.10 passou; aprovação do champion.
- Regra reutilizável: em importação de arquivos, versionar contratos + fixtures (válidas e inválidas) antes de implementar o parser/upload; o parser passa a ser testável contra casos nomeados em vez de exemplos ad hoc.
- Quando aplicar: tasks de importação (T2.2, T2.3, T3.1) e qualquer nova fonte de arquivo na Fase 1.
- Quando não aplicar: carga real (G1), que exige revalidação dos contratos contra o schema oficial antes de uso produtivo.
- Confiança: média — sequência funcionou nesta task; a confirmação completa vem quando T2.2 consumir as fixtures sem ajustes estruturais.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto; todas as fixtures são sintéticas.
