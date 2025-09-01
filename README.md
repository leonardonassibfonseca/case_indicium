# Case Indicium: Estúdio de Hollywood chamado PProductions

 Prever qual será o próximo lançamento cinamatográfico

<img src="imagem_projeto.png" alt="Cross Selling Insurance" width="500"/>

## 1.	Problema de negócio
Este projeto apresenta uma análise abrangente do banco de dados cinematográfico com o objetivo de orientar a decisão estratégica sobre o próximo filme a ser desenvolvido pela PProductions. A abordagem combina análise exploratória de dados, modelagem preditiva e considerações de mercado para maximizar o potencial de sucesso financeiro e crítico.

## 2.	Objetivo
Orientar a PProductions sobre qual tipo de filme desenvolver a seguir, usando análise de dados e modelagem preditiva para maximizar o sucesso comercial e crítico.

## 3.	Premissas do negócio
Seguem abaixo as premissas para as variáveis abaixo: 

Interpretação da coluna Certificate (faixa etária)
 
Sistema Americano (MPAA - Motion Picture Association)

G - General Audiences: Todas as idades admitidas

PG - Parental Guidance Suggested: Algum material pode não ser adequado para crianças

PG-13 - Parents Strongly Cautioned: Algum material pode ser inadequado para menores de 13 anos

R - Restricted: Menores de 17 anos requerem acompanhante adulto

NC-17 - Adults Only: Apenas adultos (não aparece na sua lista)

fonte: https://www.motionpictures.org/film-ratings/

Sistema Indiano (CBFC - Central Board of Film Certification)

U - Unrestricted Public Exhibition: Para todas as idades

UA - Unrestricted Public Exhibition with caution: Para todas as idades, mas com aviso parental

A - Adults Only: Apenas para adultos (18+)

fonte: https://www.cbfcindia.gov.in/cbfcAdmin/

Sistema Britânico (BBFC - antigo)

U - Universal: Para todas as idades

A - Adult: Para adultos (histórico, não usado mais)

U/A - Provavelmente variação do sistema indiano

fonte: https://www.bbfc.co.uk/

Classificação de TV

TV-PG - Parental Guidance Suggested: Programa de TV com orientação parental

fonte: https://www.tvguidelines.org/

Classificações Históricas (Antigas)

Passed - Sistema antigo dos EUA (pré-1968): Filme aprovado sem restrições específicas

Approved - Similar a "Passed", indica aprovação para exibição

GP - General Public: Antiga classificação similar à PG (1970-1972)

fonte: https://www.filmsite.org/rating.html

## 4.	Estratégia adotada para solução

Passo 1 - Descrição dos dados: O objetivo deste passo é ter um entendimento inicial de como os dados estão relacionados com o problema de negócio proposto.

Passo 2 - Engenharia de variáveis: Neste passo serão criadas hipóteses relativas ao negócio e também se necessário, poderão ser criadas novas variáveis a partir das variáveis originais a fim de melhorar a qualidade dos dados facilitando seu o entendimento.

Passo 3 - Filtragem das variáveis: Nesta etapa, é realizada a filtragem das variáveis com base nas restrições do negócio, ou seja, isso significa verificar se todas as variáveis essenciais estarão disponíveis na base de dados, garantindo que as informações necessárias para o modelo ou análise estejam presentes e possam ser acessadas durante a produção. Essa verificação é crucial para evitar erros futuros e assegurar que o sistema funcione corretamente quando for implementado em um ambiente de produção. Além disso, podemos identificar variáveis redundantes ou irrelevantes, que podem ser removidas para otimizar o desempenho.
 
Passo 4 - Análise exploratória: A análise exploratória dos dados (EDA) tem como principal objetivo proporcionar uma compreensão mais aprofundada dos dados, tais como: Compreender a distribuição das variáveis numéricas e categóricas, identificar outliers (valores atípicos), correlações entre  as variáveis entre outras análises.

Passo 5 - Preparação dos dados: Neste tópico, os dados poderão ser transformados, ou seja, as variáveis categóricas poderão ser convertidas em números, as variáveis numéricas poderão ser reescalados, em outras palavras, colocadas em uma escala comum. Também neste passo, serão testados os algoritmos de machine learning para avaliação.
 
Passo 6 - Conclusão.

## 5.	Top 3 insights
Hipótese 1: Filmes mais recentes têm notas mais altas?.

Falsa: Não existe uma correlação positiva e sim uma negativa (0,179), ou seja, quanto mais velho o filme melhor é sua nota.

![Imagem](img/grafico_hipotese_1.png)

Hipótese 2: Filmes com elenco estrelado Star1 têm maior faturamento em relação aos filmes com elenco Star4?.

Falsa: Filmes com atores classificados como Star4 apresentam em média um faturamento um pouco maior frente aos atores Star1, indicando que a classificação do ator não garante um faturamento maior por si só.

![Imagem](img/grafico_hipotese_2.png)

Hipótese 3: A nota média do IMDB aumentou ao longo dos anos?.

Falsa: A nota média diminuiu ao longo dos anos.

![Imagem](img/grafico_hipotese_3.png)

## 6.	Aplicação do modelo de machine learning
Foram feitos testes com vários algoritmos de machine learning, utilizando a técnica de cross-validation e ajuste fino dos parâmetros.

![Imagem](img/comparativo_algoritmos.png)

## 7.	Performance do modelo de machine learning
O RandomForestRegressor foi selecionado como o melhor modelo, alcançando um RMSE de 0.273 na validação cruzada. No entanto, este resultado apresenta desempenho abaixo do esperado para a tarefa de previsão de notas do IMDB.
 
![Imagem](img/melhor_algoritmo.png)

## 8.	Conclusão
O modelo de regressão para prever as notas apresentou resultados mistos. O Mean Absolute Error (MAE) de 0,22 ± 0,18 indica que, em média, as previsões do modelo divergem apenas 0,22 pontos da nota real, o que é considerado excelente em uma escala de 0 a 10. Da mesma forma, o Mean Absolute Percentage Error (MAPE) de 2,73% ± 0,02% confirma a alta precisão, com erro percentual médio abaixo de 3%, valor geralmente classificado como muito bom em projetos de previsão. O Root Mean Square Error (RMSE) de 0,28 ± 0,20 também ajuda na qualidade das previsões, mostrando que erros grandes são raros e que a maioria das previsões está concentrada próxima aos valores reais. No entanto, o coeficiente de determinação R² de 0,04 revela uma limitação significativa: o modelo explica apenas 4% da variabilidade total das notas do IMDB. Isso sugere que, embora as previsões sejam pontualmente precisas, o modelo não captura adequadamente os fatores subjacentes que influenciam as variações nas avaliações.
Essa disparidade entre erros absolutos baixos e R² reduzido pode indicar que o modelo é capaz de fazer previsões consistentes para certos padrões, mas falha em generalizar para toda a complexidade dos dados. Possíveis causas incluem a necessidade de variáveis mais informativas, também seria importante investigar possíveis problemas como underfitting ou vazamento de dados durante o treinamento.

## 9.	Próximos passos
•	Utilizar outras técnicas para tratamento de grandes dados;

•	Testar outros algoritmos de machine learning;

•	Implementar mais variáveis para definir melhor o comportamento dos consumidores;

•	Fazer o deploy deste projeto em ambiente cloud.

