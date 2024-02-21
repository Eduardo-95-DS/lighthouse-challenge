# Lighthouse Challenge


![istockphoto-908031820-612x612](https://github.com/Eduardo-95-DS/lighthouse-challenge/assets/95311171/d35dcf8b-f413-4fa9-9df3-28e84326be1f)

**Para instalar e executar o projeto, é recomendado que se crie um ambiente virtual (com pyenv por ex) com python versão 3.10.4, baixe o repositório localmente e instale as bibliotecas necessárias com o comando pip install -r requirements.txt dentro da pasta do projeto.**      

**Para visualizar rapidamente os resultados, pode-se usar o notebook look_4.0-ear-model_apply.ipynb, que contém apenas os códigos necessários para treinar o modelo, fazer o cross validation, prever os dados de teste (com o modelo carregado em pickle já com os melhores parâmetros) e obter os resultados de negócio.**    

**A EDA completa pode ser encontradas no notebook look_2.0-ear-eda_data-preparation.ipynb, e as entregas completas na última seção dos notebooks
look_4.0-ear-hp_tuning-error_analysis.ipynb ou look_5.0-ear-model_apply.ipynb**

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
-   
-   

# **3. Solution strategy**
- Step 01. Data description: Usar métricas estatísticas para entender os dados. 

- Step 02. Feature engineering: Derivar novos atributos com base nas variáveis ​​originais para melhor descrever o fenômeno que será modelado.    

- Step 03. Data filtering: Filtrar linhas e colunas que não contenham informações para modelagem ou que não correspondam ao escopo do negócio.   

- Step 04. Exploratory data analysis: Explorar os dados para encontrar insights e compreender melhor o impacto das variáveis ​​no aprendizado do modelo.   

- Step 05. Data preparation: Preparar os dados para que os modelos de Machine Learning possam aprender o comportamento específico.
- 
- Step 06. Feature selection: Seleção dos atributos mais significativos para treinamento do modelo.   

- Step 07. Machine learning modelling: Treinamento do modelo de aprendizado de máquina.

- Step 08. Hyperparameter fine tunning: Escolha os melhores valores para cada um dos parâmetros do modelo selecionado na etapa anterior.   

- Step 09. Convert model performance to business values: Converter o desempenho do modelo de Machine Learning em resultado de negócio.   

- Step 10. Entregas: Responder às requisições. 

# **4. Top 3 data insights**

**Hypothesis 01:**  

**Hypothesis 02:**       

**Hypothesis 03:**  

# **5. Machine learning model applied**   


# **6. Machine learning model performance**


# **7. Business results**

# **8. Conclusions**
O objetivo principal do projeto que era criar um modelo para prever os preços pode ser considerado concluído com sucesso.

# **9. Next steps to improve**   
- Realizar a tunagem nos modelos XGBoost e RandomForest.    
- Tentar realizar novamente criação de features.    
- Colocar o modelo em produção junto de alguma ferramenta de visualização. 

