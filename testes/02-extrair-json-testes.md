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

Exemplo 13 (formato numérico com separador de milhar e código alfanumérico)

Mensagem do cliente: "E aí pessoal, aqui é o Rodrigo Silva! Comprei o notebook no pedido nº BR-20451 pagando R$ 1.899,50 no PIX e até agora não recebi o código de rastreio."

Saída obtida:{"nome_cliente": "Rodrigo Silva", "numero_pedido": "BR-20451", "valor_mencionado": 1899.5, "resumo_problema": "Cliente não recebeu código de rastreio do pedido"}

Avaliação:
Passou. Removeu o ponto de milhar corretamente (1899.5), manteve o código alfanumérico sem o prefixo "nº", extraiu nome completo e resumiu o problema em 8 palavras.

Exemplo 14 (múltiplos valores monetários na mesma mensagem)

Mensagem do cliente: "Oi, sou a Beatriz. Meu pedido #7710 custava R$ 300,00, mas com o frete de R$ 25,50 cobraram R$ 350,00 no meu cartão."

Saída obtida:
{"nome_cliente": "Beatriz", "numero_pedido": "7710", "valor_mencionado": 350.0, "resumo_problema": "Cobrança no cartão superior ao valor do pedido"}

Avaliação:
Passou com ressalva (brecha na v1.0). O JSON saiu válido e o valor escolhido (350.0) faz sentido por ser o total cobrado, mas a entrada cita três valores (300,00, 25,50 e 350,00). Como a v1.0 não define qual valor priorizar quando há mais de um, a extração fica sujeita a variação entre execuções. Ponto de melhoria para v1.1.

Revalidação (v1.1): Passou. Com o critério de priorizar o valor efetivamente cobrado ou em disputa, o retorno "valor_mencionado": 350.0 ficou coberto por regra explícita.