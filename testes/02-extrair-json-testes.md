Exemplo 3 (mensagem com todos os campos) 

Mensagem do cliente: "Olá, sou a Mariana. Meu pedido #9842 no valor de R$ 249,90 veio com a tela riscada."

Saída obtida:
{"nome_cliente": "Mariana", "numero_pedido": "9842", "valor_mencionado": 249.9, "resumo_problema": "Produto entregue com a tela riscada"}

Avaliação:
Passou. Retornou JSON válido sem texto extra, removeu o # do número do pedido conforme especificado, converteu R$ 249,90 para 249.9 e manteve o resumo com 6 palavras (dentro do limite de 10).

Exemplo 4 (mensagem sem dados cadastrais ou valor)

Mensagem do cliente: "O sistema não me deixa fazer login desde ontem à noite."

Saída obtida:
{"nome_cliente": null, "numero_pedido": null, "valor_mencionado": null, "resumo_problema": "Cliente não consegue fazer login no sistema"}


Avaliação:
Passou. Não alucinou nenhum dado ausente, preencheu os três campos faltantes com null, respeitou o schema exato e resumiu o problema em 7 palavras.