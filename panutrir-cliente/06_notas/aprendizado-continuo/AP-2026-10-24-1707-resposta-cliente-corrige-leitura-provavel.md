# AP-2026-10-24-1707 — A leitura provável do registro de perguntas pode estar errada; confirmar antes de implementar

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T3.1 / SPEC-1-003 (Q-10)
- Sinal: o registro central trazia "Informado a cada ciclo" como leitura provável da Q-10. O cliente respondeu **"Calculado"** — o oposto. Se a leitura provável tivesse sido implementada sem confirmação, o motor teria nascido com o G digitado à mão em vez de derivado, e o erro só apareceria no segundo mês de uso.
- Evidência: `03_documentos/perguntas-ao-cliente.md` linha da Q-10, antes "Informado a cada ciclo / aberta", depois "Calculado / respondida (24/10/2026, Alex)". Efeito registrado na SPEC-1-003 e no changelog.
- Regra reutilizável: "leitura provável" serve para formular a pergunta e para não bloquear o início — nunca como substituto da resposta. Quando a resposta chega e diverge, corrija o registro **e** procure o que foi implementado com base na suposição, mesmo que pareça não afetar.
- Quando aplicar: toda pergunta do registro central (Q-xx) cujo valor já tenha sido seedado ou codificado como default.
- Quando não aplicar: pergunta retirada do registro sem efeito no código.
- Confiança: alta — divergência documentada entre a suposição e a resposta literal.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
