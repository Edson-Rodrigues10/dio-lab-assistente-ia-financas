# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_investidor.json` | JSON | Personalizar recomendações e explicações |
| `produtos_financeiros.json` | JSON | Base para explicações dos produtos financeiros disponíveis |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente e usar essas informações de forma didática e para sugestões|

> [!TIP]
> **Dataset público:**  [Hugging Face](https://huggingface.co/datasets).

---

## Adaptações nos Dados

Foram adicionados ao arquivo `produtos_financeiros.json` os seguintes produtos financeiros:
- Tesouro Prefixado;
- Tesouro IPCA + NTN-B;
- Poupança;
- Fundos Imobiliários.

Para uma maior base de dados para as sugestões e explicações do agente.

---

## Estratégia de Integração

### Como os dados são carregados?

Os dados serão carregados via código da seguinte forma:

```python
import pandas as pd
import json

# Arquivos CSV:
historico = pd.read_csv('data/historico_atendimento.csv')
transacoes = pd.read_csv('data/transacoes.csv')

# Arquivos Json:
with open('data/perfil_investidor.json', 'r', encoding='utf-8') as f:
  perfil = json.load(f)

with open('data/produtos_financeiros.json', 'r', encoding='utf-8') as f:
  produtos = json.load(f)
```

### Como os dados são usados no prompt?

Exemplo de injeção de dados:

```text
PERFIL DO CLIENTE (data/perfil_investidor.json):
{
  "nome": "Aldair Sobrenome",
  "idade": 28,
  "profissao": "Engenheiro Agrônomo",
  "renda_mensal": 7000.00,
  "perfil_investidor": "moderado",
  "objetivo_principal": "Construir reserva de emergência",
  "patrimonio_total": 30000.00,
  "reserva_emergencia_atual": 12000.00,
  "aceita_risco": false,
  "metas": [
    {
      "meta": "Completar reserva de emergência",
      "valor_necessario": 20000.00,
      "prazo": "2026-06"
    },
    {
      "meta": "Entrada do apartamento",
      "valor_necessario": 62000.00,
      "prazo": "2028-12"
    }
  ]
}

HISTÓRICO DE TRANSAÇÕES (data/transacoes.csv):
data,descricao,categoria,valor,tipo
2025-10-01,Salário,receita,7000.00,entrada
2025-10-02,Aluguel,moradia,1500.00,saida
2025-10-03,Supermercado,alimentacao,620.00,saida
2025-10-05,Netflix,lazer,55.90,saida
2025-10-07,Farmácia,saude,89.00,saida
2025-10-10,Restaurante,alimentacao,120.00,saida
2025-10-12,Uber,transporte,45.00,saida
2025-10-15,Conta de Luz,moradia,180.00,saida
2025-10-20,Academia,saude,99.00,saida
2025-10-25,Combustível,transporte,250.00,saida


HISTÓRICO DE ATENDIMENTOS (data/historico_atendimento.csv):
data,canal,tema,resumo,resolvido
2025-09-15,chat,CDB,Cliente perguntou sobre rentabilidade e prazos,sim
2025-09-22,telefone,Problema no app,Erro ao visualizar extrato foi corrigido,sim
2025-10-01,chat,Tesouro Selic,Cliente pediu explicação sobre o funcionamento do Tesouro Direto,sim
2025-10-12,chat,Metas financeiras,Cliente acompanhou o progresso da reserva de emergência,sim
2025-10-25,email,Atualização cadastral,Cliente atualizou e-mail e telefone,sim

```

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
