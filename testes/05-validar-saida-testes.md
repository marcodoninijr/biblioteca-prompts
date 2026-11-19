Exemplo 9 (resposta em conformidade com todas as regras)

"Olá, Fernanda! Recebemos a sua solicitação de alteração do endereço de entrega do pedido 4510. Nossa equipe de logística já foi acionada para verificar a possibilidade de atualização antes do envio. Assim que tivermos a confirmação, avisaremos você por aqui."

Saída obtida:
{"aprovado": true, "regras_violadas": [], "motivo_reprovacao": null}

Avaliação: 
Passou. A entrada cumpre todos os critérios (4 frases curtas, tom profissional, sem promessa de prazo exato e sem variáveis vazadas), resultando na aprovação em JSON puro conforme o schema.

Exemplo 10 (resposta com violações múltiplas)

"Fala, null! Relaxa que eu já vou fazer o seu estorno imediato aqui pra você, em 5 minutinhos o dinheiro cai na conta."

Saída obtida:
{"aprovado": false, "regras_violadas": [1, 2, 4], "motivo_reprovacao": "A resposta promete estorno imediato com prazo exato de 5 minutos, usa gírias e tom excessivamente informal, além de expor o termo 'null' na saudação."}

Avaliação:
Passou. Identificou todas as três violações sem marcar erroneamente a regra 3 (o texto tem apenas 2 frases), manteve o JSON limpo e justificou cada falha de forma objetiva.

Exemplo 19 (tom profissional, mas com prazo exato e 5 frases)

"Olá, Juliana! Analisamos o seu relato sobre o erro no boleto bancário. Nossa equipe financeira já está tratando o seu caso com prioridade. Até amanhã às 14h o novo boleto estará disponível no seu painel. Caso tenha qualquer outra dúvida, estamos à disposição por aqui."

Saída obtida:
{"aprovado": false, "regras_violadas": [1, 3], "motivo_reprovacao": "Informa prazo exato de resolução (amanhã às 14h) e excede o limite de 4 frases curtas (possui 5 frases)."}

Avaliação:
Passou. Mesmo com um texto educado e bem escrito, o auditor detectou tanto o prazo exato (regra 1) quanto o excesso de frases (regra 3), sem falsos positivos nas regras 2 e 4.

Exemplo 20 (variável de template vazada + tom passivo-agressivo)

"Olá, {{nome_cliente}}! Como já explicamos antes, basta ler o manual com atenção para evitar esse erro básico. Não podemos ajudar se você não seguir as instruções."

Saída obtida:
{"aprovado": false, "regras_violadas": [2, 4], "motivo_reprovacao": "Apresenta tom agressivo e pouco empático com o cliente e contém a variável não preenchida '{{nome_cliente}}'."}

Avaliação:
Passou. Capturou o vazamento do placeholder {{nome_cliente}} (regra 4) e o tom hostil sem depender de gírias explícitas (regra 2), mantendo o JSON estritamente dentro do schema.