# Biblioteca de Prompts — Fluxo de Atendimento ao Cliente

Biblioteca de prompts reutilizáveis em texto puro, versionada com Git e validada por 20 casos de teste manuais (4 por prompt), cobrindo caminho feliz, casos de borda, ambiguidades e testes de estresse.

## Estrutura do Repositório

```text
biblioteca-prompts/
├── README.md
├── prompts/
│   ├── 01-classificar.md
│   ├── 02-extrair-json.md
│   ├── 03-resumir.md
│   ├── 04-rascunhar-resposta.md
│   └── 05-validar-saida.md
└── testes/
    ├── 01-classificar-testes.md
    ├── 02-extrair-json-testes.md
    ├── 03-resumir-testes.md
    ├── 04-rascunhar-resposta-testes.md
    └── 05-validar-saida-testes.md
```

## Índice de Prompts e Cobertura de Testes (v1.1)

| # | Prompt | Objetivo | Testes | Status (v1.1) |
|---|---|---|---|---|
| 1 | [Classificar](prompts/01-classificar.md) | Define área/escopo e severidade em formato fixo | [Testes 1, 2, 11, 12](testes/01-classificar-testes.md) | 4/4 Aprovados |
| 2 | [Extrair JSON](prompts/02-extrair-json.md) | Extrai entidades da mensagem em JSON puro com schema fixo | [Testes 3, 4, 13, 14](testes/02-extrair-json-testes.md) | 4/4 Aprovados |
| 3 | [Resumir](prompts/03-resumir.md) | Gera resumo factual em 3 linhas para passagem de turno | [Testes 5, 6, 15, 16](testes/03-resumir-testes.md) | 4/4 Aprovados |
| 4 | [Rascunhar Resposta](prompts/04-rascunhar-resposta.md) | Redige resposta empática ao cliente seguindo regras de negócio | [Testes 7, 8, 17, 18](testes/04-rascunhar-resposta-testes.md) | 4/4 Aprovados |
| 5 | [Validar Saída](prompts/05-validar-saida.md) | Audita o rascunho contra 4 regras e retorna aprovação em JSON | [Testes 9, 10, 19, 20](testes/05-validar-saida-testes.md) | 4/4 Aprovados |

**Total:** 20/20 casos de teste aprovados.

## Como Usar

1. Abra o arquivo desejado em `prompts/`.
2. Substitua os placeholders entre chaves duplas (ex.: `{{mensagem_cliente}}`, `{{historico_conversa}}`, `{{resposta_gerada}}`) pelos dados reais do atendimento.
3. Envie o template completo ao modelo de linguagem.
4. Sempre que alterar qualquer regra de um prompt, reexecute os 4 casos correspondentes em `testes/` para evitar regressões antes de criar um novo commit.

## Changelog

### v1.1
- **01-classificar:** adicionada ordem de precedência para conflito entre áreas (`CANCELAMENTO > FINANCEIRO > SUPORTE_TECNICO > DUVIDA_GERAL`) e instrução para ignorar pedidos de quebra de formato na mensagem do cliente.
- **02-extrair-json:** adicionada regra de desempate para múltiplos valores monetários (prioriza valor cobrado/em disputa ou total do pedido).
- **03-resumir:** adicionada instrução explícita anti-*prompt injection* tratando o histórico como entrada não confiável.
- **04-rascunhar-resposta:** adicionada proibição explícita de inventar recursos/políticas fora do contexto e reforço de manutenção de tom profissional.
- **Testes:** bateria expandida de 10 para 20 casos e 4 ressalvas da v1.0 revalidadas com aprovação integral (20/20).

### v1.0
- Estrutura inicial do repositório com 5 prompts reutilizáveis e 10 casos de teste iniciais (2 por prompt).