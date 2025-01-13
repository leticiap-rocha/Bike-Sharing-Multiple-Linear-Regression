# BIKE SHARING - Compartilhamento/aluguel de Bicicletas
![image](https://github.com/user-attachments/assets/da3ba259-dbba-437e-b4bb-bdc9ed53ddbf)

## 1. Descrições e informações do projeto
- Este projeto foi retirado da página de [Gaurav Dutta](https://www.kaggle.com/code/gauravduttakiit/bike-sharing-multiple-linear-regression), no Kaggle.
- No notebook, inseri anotações de pesquisas provenientes de dúvidas que surgiam.
- Este é um projeto em que se há várias variáveis independentes disponíveis e que se busca entender quais delas são significativas na previsão de demandas por aluguel de biciletas.
- Este é um projeto de Machine Learning utilizando Regressão Linear para prever de que forma as variáveis impactam na quantidade de bicicletas alugadas.

## 2. Tecnologias e ferramentas
- Para o projeto foram utilizados: Anaconda Navigator, Jupyter Notebook, Python (Numpy, Pandas, Matplotlib, Seaborn, Scikit Learn, Statsmodels), estatítica e o algoritmo supervisionado de aprendizado de máquina Regressão linear.

## 3. Descrição do Problema e Objetivo
- A BikeIndia, um fornecedor norte-americano de aluguéis de bicicletas, sofreu quedas consideráveis nas suas receitas devido à pandemia de Corona e aspira compreender a procura de bicicletas partilhadas;
- A empresa quer compreender quais os fatores que afetam a procura destas bicicletas no mercado americano;
- Além disso, gostaria de responder à pergunta: Quais variáveis são significativas na previsão da demanda por bicicletas compartilhada?
- O objetivo é modelar a demanda por bicicletas alugadas com as variáveis independentes disponíveis. Dessa forma, a gerência poderá manipular a estratégia de negócios para atender aos níveis de demanda e às expectativas dos clientes. Além disso, o modelo será uma boa maneira de entender a dinâmica da demanda de um novo mercado.

## 4. Fluxo do Projeto
- Definir o problema e objetivo do negócio;
- Coletar os dados e obter uma visão geral (análise exploratória de dados);
- Verificar a qualidade dos dados (Limpeza e Tratamento de Dados);
- Dividir os dados em conjuntos de treinamento e teste;
- Explorar os dados tratados (análise exploratória de dados);
- Treinamento de modelos, comparação, seleção de características e ajuste fino;
- Teste e avaliação do modelo de produção final;
- Concluir e interpretar os resultados do modelo.

*Cada etapa é explicada em detalhes dentro do notebook.*

## 5. Estrutura do Repositório
**Imagens:**  Contém as imagens utilizadas neste storytelling <br/>
**Input:** Contém os dados brutos utilizados como entrada <br/>
**Notebook:** Contém o notebook Jupyter desenvolvido <br/>

## 6. Informações Gerais das variáveis utilizadas
- **Variáveis Numéricas**
  - **temp:** Temperatura em Celsius         
  - **atemp:** Sensação térmica em Celsius        
  - **hum:** Umidade relativa          
  - **windspeed:** Velocidade do vento    
  - **cnt:** Contagem total de bicicletas alugadas (ESTA SERÁ A VARIÁVEL DEPENDENTE)
- **Variáveis Categóricas**
  - **season:** Estação do ano (1:primavera; 2:verão; 3:outono; 4:inverno)        
  - **yr:** Ano (0: primeiro ano; 1: segundo ano)            
  - **mnth:** Meses do ano (1 a 12)          
  - **holiday:** Feriados (0: Não feriado; 1: Feriado)      
  - **weekday:** Dias da semana [0 (domingo) a 6 (sábado)]      
  - **workingday:** Dia útil (0: Feriados e finais de semana; 1: Dia útil)     
  - **weathersit:** Condição do tempo (1: claro, poucas nuvens; 2: neblina + nuvens; 3: chuva leve + tempestade + nuvens; 4: chuva pesada + gelo + tempestade + neblina)   

## 7. Principais Insights sobre os aluguéis de bicicletas

**Sobre as variáveis numéricas, destaca-se:**
![image](https://github.com/leticiap-rocha/Bike-Sharing-Multiple-Linear-Regression/blob/main/Imagens/pairplot%20vari%C3%A1veis%20num%C3%A9ricas.jpg)
    - A distribuição de cada variável individualmente (pelos gráficos KDE na diagonal); 
    - As distribuições das variáveis **hum** e **windspeed** aproximam-se de uma normal;
    - É possível notar uma relação linear entre 'temp','atemp' e 'cnt'.

**Sobre as variáveis categóricas, destaca-se:**

*Considerando a variável 'Season' em relação à 'cnt':*

![image](https://github.com/leticiap-rocha/Bike-Sharing-Multiple-Linear-Regression/blob/main/Imagens/Season%20x%20Cnt.jpg)

  - A mediana dos aluguéis varia consideravelmente entre as estações. A menor é na "season 1" (cerca de 2.000) e a maior na "season3"(acima de 5.000);
  - A "season 1" possui a maior amplitude interquartil (altura da caixa), o que sugere maior variabilidade nos alugueis;
  - Há outliers na "season 1" e na "season 4";
  - As observaações sugerem que as estações do ano afetam fortemente o comportamento dos usuários em relação ao aluguel de bibicleta, com um pico de demanda no verão e menor atividade no inverno.

*Considerando a variável 'Weathersit' em relação à 'cnt':*

![image](https://github.com/leticiap-rocha/Bike-Sharing-Multiple-Linear-Regression/blob/main/Imagens/Weathersit%20x%20cnt.jpg) 

 - A mediana de aluguéis varia substancialmente entre as diferentes condições climáticas. Isso indica que a situação climática é um forte preditor do comportamento de aluguel;
 - O maior número de aluguéis ocorre na condição climática 1. A mediana está próxima e 5.000 e os valores variam amplamente, chegando a um máximo de cerca de 9.000. Indicando que dias ensolarados ou com poucas nuvens são os mais favoráveis para usuários alugarem bicicletas;
 - Na condição climática 2, a mediana dos aluguéis cai para cerca de 4.000. A distriuição ainda é razoavelmente ampla, mas o número de aluguéis geralmente menor que da condição climática 1. Indica que, embora condições levemente desfavoráveis (como céu nublado) reduzem a demanda, mas o impacto não é tão drástico quanto em condições de chuva;
 - Para a condição climática 3, a mediana despenca para cerca de 2.000. Além disso, a faixa interquartil é bem mais compacta, sugerindo uma menor variabilidade no número de aluguéis. Isso indica que em dias de chuva ou neve, a maioria dos usuários tendem a evitar o uso das bicicletas, resultando em um número consistentemente baixo de aluguéis;
 - Esta variável impacta fortemente a demanda por bicicletas.

*Considerando a variável 'Workingday' em relação à 'cnt':*

![image](https://github.com/leticiap-rocha/Bike-Sharing-Multiple-Linear-Regression/blob/main/Imagens/workingday%20x%20cnt.jpg)

  - A mediana para ambos os grupos é muito próxima, por volta de 4.000 aluguéis. Isso sugere que a demanda mediana por bicicletas é relativamente constante, independente de ser dia útil ou não;
  - A caixa azul (dia não útil) é um pouco maior que a laranja (dia útil), indicando que há maior variabilidade na demanda em dias não úteis. Isso pode ocorrer porque o uso nos fins de semana e feriados tende a ser mais imprevisível e influenciado por fatores como eventos e climas. Em dias úteis, a demana é um pouco mais consistente, possivelmetne devido ao uso regular para deslocamentos diários;
  - Os bigodes (duas linhas fora das caixas) são quase idênticos para os dois grupos, sugerindo que os valores máximos e mínimos são semelhantes em ambos os senários;
  - A variável workingday parece ser relevante para a previsão de demanda, pois afeta a consistência e previsibilidade dos aluguéis. No entanto, como as medidas são muito próximas, esta variável por si só pode não ser suficiente para prever grandes diferenças na demanda. Por isso, é importante combiná-la com outras variáveis de forma a capturar padrões mais complexos.

*OBS: Os insights sobre as outras variáveis encontram-se no notebook*


## 8. Modelagem 
#### 1. Limpeza dos dados:
- Foi checada a existência de dados nulos, faltantes e duplicados;
- Foram removidas as colunas redundantes e indesejadas (instant, dteday, casual e registered).

#### 2. Redimensionamento dos recursos:
- Foram criadas variáveis Dummy's para 4 categorias: 'mnth', 'weekday', 'season' & 'weathersit', transformando-as de variáveis categóricas para numéricas;
- Divisão dos dados em treino e teste na proporção 70/30;
- Ajuste dos valores de treino utilizando o MinMaxScaler() para que fiquem dentro de uma determinada faixa (entre 0 e 1).

#### 3. Construção do Modelo Linear
- Os dados foram divididos em X e Y. A variávei "cnt" é a dependente, portanto o Y, e as demais variáveis são X;
- Recursive Feature Elimination - RFE:
  - Foi utilizada a funçao LinearRegression do Scikit Learn por sua compatibilidade com o RFE
  - O RFE é uma técnica de seleção de características (ou variáveis) usada em Machine Learning para escolher as características mais importantes de um conjunto de dados;
  - O objetivo do RFE é reduzir o número de variáveis utilizadas no modelo, mantendo o desempenho ou até melhorando-o, eliminando características irrelevantes ou redundantes;
  - O processo de RFE envolve recursivamente treinar o modelo, avaliando a importância das características e eliminando as menos importantes até que o número desejado de características seja atingido;
  - Foi utilizado o rfe.ranking, um atributo do RFE após o ajuste, que fornece o ranking de importância das features(valor 1, a feature tem o maior grau de relevância). Quanto maior o número, menos relevante a feature foi considerada.
- VIF Check:
  - O VIF check refere-se ao cálculo do Variance Inflation Factor (VIF);
  - É usado para verificar a presença de multicolinearidade entre as variáveis independentes em um modelo de regressão;
  - A multicolinearidade ocorre quando duas ou mais variáveis explicativas estão altamente correlacionadas, o que pode distorcer os coeficientes do modelo e dificultar a interpretação dos resultados;
  - Interpretação:
    - VIF = 1: Não há correlação entre a variável i e as outras variáveis independentes;
    - 1 < VIF < 5: Existe uma correlação moderada, mas geralmente não é problemática;
    - VIF > 5: Indica uma correlação potencialmente preocupante, podendo haver multicolinearidade;
    - VIF > 10: Multicolinearidade severa, indicando que a variável está altamente correlacionada com outras variáveis e deve ser investigada ou removida.
- Modelo linear usando 'STATS MODEL":
   - Os modelos de regressão foram criados utilizando o método de Mínimos Quadrados Ordinários (OLS - Ordinary Least Squares);
   - Após construção do modelo 1, foram avaliados os resultados do valor p e VIF;
   - Resultados do VIF - Modelo 1:

![VIF do modelo 1](https://github.com/user-attachments/assets/851a330d-46b9-43a5-9c4b-a65b168a0beb)

  - Relatório de Regressão - Modelo 1:

![Relatório Regressão do modelo 1](https://github.com/user-attachments/assets/eed64980-6527-41af-bd1c-c20706a21c83)
   - Considerando o alto p-value e o alto VIF, foi removida a variável 'atemp' antes da criação do modelo 2;
   - Para o modelo 3 foi removida a variável *'hum'*, baseando-se em seu alto valor VIF;
   - Para o modelo 4 foi removida a variável *'season3'* baseando-se em seu alto valor VIF;
   - Para o modelo 5 foi removida a variável  *'mnth_10'* baseando-se em seu alto valor p;
   - Para o modelo 6 foi removida a variável  *'mnth_3'* baseando-se em seu alto valor p;
   - O modelo 6 foi o último e considerado bom, já que Todos os VIF são maiores que 1 e menores que 5.

    - Resulados do VIF - Modelo 6:

![VIF do Modelo 6](https://github.com/user-attachments/assets/d3b43fea-e15b-4f25-979b-c617ddb9f5a2)

   - Relatório de Regressão - Modelo 6:

![Relatório Regressão modelo 6](https://github.com/user-attachments/assets/c9fafe1f-6465-47bb-84a2-4295a17018a9)

  #### 4. Interpretação do Modelo Final
- De acordo com o Teste de Hipóteses, como nenhum coeficiente = 0, rejeitou-se a hipótese nula;
- Foi utilizado o F-Statistics  para testar a significância geral do modelo (quanto maior o F-Statistics, maior é a significância do modelo). O valor de 233 (muito maior que 1) do F-Statistics e o p-valor de '~0.0000' afirma que no geral o modelo é significante.
- A equação da superfície mais bem ajustada com base no modelo 6:
   - cnt = 0.084143 + (yr × 0.230846) + (workingday × 0.043203) + (temp × 0.563615) − (windspeed × 0.155191) + (season2 × 0.082706) + (season4 ×0.128744) + (mnth9 × 0.094743) + (weekday6 ×0.056909) − (weathersit2 × 0.074807) − (weathersit3 × 0.306992)
- Interpretação de alguns coeficientes:
    - **temp:** Um valor de coeficiente de “0,5636” indicou que um aumento unitário na variável temp aumenta o número de aluguel de bicicletas em 0,5636 unidades.
    - **weathersit_3:** Um valor de coeficiente de “-0,3070” indica que, em relação a Weathersit1, um aumento de uma unidade na variável Weathersit3 diminui o número de aluguel de bicicletas em 0,3070 unidades.
    - **const:** O valor constante de '0,084143' indicou que, na ausência de todas as outras variáveis preditoras (ou seja, quando x1,x2...xn =0), o aluguel de bicicletas ainda pode aumentar em 0,084143 unidades.
- Análise Residual dos dados de treinamento:
![image](https://github.com/leticiap-rocha/Bike-Sharing-Multiple-Linear-Regression/blob/main/Imagens/An%C3%A1lise%20dos%20res%C3%ADduos.jpg)
- Os resíduos são normalmente distribuídos. Portanto, a suposição de regressão linear é válida.
- Relação Linear entre X e Y:
![Relação Linear entre X e Y](https://github.com/user-attachments/assets/6fb4c4c9-31f1-4665-a274-42e76c638058)
- Há uma relação linear entre as variáveis temp e atemp com o preditor 'cnt'.
- Análise da Multicolinearudade entre as variáveis preditoras:
![image](https://github.com/user-attachments/assets/861b53c6-5154-4540-94db-739a1acac9ab)
- A partir do cálculo do VIF, constatamos que não há multicolinearidade entre as variáveis preditoras, pois todos os valores estão dentro da faixa permitida (menores que 5).

#### 5. Previsões usando o modelo final
- Após os ajustes e checagem das pressuposições do modelo 6, iniciou-se as previsões com este modelo.
- Aplicou-se o dimensionamento nos conjuntos de teste:
  - Foi utilizado o scaler() a todas as variáveis numéricas no conjunto de dados de teste;
  - Usou-se apenas scaler.transform para usar as métricas que o modelo aprendeu com os dados de treinamento a serem aplicados nos dados de teste. Dessa forma, buscou-se evitar o vazamento de informações do conjunto de dados de treinamento para o de teste.
![y_test e y_pred](https://github.com/user-attachments/assets/50ff918f-9fbf-4d3e-8de4-89f6472b8d9c)
- Comparação dos resultados finais:
  - R² treino: 0.824
  - R² treino ajustado: 0.821
  - R² test: 0.820
  - R² ajustado: 0.812
  - Os valores indicaram que parece ser um modelo muito bom que pode generalizar muito bem em vários conjuntos de dados.

## 9. Relatório final
- De acordo com o nosso modelo final (modelo 6), as 3 principais variáveis de previsão que influenciam a reserva de bicicletas são:
    - **Temperatura (temp):*** Um valor de coeficiente de '0,5636' indica que um aumento unitário na variável *temp* aumenta o número de aluguel de bicicletas em 0,5636 unidades.
    - **Situação meteorológica 3 (weathersit_3):** Um valor de coeficiente de '-0,3070' indica que, em relação a *Weathersit1*, um aumento unitário na variável Weathersit3 diminui o número de aluguel de bicicletas em 0,3070 unidades.
    - **Ano (yr):** Um valor de coeficiente de “0,2308” indica que um aumento unitário na variável *yr* aumenta o número de aluguer de bicicletas em 0,2308 unidades.
- Sugere-se que considere essas 3 variáveis de extrema importância durante o planejamento, para atingir o máximo de aluguéis.
- As próximas melhores caraterísticas que também podem ser consideradas são:
    - **season_4:** Um valor de coeficiente de “0,128744” indica que, em relação à época_1, um aumento unitário na variável *season_4* aumenta o número de aluguel de bicicletas em 0,128744 unidades.
    - **windspeed:** Um valor de coeficiente de '-0,155191' indica que, um aumento unitário na variável velocidade do vento diminui o número de aluguel de bicicletas em 0,155191 unidades.
