# Challenge Telecom X - Parte 2: Previsão de Churn com Machine Learning

## 1. Propósito da Análise

Este projeto é a segunda fase do Challenge Telecom X, uma iniciativa do programa Oracle Next Education em parceria com a Alura. O objetivo principal desta análise foi desenvolver um pipeline de Machine Learning para **prever a evasão (churn) de clientes**. A partir de um conjunto de dados contendo características demográficas, de contrato e de serviços, construímos modelos preditivos capazes de identificar quais clientes têm maior chance de cancelar seus serviços, permitindo que a empresa tome ações de retenção proativas.

## 2. Estrutura do Projeto

O repositório está organizado da seguinte forma:

```
├── challenge_telecom_x_churn_part2.ipynb
├── README.md
```

- **`challenge_telecom_x_churn_part2.ipynb`**: O notebook principal contendo todo o código e a análise da Parte 2, desde o carregamento dos dados até a conclusão estratégica.
- **`README.md`**: Este arquivo, com a documentação do projeto.

## 3. Processo de Preparação dos Dados

Antes da modelagem, os dados passaram por um rigoroso processo de preparação para garantir que estivessem em um formato adequado para os algoritmos de Machine Learning.

- **Classificação das Variáveis:** As variáveis foram tratadas como numéricas (ex: `customer_tenure`, `account_Charges_Monthly`) ou categóricas (ex: `account_Contract`, `customer_gender`).
- **Encoding de Variáveis Categóricas:** As colunas de texto foram convertidas para um formato numérico através da técnica de **One-Hot Encoding** (`pd.get_dummies`). Isso criou novas colunas binárias para cada categoria, evitando relações de ordem falsas.
- **Normalização:** As features numéricas foram normalizadas usando o **MinMaxScaler**, que ajusta os valores para uma escala comum entre 0 e 1. Isso é crucial para modelos sensíveis à escala, como a Regressão Logística.
- **Separação em Treino e Teste:** O conjunto de dados foi dividido em 70% para treino e 30% para teste (`train_test_split`), utilizando a estratificação (`stratify`) para manter a mesma proporção de churn em ambos os conjuntos.

## 4. Justificativas para a Modelagem

Foram escolhidos dois modelos de classificação com características distintas para uma análise comparativa:

1.  **Regressão Logística:**
    - **Justificativa:** É um modelo clássico, rápido e altamente interpretável. Serve como um excelente *baseline* para entender a influência linear de cada variável na probabilidade de churn.
    - **Necessidade de Normalização:** Sim, por ser sensível à escala das features.

2.  **Random Forest (Floresta Aleatória):**
    - **Justificativa:** É um modelo de *ensemble* mais robusto, capaz de capturar relações complexas e não-lineares nos dados. Geralmente apresenta alta performance e fornece uma métrica direta da importância de cada variável.
    - **Necessidade de Normalização:** Não, mas os dados normalizados foram utilizados para simplificar o pipeline.

## 5. Gráficos e Insights da Análise (EDA)

A análise exploratória revelou fortes indicadores de churn. Os gráficos abaixo ilustram duas das principais descobertas:

**Tempo de Contrato vs. Evasão**

O boxplot mostra que clientes que evadiram (`Churn = 1`) tinham, em média, um tempo de contrato significativamente menor do que os que permaneceram.


<img width="844" height="629" alt="image" src="https://github.com/user-attachments/assets/cdd2e3d5-59c1-4934-9054-69dfcbeb3c06" />


**Análise de Correlação**

O ranking de correlação com a variável `Churn` destacou os principais fatores de risco (correlação positiva) e de proteção (correlação negativa).


<img width="1793" height="1558" alt="image" src="https://github.com/user-attachments/assets/67566d68-dbcc-40bd-bbba-997e9ab39164" />


- **Principais Insights:** Contratos mensais, baixo tempo de contrato e serviço de fibra ótica estão fortemente associados a um maior risco de churn. Por outro lado, contratos de longo prazo (1 ou 2 anos) são os principais fatores de retenção.

## 6. Instruções para Execução

Para executar este projeto, siga os passos abaixo:

**Bibliotecas Necessárias:**
Certifique-se de ter as seguintes bibliotecas Python instaladas:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

**Executando o Notebook:**
1. Clone este repositório do GitHub.
2. Abra o arquivo `challenge_telecom_x_churn_part2.ipynb` em um ambiente como Jupyter Notebook ou Google Colab.
3. O notebook está configurado para carregar o arquivo `dados_tratados.csv` diretamente da URL "Raw" do GitHub, então não é necessário fazer o upload manual dos dados. Apenas execute as células em sequência.
