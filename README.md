# Lighthouse Challenge


![istockphoto-908031820-612x612](https://github.com/Eduardo-95-DS/lighthouse-challenge/assets/95311171/d35dcf8b-f413-4fa9-9df3-28e84326be1f)

**Para instalar e executar o projeto, é recomendado que se crie um ambiente virtual (com pyenv por ex) com python versão 3.10.4, baixe o repositório localmente e instale as bibliotecas necessárias com o comando pip install -r requirements.txt dentro da pasta do projeto.**      

**Para visualizar rapidamente os resultados, pode-se usar o notebook look_4.0-ear-model_apply.ipynb, que contém apenas os códigos necessários para treinar o modelo, fazer o cross validation, prever os dados de teste (com o modelo carregado em pickle já com os melhores parâmetros) e obter os resultados de negócio.**    

**A EDA completa pode ser encontradas no notebook look_2.0-ear-eda_data-preparation.ipynb, e as entregas completas na última seção dos notebooks
look_4.0-ear-hp_tuning-error_analysis.ipynb ou look_4.0-ear-model_apply.ipynb**

# **1. Business problem**
Você foi alocado(a) em um time da Indicium que está trabalhando atualmente junto a um cliente no processo de criação de uma plataforma de aluguéis temporários na cidade de Nova York. Para o desenvolvimento de sua estratégia de precificação, pediu para que a Indicium fizesse uma análise exploratória dos dados de seu maior concorrente, assim como um teste de validação de um modelo preditivo.    

Seu objetivo é desenvolver um modelo de previsão de preços a partir do dataset oferecido, e avaliar tal modelo utilizando as métricas de avaliação que mais fazem sentido para o problema.        

Entregas:
- Faça uma análise exploratória dos dados (EDA), demonstrando as principais características entre as variáveis e apresentando algumas hipóteses de negócio relacionadas. Seja criativo!
  
- Responda também às seguintes perguntas:
  
- Supondo que uma pessoa esteja pensando em investir em um apartamento para alugar na plataforma, onde seria mais indicada a compra?

- O número mínimo de noites e a disponibilidade ao longo do ano interferem no preço?   

- Existe algum padrão no texto do nome do local para lugares de mais alto valor?    

- Explique como você faria a previsão do preço a partir dos dados. 
Quais variáveis e/ou suas transformações você utilizou e por quê?    
Qual tipo de problema estamos resolvendo (regressão, classificação)?    
Qual modelo melhor se aproxima dos dados e quais seus prós e contras?     
Qual medida de performance do modelo foi escolhida e por quê?

- Supondo um apartamento com as seguintes características:

{'id': 2595,
 'nome': 'Skylit Midtown Castle',
 'host_id': 2845,
 'host_name': 'Jennifer',
 'bairro_group': 'Manhattan',
 'bairro': 'Midtown',
 'latitude': 40.75362,
 'longitude': -73.98377,
 'room_type': 'Entire home/apt',
 'price': 225,
 'minimo_noites': 1,
 'numero_de_reviews': 45,
 'ultima_review': '2019-05-21',
 'reviews_por_mes': 0.38,
 'calculado_host_listings_count': 2,
 'disponibilidade_365': 355}

Qual seria a sua sugestão de preço?     

Salve o modelo desenvolvido no formato .pkl.       

- A entrega deve ser feita através de um repositório de código público que contenha:
     
  README explicando como instalar e executar o projeto   
  Arquivo de requisitos com todos os pacotes utilizados e suas versões   
  Relatórios das análises estatísticas e EDA em PDF, Jupyter Notebook ou semelhante conforme passo 1 e 2.    
  Códigos de modelagem utilizados no passo 3 (pode ser entregue no mesmo Jupyter Notebook).    
  Arquivo .pkl conforme passo 5 acima.    
Todos os códigos produzidos devem seguir as boas práticas de codificação.
 

# **2. Business assumptions**
The assumptions about the business problem are as follows:       
- Days with stores closed and/or zero sales were not taken into account.       
- Stores without close competitors had the distance fixed at 200000, which is a lot higher than other distances, as a way of preserving the rows, instead of deleting them.   



# **3. Solution strategy**
- Step 01. Data description: My goal is to use statistics metrics to identify data outside the scope of business.   

- Step 02. Feature engineering: Derive new attributes based on the original variables to better describe the phenomenon that will be modeled.    

- Step 03. Data filtering: Filter rows and select columns that do not contain information for modeling or that do not match the scope of the business.   

- Step 04. Exploratory data analysis: Explore the data to find insights and better understand the impact of variables on model learning.   

- Step 05. Data preparation: Prepare the data so that the Machine Learning models can learn the specific behavior.   

- Step 06. Feature selection: Selection of the most significant attributes for training the model.   

- Step 07. Machine learning modelling: Machine Learning model training.   

- Step 08. Hyperparameter fine tunning: Choose the best values for each of the parameters of the model selected from the previous step.   

- Step 09. Convert model performance to business values: Convert the performance of the Machine Learning model into a business result.   

- Step 10. Deploy model to production: Publish the model in a cloud environment so that other people or services can use the results to improve the business decision.   


# **4. Top 3 data insights**
**Hypothesis 01:** Stores with greater assortments should sell more.   
**True.** As observed, the extra assortment sells more, followed by extended and basic, in that order.       

<!---![Screenshot from 2023-06-19 21-32-36](https://github.com/Soturno95/Rossmann-sales-prediction/assets/95311171/533284b2-9781-4160-afd8-3010c5366834)-->
![1](https://github.com/Eduardo-95-DS/Rossmann-sales-prediction/assets/95311171/aba06611-730d-4d61-acd5-b72b97e99104)
![2](https://github.com/Eduardo-95-DS/Rossmann-sales-prediction/assets/95311171/d3ed406b-afc8-444f-a9f5-b563b5942db5)


**Hypothesis 02:** Stores with closer competitors should sell less.      
**False.** As observed, the distance between stores doesn't affect the sales.
![3](https://github.com/Eduardo-95-DS/Rossmann-sales-prediction/assets/95311171/7846f196-6527-47ce-9516-f568fb0f736e)



**Hypothesis 06:** Stores with consecutive promotions should sell more.         
**True.** As observed, consecutive promotions increase sales.    
![4](https://github.com/Eduardo-95-DS/Rossmann-sales-prediction/assets/95311171/06b1a64c-cb65-4280-b4f2-29c8c1aae7a5)



# **5. Machine learning model applied**   
Tests were made using different algorithms.     

| Model name | MAE | MAPE | RMSE | 
|-----------|---------|-----------|---------|
| CatBoost Regressor   | 987.056237 | 0.143865  | 1412.787567 | 
| Average Model	|1354.800353|	0.455051|	1835.135542 |
| XGBoost Regressor	|1713.183272	|0.261204|	2449.559832
| Random Forest Regressor|	1956.270109	|0.297115|	2837.878419|
| Linear Regression	|2057.384627	|0.301612	|3039.636280|
| Linear Regression - Lasso|	2198.584167|	0.342759	|3110.514747|

# **6. Machine learning model performance**
The chosen algorithm was the CatBoost Regressor. In addition, I made a performance calibration on it.   

These are the metrics obtained from the test set.

| Model name | MAE | MAPE | RMSE | 
|-----------|---------|-----------|---------|
| CatBoost Regressor   | 987.056237 | 0.143865  | 1412.787567 | 

The summary below shows the metrics comparison after running a five fold cross validation without and with tuned hyper parameters.   

| Model name | MAE | MAPE | RMSE | 
|-----------|---------|-----------|---------|
| CatBoost Regressor (CV)  | 1003.69 +/-163.91	 |0.14 +/-0.01  | 1454.77 +/-248.75 | 
| CatBoost Regressor (CV + Tuned HP) | 900.86 +/-84.27| 0.12 +/-0.01  | 1300.25 +/-147.89 | 

# **7. Business results**
In the dataset, there were 1115 different stores; if we take into account the mean absolute error of the predictions from all stores using the average model, which uses a simple mean of all stores to predict sales, it leads to a **€1,509,710** miscalculation, while the algorithm gets to a total of **€978,970** mean absolute error, a difference of **€530,740**.    

Here's an example of a six weeks predictions from the five stores with the more accurate predictions ; predictions are the total sales of a giving store, while worst and best scenarios are the possible under and over estimations based on MAE, the mean absolute error.    


|store|	predictions	|worst_scenario|	best_scenario|	MAE	|MAPE|
|--------|-----------|-----------|------------|--------------|----------|
|1098	|€186,619.22	|€186,337.23	|€186,901.21	|281.990104	|0.055884
|523	|€495,993.58	|€495,219.52	|€496,767.64	|774.063158	|0.056405
|981	|€256,660.41	|€256,274.28	|€257,046.54	|386.131729|	0.056915
|875	|€183,020.81	|€182,758.53	|€183,283.08	|262.276640	|0.058730
|489	|€265,813.56	|€265,286.71	|€266,340.41	|526.850079|	0.059235

This would be the possible scenarios from all the stores in six week's advance:   
|Scenario	|Values|
|---------|-------|
|predictions	|€277,707,021.57|
|worst_scenario	|€276,725,465.55|
|best_scenario	|€278,688,577.58|

# **8. Conclusions**
The project successfully solved the two initial problems; the automatization of the predictions with a good precision and a way for the CFO to consult those in a simple and accesible fashion.

# **9. Lessons learned**   
- Develop solutions in a ciclical way
- Build a telegram bot
- Prioritize tasks   
