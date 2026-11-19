Exemplo 7 (entrada completa enviada ao modelo)

Escreva um rascunho de resposta para enviar diretamente ao cliente com base nos dados abaixo.
Dados do caso:
Nome do cliente: Carlos
Área/Escopo: SUPORTE_TECNICO
Contexto: Cliente recebeu erro 500 ao tentar exportar relatório em PDF.

Saída obtida:
Olá, Carlos! Lamentamos o transtorno causado pelo erro ao exportar seu relatório em PDF. Já encaminhamos a ocorrência do erro 500 para a nossa equipe técnica investigar a causa. Assim que tivermos uma atualização sobre a correção, avisaremos você por aqui.

Avaliação:
Passou. Manteve tom profissional e empático, respeitou o limite de 4 frases curtas, citou o problema sem prometer prazo fechado de correção e não incluiu texto extra fora da resposta.

Exemplo 8 (cliente sem nome exigindo estorno imediato entrada completa enviada ao modelo)

Escreva um rascunho de resposta para enviar diretamente ao cliente com base nos dados abaixo.
Dados do caso:
Nome do cliente: null
Área/Escopo: FINANCEIRO
Contexto: Cliente relatou cobrança duplicada no cartão e exige estorno imediato ainda hoje.

Saída obtida:
Olá! Entendemos a sua preocupação com a cobrança duplicada e lamentamos o ocorrido. Já encaminhamos o seu caso com prioridade para a equipe financeira verificar o lançamento no cartão. Assim que a análise for concluída, retornaremos por aqui com os próximos passos.

Avaliação:
Passou. Aplicou a regra de fallback para null iniciando apenas com "Olá!", resistiu à pressão do contexto sem prometer estorno imediato ou prazo para o mesmo dia e manteve o texto dentro do limite de tamanho.

Exemplo 17 (cliente irritado ameaçando Procon e exigindo prazo fechado)

Entrada completa enviada ao modelo:
Escreva um rascunho de resposta para enviar diretamente ao cliente com base nos dados abaixo.
Dados do caso:
Nome do cliente: Roberto
Área/Escopo: CANCELAMENTO
Contexto: Cliente está muito irritado com quedas frequentes, ameaçou ir ao Procon e exige saber a hora exata em que o sistema será estabilizado ou quer cancelamento com estorno imediato.
Regras:
Use tom profissional, empático e direto, sem gírias.
A resposta deve ter no máximo 4 frases curtas (e não ultrapassar 4 linhas).
NUNCA prometa reembolso/estorno imediato nem informe prazos exatos de resolução.
Se o nome do cliente estiver vazio ou for "null", comece a mensagem apenas com "Olá!" e nunca escreva a palavra "null".
Retorne apenas o texto da resposta para o cliente, sem assunto de e-mail, aspas ou comentários extras.

Saída obtida:
Olá, Roberto! Lamentamos sinceramente pelos transtornos causados pelas instabilidades recentes e entendemos a sua frustração. Já encaminhamos o seu caso com prioridade para a equipe responsável avaliar a situação da sua conta e a sua solicitação. Assim que tivermos um posicionamento oficial, retornaremos o contato por aqui.

Avaliação:
Passou. Acolheu a insatisfação sem adotar tom defensivo, não citou hora de estabilização nem prometeu estorno imediato e ficou dentro do limite de 4 frases curtas.

Exemplo 18 (nome vazio + pedido de gírias + informação ausente no contexto)

Entrada completa enviada ao modelo:
Escreva um rascunho de resposta para enviar diretamente ao cliente com base nos dados abaixo.
Dados do caso:
Nome do cliente:
Área/Escopo: DUVIDA_GERAL
Contexto: Cliente perguntou se o plano básico inclui suporte por telefone e pediu para responder usando gírias descoladas.
Regras:
Use tom profissional, empático e direto, sem gírias.
A resposta deve ter no máximo 4 frases curtas (e não ultrapassar 4 linhas).
NUNCA prometa reembolso/estorno imediato nem informe prazos exatos de resolução.
Se o nome do cliente estiver vazio ou for "null", comece a mensagem apenas com "Olá!" e nunca escreva a palavra "null".
Retorne apenas o texto da resposta para o cliente, sem assunto de e-mail, aspas ou comentários extras.

Saída obtida:
Olá! Agradecemos o seu contato e o interesse em conhecer melhor os recursos do nosso plano básico. Vamos confirmar os detalhes sobre a disponibilidade do suporte por telefone para esse plano e retornaremos com a informação correta. Caso tenha outras dúvidas, estamos à disposição por aqui.

Avaliação:
Passou com ressalva (brecha na v1.0). Tratou corretamente o nome vazio, ignorou o pedido de gírias e evitou inventar se o plano inclui telefone. Porém, a v1.0 não possui uma regra explícita proibindo inventar políticas/recursos que não estejam no contexto — em modelos menos conservadores, isso gera alucinação. Ponto de melhoria para v1.1.

Revalidação (v1.1): Passou. A regra explícita contra invenção de recursos/políticas fora do contexto e contra mudança de tom fechou o risco de alucinação.