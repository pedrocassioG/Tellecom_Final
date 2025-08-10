# Análise Preditiva de Evasão de Clientes (Churn) - TellecomX2

## Descrição do Projeto

Este projeto de Data Science realiza uma análise completa sobre a evasão de clientes (churn) em uma empresa de telecomunicações fictícia, a TellecomX2. O objetivo é identificar os principais fatores que influenciam a decisão de um cliente cancelar seu serviço e construir modelos de machine learning para prever quais clientes estão em maior risco de evasão, permitindo que a empresa tome ações de retenção proativas.

## Problema de Negócio

A evasão de clientes é um dos principais desafios para empresas de serviços por assinatura, como as de telecomunicações. Adquirir um novo cliente custa significativamente mais do que reter um existente. Portanto, a capacidade de prever o churn com antecedência e entender suas causas é crucial para a saúde financeira e o crescimento sustentável do negócio.

## Metodologia Aplicada

O projeto foi estruturado seguindo um pipeline clássico de Data Science, desde a análise dos dados até a avaliação de modelos e a geração de insights:

1.  **Análise Exploratória de Dados (EDA):**
    * Carregamento e inspeção inicial do dataset `dados_tratados (1).csv`.
    * Verificação da distribuição da variável alvo (`Churn`), identificando um desbalanceamento de classes (aproximadamente 26.6% de churn).
    * Análise visual das relações entre variáveis-chave (como Tempo de Contrato e Gasto Total) e a evasão, utilizando gráficos de boxplot e dispersão.

2.  **Pré-processamento e Limpeza dos Dados:**
    * Remoção de colunas irrelevantes (`customerID`).
    * Codificação de variáveis categóricas para formato numérico utilizando *One-Hot Encoding*.
    * Tratamento de valores ausentes por meio da remoção das linhas correspondentes.

3.  **Seleção de Variáveis e Análise de Multicolinearidade:**
    * Criação de uma matriz de correlação para entender a relação entre as variáveis.
    * Seleção de features com maior correlação (positiva ou negativa, com limiar de 0.2) em relação à variável alvo `Churn_Yes`.
    * Análise iterativa de **Fator de Inflação de Variância (VIF)** para detectar e remover variáveis com alta multicolinearidade, garantindo a robustez estatística dos modelos.

4.  **Modelagem Preditiva:**
    * Divisão dos dados em conjuntos de **treino (70%)** e **teste (30%)** com estratificação para manter a proporção de classes.
    * Padronização das features numéricas com `StandardScaler`.
    * Aplicação da técnica de sobreamostragem **SMOTE** no conjunto de treino para corrigir o desbalanceamento de classes.
    * Treinamento de dois modelos de classificação:
        * **Regressão Logística**
        * **Random Forest**

5.  **Avaliação dos Modelos:**
    * Os modelos foram avaliados no conjunto de teste (não visto e não balanceado) utilizando métricas como Acurácia, ROC AUC, Matriz de Confusão, Precision, Recall e Curva Precision-Recall.

## Resultados e Insights

### Fatores de Evasão
A análise identificou os seguintes fatores como os principais preditores de churn:
* **Tipo de Contrato:** Clientes com contratos **Mês a Mês** possuem a maior taxa de evasão.
* **Tempo de Contrato (Tenure):** Clientes com **baixo tempo de casa** (novos) são muito mais propensos a cancelar.
* **Cobrança Mensal e Serviço de Internet:** **Cobranças mensais mais altas**, especialmente associadas ao serviço de **Fibra Ótica**, aumentam a probabilidade de churn.

### Desempenho dos Modelos
* A **Regressão Logística** se mostrou mais eficaz em **capturar o máximo de churners possíveis (Recall de 81%)**, sendo ideal para campanhas de retenção em massa, mesmo que isso implique em mais falsos positivos.
* O **Random Forest** apresentou maior **precisão (58%)**, sendo mais adequado para ações de retenção direcionadas e de maior custo, onde a certeza da previsão é mais importante.

## Tecnologias Utilizadas
* **Linguagem:** Python 3
* **Bibliotecas Principais:**
    * Pandas
    * NumPy
    * Matplotlib
    * Seaborn
    * Scikit-learn
    * Statsmodels
    * Imbalanced-learn
