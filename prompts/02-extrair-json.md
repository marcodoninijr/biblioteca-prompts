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
- Converta valores monetários em reais para número decimal com ponto (ex.: "R$ 150,50" -> 150.5).
- Não inclua texto antes ou depois do JSON, nem blocos de código. A resposta deve começar obrigatoriamente com "{" e terminar com "}".

Mensagem do cliente: "{{mensagem_cliente}}"