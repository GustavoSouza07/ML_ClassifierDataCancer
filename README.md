## Aplicação do Machine Learning (classificação)
base de dados: https://www.kaggle.com/datasets/erdemtaha/cancer-data   

O objetivo é aplicar alguns algoritmos de classificação de modo que possamos prever o resultado da variável "Diagnosis". 

Algumas variáveis que contém uma correlação forte com a variável alvo são denominadas previsoras, através da análise de correlação.

variável alvo: diagnosis
Cancer Types:
1. Benign cancer (B)
2. Malignant cancer (M)

## Pré processamento de dados
No pré processamento dos dados é feito inicialmente a separação dos previsores e do alvo.

Em seguida pelo alto número de variáveis previsores é feito a redução de dimensionalidade.

A partir da redução de dimensionalidade, é feito o escalonamento (padronização) das variáveis com dimensionalidade reduzida.

### Previsores e alvo
- alvo: variável com transformação categorica ordinal
- previsores: variável previsores sem nenhum pré processamento
- previsores_esc: variável previsores com escalonamento (padronização)
- previsores_decompose: variável previsores com redução de dimensionalidade --> n_components=10,random_state=0
- previsores_escDecompose: variável previsores_decompose com escalonamento (padronização)


### Resultados algoritmos de classificação
- Naive Bayes (previsores_decompose): teste - 91.22% / treino - 88.69% / validação cruzada - 89.10% 

- Maquina vetor de suporte (previsores_decompose): teste - 92.39% / treino - 92.71% / validação cruzada - 92.05% 

- KNN (previsores): teste - 92.39% / treino - 94.22% / validação cruzada - 93.22% 

- Árvore de decisão (previsores_decompose): teste - 91.22% / treino - 93.21% / validação cruzada - 92.03%

- Random Florest (previsores_decompose): teste - 91.81% / treino - 94.47% / validação cruzada - 92.61%

- XgBoost (previsores_decompose): teste - 92.39% / treino - 96.23% / validação cruzada - 94.05%


### Avaliação dos resultados
Todos os algoritmos de classificação que foram testados, estão fora de overffiting (Resultados melhores nos dados de treino e inferiores nos dados de teste). Obtendo resultados semelhantes e adequados aos previsores com dimensionalidade reduzida.

Os dois melhores algoritmos dos 6 algoritmos de classificação avaliados foram :
- KNN
- XgBoost

configuração do algoritmo

- knn = KNeighborsClassifier(n_neighbors=5,metric='minkowski',p=2,weights='uniform')

- xgb = XGBClassifier(learning_rate=0.01,n_estimators=300,objective='binary:logistic',max_depth=2,random_state=0)

### Testes conduzidos
Foram realizados dois tipos de testes, teste randômico (dados de entrada aleatórios/gerados por ia) e teste com dados reais para comparação (dados do arquivo dos previsores indicados para o determinado algoritmo).

Os testes indicaram uma boa comparação dos dois algoritmos, assim como também uma boa eficiência.

### Conclusão
O algoritmo XgBoost se torna mais eficiente que o KNN na classificação, pelo fato da sua acurácia ser maior e também por se tratar de um algoritmo baseado em árvores de decisão. 
