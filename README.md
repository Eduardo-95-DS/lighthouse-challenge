# Lighthouse Challenge


![istockphoto-908031820-612x612](https://github.com/Eduardo-95-DS/lighthouse-challenge/assets/95311171/d35dcf8b-f413-4fa9-9df3-28e84326be1f)

**Para instalar e executar o projeto, é recomendado que se crie um ambiente virtual (com pyenv por ex) com python versão 3.10.4, baixe o repositório localmente e instale as bibliotecas necessárias com o comando pip install -r requirements.txt dentro da pasta do projeto.**      

**Para implementar rapidamente o modelo, pode-se usar o notebook look_5.0-ear-model_apply.ipynb, que contém apenas os códigos necessários para treinar o modelo, fazer o cross validation ou prever os dados de teste com o modelo carregado em pickle já com os melhores parâmetros, e obter os resultados de negócio.**    

**A EDA completa pode ser encontradas no notebook look_2.0-ear-eda_data-preparation.ipynb, e as ENTREGAS completas na última seção dos notebooks
look_4.0-ear-hp_tuning-error_analysis.ipynb ou look_5.0-ear-model_apply.ipynb.**

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

As premissas sobre o problema de negócio foram as seguintes:       

-   Presume-se que id e host_id são gerados aleatoriamente, portanto não possuem nenhuma importância na previsão dos preços.
-   Os preços igual a zero, seja por erro de input ou por escolha do proprietário para talvez negociar com os interessados, foram substituídos por preços levando em conta a localização e o tipo de acomodamento.  

# **3. Solution strategy**
- Step 01. Data description: Usar métricas estatísticas para entender os dados. 

- Step 02. Feature engineering: Derivar novos atributos com base nas variáveis ​​originais para melhor descrever o fenômeno que será modelado.    

- Step 03. Data filtering: Filtrar linhas e colunas que não contenham informações para modelagem ou que não correspondam ao escopo do negócio.   

- Step 04. Exploratory data analysis: Explorar os dados para encontrar insights e compreender melhor o impacto das variáveis ​​no aprendizado do modelo.   

- Step 05. Data preparation: Preparar os dados para que os modelos de Machine Learning possam aprender o comportamento específico.
  
- Step 06. Feature selection: Seleção dos atributos mais significativos para treinamento do modelo.   

- Step 07. Machine learning modelling: Treinamento do modelo de aprendizado de máquina.

- Step 08. Hyperparameter fine tunning: Escolha os melhores valores para cada um dos parâmetros do modelo selecionado na etapa anterior.   

- Step 09. Convert model performance to business values: Converter o desempenho do modelo de Machine Learning em resultado de negócio.   

- Step 10. Entregas: Responder às requisições. 

# **4. Top 3 data insights**

**Hypothesis 01:**  
 **Manhattan tem em média preços pelo menos 30% maiores**    
 ***Verdadeiro***
 ![1](https://github.com/Eduardo-95-DS/lighthouse-challenge/assets/95311171/34feae45-edc9-4fde-bbb6-a6d897afc39b)    
 
A diferença percentual da média de Manhattan em relação às outras cidades:

  |bairro_group|  diff_percent|   
  |-----------|---------|
  |Manhattan      ||
  |Brooklyn   |-36.945324|
  |Staten Island    |-41.158341|
  |Queens    |-49.250131|
  |Bronx    |-55.832950|
 
**Hypothesis 02:**       
**Room type do tipo 'Entire home/apt' são pelo menos 100% mais caros em média**    
***Falso***    
![2](https://github.com/Eduardo-95-DS/lighthouse-challenge/assets/95311171/9649db69-18ed-45e7-a002-3cca73b096c2)   

  |room_type |  diff_percent|   
  |-----------|---------|
  |Entire home/apt       ||
  |Private room    |-57.714187|
  |Shared room    |-67.184348|

**Hypothesis 03:**  
 **Aluguéis disponíveis por no máximo uma semana são pelo menos 30% mais caros em média**         
 ***Falso***       
![3](https://github.com/Eduardo-95-DS/lighthouse-challenge/assets/95311171/d5b79a60-2015-436a-aea5-f09127fc73af)

A média do preço para minimo_noites até 7 é: **154.79**    
A média do preço para minimo_noites maior que 7 é: **147.16**    
A diferença percentual é: **-5.18%**     

# **5. Machine learning model applied**      
Os testes foram feitos testando cinco algoritmos e um modelo baseline baseado na média.   
O modelo escolhido para realizar a etapa de fine-tuning e previsão em cima dos dados de teste foi o **CatBoostRegressor**, com base em sua performance no cross validation.     
A principal métrica foi o MAE (erro médio absoluto); o MAPE(erro médio percentual absoluto) e o RMSE(Erro Quadrático Médio) foram utilizados para auxiliar no desenvolvimento dos modelos. 

# **6. Machine learning model performance**
Performance final dos modelos no cross validation:        
| Model name | MAE | MAPE | RMSE | 
|-----------|---------|-----------|---------|
| CatBoost    | 53.207368	 | 0.316628 | 152.662339 | 
| XGBoost 	|53.982947	|	0.324878|	152.752383 |
| Random Forest 	|	54.361176	|0.329452|	153.149289
| Linear Regression|	58.506377		|0.351993|	162.392385|
| Lasso|80.413548	|0.606918	|181.342764|
| Baseline model|88.610938|	0.872001	|178.589160|

Performance do modelo escolhido sobre os dados de teste após a escolha dos melhores parâmetros(fine-tuning):    
| Model name | MAE | MAPE | RMSE | 
|-----------|---------|-----------|---------|
|	CatBoost	|51.78667	|0.30798	|159.667159|

# **7. Business results**

# **8. Conclusions**
O objetivo principal do projeto que era criar um modelo para prever os preços pode ser considerado concluído com sucesso.

# **9. Next steps to improve**   
- Realizar a tunagem nos modelos XGBoost e RandomForest.    
- Tentar realizar novamente criação de features.    
- Colocar o modelo em produção junto de alguma ferramenta de visualização. 

