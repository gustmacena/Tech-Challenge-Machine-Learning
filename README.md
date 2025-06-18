# Tech-Challenge-Machine-Learning

## Overview  
Este repositório contém o desenvolvimento de um modelo preditivo para prever se o índice IBOVESPA fechará em alta (↑) ou baixa (↓) no dia seguinte, utilizando dados históricos diários e técnicas de Machine Learning. Ainda estamos em fase de refinamento para atingir a acurácia mínima de 75% exigida no desafio. fileciteturn0file0

## Challenge Description  
- **Problema:** Prever se o fechamento do IBOVESPA no dia seguinte será maior ou menor que o do dia atual. fileciteturn0file0  
- **Dados:** Séries históricas diárias do IBOVESPA obtidas em formato CSV, cobrindo um mínimo de 2 anos de operações. fileciteturn0file0  
- **Objetivo:** Modelo com acurácia ≥ 75% no conjunto de teste, que deve conter os últimos 30 dias disponíveis. fileciteturn0file0  

## Estrutura do Projeto  
```
├── DadosHistoricos_Ibovespa.csv   # Dados brutos baixados do Investing.com  
├── POSTECH - Tech Challenge - Fase 2.pdf  # Descrição oficial do desafio  
├── Direta.ipynb                   # Notebook de limpeza, EDA e baseline com Random Forest  
├── main.ipynb                     # Notebook de feature engineering avançada e otimização de modelos  
└── README.md                      # Este arquivo  
```

## Pré-requisitos  
- Python 3.7+  
- Recomenda-se criar e ativar um ambiente virtual:  
  ```bash
  python -m venv venv
  source venv/bin/activate    # Linux/Mac
  venv\Scripts\activate       # Windows
  ```  
- Instalar dependências:  
  ```bash
  pip install pandas numpy matplotlib seaborn scikit-learn xgboost ta
  ```  

## Como Executar  
1. **Carregar dados e pré-processar**  
   - Converte colunas de data e volume (`Direta.ipynb`).  
   - Cria variação percentual diária, médias móveis, RSI, MACD, lags, features cíclicas, Bollinger Bands, etc.  
2. **Definir target**  
   - `target = 1` se o fechamento do dia seguinte > fechamento de hoje; caso contrário `0`.  
3. **Divisão treino/teste**  
   - Treino: todos os dias, exceto os últimos 30.  
   - Teste: últimos 30 dias.  
4. **Modelagem**  
   - Testes iniciais com Regressão Logística, Random Forest e XGBoost.  
   - Busca de hiperparâmetros com `RandomizedSearchCV` e validação temporal (`TimeSeriesSplit`).  
   - Experimentos com Stacking de modelos.  
5. **Avaliação**  
   - Métricas: acurácia, matriz de confusão e relatório de classificação.

Cada etapa está documentada nos notebooks correspondentes.  

## Status & Próximos Passos  
- **Status:** Em desenvolvimento, com acurácia atual próxima de 67% (aumentar para ≥ 75%).  
- **Próximos passos:**  
  - Refinar a engenharia de atributos (ex.: features de volatilidade, momentum de mais janelas).  
  - Explorar modelos de sequência (p.ex. LSTM) para capturar dependências temporais.  
  - Implantar pipeline reproduzível (scripts `.py` ou pipeline Airflow/n8n).  

---

> _Este projeto faz parte do Tech Challenge da Pós-Tech em Data Analytics da FIAP._  
