Marqs - Assistente e Educador Financeiro 🤖💰
Um agente financeiro inteligente desenvolvido com IA Generativa para ensinar conceitos básicos de finanças e orientar sobre investimentos de baixo risco.
🎯 O Problema
A maioria dos adultos não possui conhecimento mínimo para organizar sua vida financeira, resultando em dificuldades para alcançar objetivos e acúmulo de dívidas.
💡 A Solução
Marqs é um educador financeiro que:

Ensina conceitos financeiros de forma didática e acessível
Analisa o perfil e histórico financeiro do usuário
Sugere investimentos de baixo risco personalizados
Explica produtos financeiros disponíveis
Ajuda a administrar finanças pessoais

🚀 Tecnologias

LLM: Ollama (Gemma2:9b)
Interface: Streamlit
Linguagem: Python
Dados: CSV e JSON

📁 Estrutura do Projeto
📁 lab-agente-financeiro/
├── 📁 data/                          # Dados mockados do cliente
│   ├── perfil_investidor.json        # Perfil e metas
│   ├── transacoes.csv                # Histórico de gastos
│   ├── historico_atendimento.csv     # Atendimentos anteriores
│   └── produtos_financeiros.json     # Produtos disponíveis
│
├── 📁 docs/                          # Documentação completa
│   ├── 01-documentacao-agente.md     # Caso de uso e arquitetura
│   ├── 02-base-conhecimento.md       # Estratégia de dados
│   ├── 03-prompts.md                 # Engenharia de prompts
│   ├── 04-metricas.md                # Avaliação e resultados
│   └── 05-pitch.md                   # Apresentação do projeto
│
└── 📁 src/                           # Código da aplicação
    ├── app.py                        # Aplicação Streamlit
    └── README.md                     # Instruções de execução
⚙️ Como Executar
1. Instalar o Ollama
bash# Baixe em: https://ollama.com
# Baixe o modelo:
ollama pull gemma2:9b
2. Instalar dependências
bashpip install streamlit pandas requests
3. Verificar o Ollama
bashollama serve
4. Executar a aplicação
bashstreamlit run src/app.py
🎭 Características do Marqs
Personalidade:

Educativo e consultivo
Formal e acessível
Didático e paciente

Capacidades:

✅ Explica conceitos financeiros básicos
✅ Analisa gastos do usuário
✅ Sugere investimentos de baixo risco
✅ Contextualiza com base no perfil do cliente
❌ Não sugere investimentos em ações
❌ Não acessa dados sensíveis

📊 Produtos Financeiros Cobertos

Tesouro Selic, Prefixado e IPCA+
CDB Liquidez Diária
LCI/LCA
Poupança
Fundos Multimercado
Fundos Imobiliários (FIIs)
Fundos de Ações (apenas explicação)

🔒 Segurança

Respostas baseadas apenas nos dados fornecidos
Não inventa informações financeiras
Admite quando não sabe algo
Não compartilha dados de outros clientes

📈 Resultados
O agente demonstrou assertividade nas respostas esperadas durante os testes, respondendo corretamente a:

Consultas sobre conceitos financeiros
Análise de gastos pessoais
Recomendações personalizadas
Perguntas fora do escopo (recusa adequada)

🎯 Próximos Passos

 Melhorar a linguagem para ser mais descontraída
 Otimizar tempo de resposta
 Integrar com API de LLM mais robusta
 Expandir base de conhecimento

📝 Documentação Completa
Toda a documentação detalhada está disponível na pasta docs/, incluindo arquitetura, estratégias de prompt, métricas e pitch.

Desenvolvido como parte do desafio de IA Generativa da DIO
