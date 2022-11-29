# 🧬 Bank Loan Model

## 🎯 Objetivo

O objetivo desse projeto é usar um dataset de empréstimos bancários para construir um modelo de predição para possiveis inadimplências nos empréstimos, o modelo escolido foi o XGBOOST e o dataset inicial é o arquivo "datataset_bank_loan.csv" 

## ETL

- Verificação de nulos na variável resposta (default) ✔️
- Correção da tipagem dos dados ✔️
- Exclusão de registros nulos nas features ✔️
- Análise da distribuição da variável resposta x features ✔️
- Encoding dos dados ✔️
- Matriz de correlação ✔️
- Seleção final das features ✔️

O dataset final após a preparação dos dados se encontra com 88471 linhas  e 38 colunas.

## 🛠️ Construção do Modelo 

### Modelo XGBOOST

O modelo XGBoost representa uma categoria de algoritmo baseada em Decision Trees (árvores de decisão) com Gradient Boosting (aumento de gradiente).

Extremamente flexível uma vez que possui um grande número de hiperparâmetros passíveis de aperfeiçoamento você consegue ajustar adequadamente o XGBoost para o cenário do seu problema, seja ele qual for.


- Divisão entre treino e teste, como padrão foi utilizado o split entre 70 - 30

    ![CurvaROC](https://github.com/joaovbdss69/Bank-Loan-Model/blob/main/images/DivisaoTreinoTeste.png)
	
- Seleção de parâmetros do modelo
    - learning_rate 
    - gamma
    - max_depth
    - min_child_weight
    - max_delta_step
    - subsample
    - colsample
    - n_estimators
- E para atingir os melhores valores para esses parâmetros foi utilizado o BayesianOptimization

    ![BayesianOptimization](https://github.com/joaovbdss69/Bank-Loan-Model/blob/main/images/BayesianOptimization.png)

- Treinamento do Modelo com os parâmetros e seus respectivos valores

![Model](https://github.com/joaovbdss69/Bank-Loan-Model/blob/main/images/modeloXGBOOST.png)

#### Avaliação da Curva ROC 

![CurvaROC](https://github.com/joaovbdss69/Bank-Loan-Model/blob/main/images/CURVAROC.png)

A AUC junto com a curva mostra se um modelo esta overfitado, ou seja, uma das features que foram escolhidas tem um peso muito grande com a variável target.

- Como podemos ver abaixo os pesos das features no modelo em relação a target

![Variáveis](https://github.com/joaovbdss69/Bank-Loan-Model/blob/main/images/pesoVariavel.png)

Neste modelo, obtive um valor de 0.868 de AUC em treino enquanto 0.862 em teste, não tendo um valor discrepante entre esses dois valores, significa que o modelo esta acertivo e para confirmar esse ponto temos a matriz de confusão e termos algumas métricas como Acurácia e Precisão

![CurvaROC](https://github.com/joaovbdss69/Bank-Loan-Model/blob/main/images/Matrizdeconfusao.png)
