# Challenge Telecom X - Parte 2: Previsão de evasão de clientes com Machine Learning

## 1. Propósito da Análise

Este projeto faz parte da segunda fase do Challenge Telecom X, uma iniciativa realizada pelo programa Oracle Next Education em parceria com a Alura. O grande objetivo desta etapa foi desenvolver um processo automatizado, chamado pipeline de Machine Learning, para ajudar a empresa a prever quais clientes têm mais chance de cancelar seus serviços (o chamado “churn”).

Para isso, utilizamos uma base de dados que contém várias informações importantes sobre os clientes, como dados pessoais, detalhes dos contratos e dos serviços utilizados. A partir desse material, treinamos modelos de previsão (modelos preditivos) capazes de identificar os clientes que correm maior risco de sair da empresa.

Com essas previsões em mãos, a empresa consegue agir antes que o cancelamento aconteça, adotando estratégias para manter os clientes e, assim, diminuir a perda de contratos.

## 2. Estrutura do Projeto

O repositório está organizado da seguinte forma:

```
├── Telecom2.ipynb
├── README.md
├── Dlimp.csv
```

- **Telecom2.ipynb`**: O notebook principal contendo todo o código e a análise da Parte 2, desde o carregamento dos dados até a conclusão estratégica.
- **README.md`**: Este arquivo, com a documentação do projeto.

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

## 5. Instruções para Execução

Para executar este projeto, siga os passos abaixo:

**Bibliotecas Necessárias:**
Certifique-se de ter as seguintes bibliotecas Python instaladas:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

**Executando o Notebook:**
1. Clone este repositório do GitHub.
2. Abra o arquivo `Telecom2.ipynb` em um ambiente como Jupyter Notebook ou Google Colab.
3. O notebook está configurado para carregar o arquivo `Dlimp.csv` diretamente da URL "Raw" do GitHub, então não é necessário fazer o upload manual dos dados. Apenas execute as células em sequência.
