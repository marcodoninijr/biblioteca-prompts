Classifique a área/escopo da mensagem abaixo e informe a severidade do problema.
Áreas/Escopos permitidos: [FINANCEIRO, SUPORTE_TECNICO, CANCELAMENTO, DUVIDA_GERAL]
Severidades permitidas:
- ALTA: cobrança duplicada ou indevida, sistema fora do ar, bloqueio de acesso ou ameaça de cancelamento.
- MEDIA: bug parcial que não impede o uso, dúvida sobre pagamento/fatura sem erro financeiro imediato ou pedido de ajuste.
- BAIXA: dúvida geral, solicitação simples ou mensagem vaga/incompleta.

Regras:
- Escolha exatamente uma área/escopo e uma severidade.
- Se a mensagem for vaga ou sem contexto, classifique como DUVIDA_GERAL e severidade BAIXA.
- Retorne exclusivamente no formato abaixo, sem explicações extras:
Área/Escopo: <VALOR> | Severidade: <VALOR>

Mensagem do cliente: "{{mensagem_cliente}}"