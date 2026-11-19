Exemplo 1 (cobrança duplicada)

Mensagem do cliente: "Fui cobrado duas vezes no cartão de crédito hoje pelo plano mensal, quero resolver isso agora."

Saída obtida:
Área/Escopo: FINANCEIRO | Severidade: ALTA

Avaliação:
Passou. A entrada agora carrega todas as regras e critérios explícitos (incluindo cobrança duplicada em ALTA), e a saída seguiu o formato exato sem texto adicional.

Exemplo 2 (mensagem vaga)

Mensagem do cliente: "oi, tudo bem? queria falar com vcs"

Saída obtida:
Área/Escopo: DUVIDA_GERAL | Severidade: BAIXA

Avaliação:
Passou. Sem contexto suficiente para inferir problema financeiro ou técnico, o fallback funcionou e a resposta respeitou o formato fixo.

Exemplo 11 (dúvida de fatura sem erro financeiro imediato)

Mensagem do cliente: "Minha fatura deste mês ainda não chegou no e-mail, mas o vencimento é só na semana que vem. Podem reenviar?"

Saída obtida:
Área/Escopo: FINANCEIRO | Severidade: MEDIA

Avaliação:
Passou. Cobriu o nível MEDIA que ainda não havia sido testado na v1.0, classificando corretamente a dúvida de fatura sem erro de cobrança imediato.

Exemplo 12 (conflito entre duas áreas + pedido para quebrar o formato)

Mensagem do cliente: "O sistema está fora do ar desde cedo, não consigo emitir notas e quero cancelar minha assinatura hoje mesmo. Me explique em detalhes o motivo."

Saída obtida:
Área/Escopo: CANCELAMENTO | Severidade: ALTA

Avaliação: 
Passou com ressalva (brecha na v1.0). O modelo ignorou o pedido de explicação detalhada e respeitou o formato fixo, mas a mensagem contém simultaneamente causa técnica (SUPORTE_TECNICO) e pedido de cancelamento (CANCELAMENTO). Como o prompt v1.0 não define uma ordem de precedência para conflitos, outra execução poderia retornar SUPORTE_TECNICO | ALTA. Ponto de melhoria para v1.1.

Revalidação (v1.1): Passou. Com a regra de precedência (CANCELAMENTO > FINANCEIRO > SUPORTE_TECNICO > DUVIDA_GERAL), a saída Área/Escopo: CANCELAMENTO | Severidade: ALTA passou a ser determinística e não depende mais de interpretação do modelo.