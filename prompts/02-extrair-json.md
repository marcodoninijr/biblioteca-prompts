Extraia as informações da mensagem do cliente abaixo e retorne exclusivamente um objeto JSON válido.

Schema obrigatório:
{
  "nome_cliente": string ou null,
  "numero_pedido": string (apenas o código, sem "#") ou null,
  "valor_mencionado": number (float com ponto decimal) ou null,
  "resumo_problema": string (máximo 10 palavras)
}

Regras:
- Não invente nem suponha dados. Se uma informação não estiver explícita na mensagem, preencha com null.
- Converta valores monetários em reais para número decimal com ponto (ex.: "R$ 150,50" -> 150.5; "R$ 1.899,50" -> 1899.5).
- Se houver mais de um valor monetário na mensagem, extraia o valor efetivamente cobrado ou em disputa; caso não haja cobrança em disputa, extraia o valor total do pedido.
- Não inclua texto antes ou depois do JSON, nem blocos de código. A resposta deve começar obrigatoriamente com "{" e terminar com "}".

Mensagem do cliente: "{{mensagem_cliente}}"