# Health Insurance Cross-Sell Prediction

<img src="https://github.com/wrferreira1003/-health-insurance-cross-sell.pa00404/tree/main/reports/figures/capa.jpg" width=70% height=40% title="Health-Insurance-Ranking" alt="project_cover_image"/>

Projeto de rankeamento de clientes interessados na aquisição de um seguro veicular.

## 1. Contextualização:

Os dados do projeto foram obtidos do kaggle, do desafio "Health Insurance Cross Sell Prediction".

O contexto do negoócio é fictício, porem todo o planejamento e desenvolvimento da solução é realizado seguindo todos os passos de um projeto real para o mercado de trabalho.


### 1.1 Problema de Negócio
A empresa Insurance All é uma CIA de seguros de saúde e esta interessado em aproveitar os clientes que ja tem para tentar vender um novo produto, que seria um seguro de veiculo, para isso a empresa realizou uma pesquisa onde ela obteve o retorno de 304 mil clientes sobre o interesse em adquirir  ou não o novo produto (Seguro veicular). 

Porém existem 76 mil clientes, entre novos clientes e antigos, que não responderam a pesquisa.

### 1.2 Objetivo
A partir dos 304 mil dados da pesquisa, onde temos os clientes que estão ou não interessados no seguro de automovel, iremos construir um ranking por ordem de interesse (propensão de compra) dos 76 mil potenciais clientes.

As Seguintes questões de negócio precisam ser respondidas ao gestor do Call Center:

- Quais são os principais insights sobre os atributos mais relevantes de clientes interessados em seguro veicular?
- Qual a porcentagem de clientes interessados em seguro veicular, o call center conseguirá contatar fazendo 20 mil ligações?
- Se a capacidade do call center aumentar para 40 mil ligações, qual a porcentagem de clientes interessados em adquirir um seguro o call center conseguirá contatar?
- Quantas ligações o call center precisa fazer para contatar 80% da base dos clientes interessados em adquirir o seguro?

## 2. Premissas de Negócio

O time de vendas já utliza o google sheets como ferramenta corporativa, por este motivo uma das soluções desse projeto será mostrar o ranking de propensão de compra na propria tabela de clientes ja utlizada pela equipe.

## 3. Planejamento da Solução

### 3.1 Produto Final
O que será entregue efetivamente:
- Uma funcionalidade dentro da ferramenta google sheets, que ordena os 76 mil clientes, ou qualquer novo cliente incluso na planilha por propensão de compra.

### 3.2 Ferramentas
Ferramentas que serão utilizada no processo:
- python;
- Jupyter Notebook;
- Git, GitHub e GitLab;
- Google Mindmaps;
- SweetViz;
- Heroku Cloud;
- Algoritmos de Regressão e Classificação;
- Pacotes de Machine Learning sklearn e xgboost;
- Técnicas de Seleção de Atributos;
- Flask e Python API's;
- Google Sheets Apps Script.

### 3.3 Processo da solução

#### 3.3.1 Estrategia da Solução
Com base no objetivo do projeto, trata-se portando de um problema de Learning to Rank (LTR)

Abaixo detalho a minha estrategia para este problema de negócio, utilizando sempre a metodologia CRISP-DS:

**Step 1. Data Description:**
- Coletar dados em um banco de dados AWS Cloud.
- Compreender os dados e os significados de cada atributo(Features) dos interessados.
- Se Necessario renomear as colunas, analisar dimensões e os tipos dos dados.
- Identificar e tratar Dados Nulos.
- Analisar os atributos utilizando a estatística descritiva.
- Separa 20% dos dados para teste (Aleatoriamente, mas estratificados pela varável resposta).

**Step 2. Feature Engineering:**
- Criação do mindmap de Hipóteses de negócio.
- Realizar a feature engeneering, com as criações das features necessárias para validações das hipóteses.

**Step 3. Data Filtering:**
- Filtrar registros e atributos de acordo com restrições de negócio.

**Step 4. Exploratory Data Analysis:**
- Realizar uma análise univariada com uso do Sweetviz, avaliando detalhes de cada atributo.
- Realizar a análise Bivariada, validando as hipóteses criada e gerando insights de neǵocio.
- Criar tabela de resultados das Hipóteses, com suas relevancias estimada, essas informações serão importantes na hora de decidir quais features passar para os modelos.

**Step 5. Data Preparation:**
- Padronizar atributos numéricos com distribuição normal.
- Reescalar atributos numéricos com distribuição não normal.
- Codificar atributos categóricos em atributos numérico.
- Aplicar as transformações citado acima nos dados de teste.

**Step 6. Feature Selection:**
- Separar os dados de treino e Validação
- Rodar algoritmos para obter as features mais relevantes.
- Analisar as features mais relevante dada pelo modelo com as features relevante escolhido na EDA (Exploratory Data Analysis)
- Selecionar os melhores atributos para iniciar os treinos e validação dos modelos de machine learning.

**Step 7. Machine Learning Modelling:**
- Algoritmos Selecionados: KNN Classifier, Logistic regression, ExtraTrees Classifier e XGBboost Classifier.
- Como metrica, vou plotar a curva de ganho cumulativo e lift, e calcular precision@K/Recall@K de cada modelo.
- Criar uma tabela de performance comparando os resultados de cada modelo.

**Step 8. Hyperparamater And Fine Tunning:**
- Realizar um ajuste fino de Hiperparâmetros em cada modelo, identificando o melhor conjunto de parâmetros para maximizar suas capacidades de aprendizados.
- Aplicar validação cruzada em cada modelo, reduzindo o vies de selação (teoria da amostragem), por utilizar várias amostras diferentes dos dados.
- Selecionar os 4 modelos com melhor conjunto de hiperparâmetros, e avaliar sua capacidade de aprendizagem.
- Plotar as curvas cumulativo e lift, comparando os 4 modelos.
- Calcular o precision@K e Recall@K dos 4 modelos, e selecionar o de melhor performance.
- Submeter esse modelo aos dados de teste, e plotar suas curvas de ganho cumilativo e lift.
- Comparar as metricas no treino e nos dados de teste, avaliando a capacidade de generalização do modelo (Aprendizado com os dados novos).

**Step 9. Convert Model Performance to Business Values:**
- Responder as questões de negócio do gestor ao Call center.
- Comparar os resultados da lista aleatória com a lista ordenada por propensão de compra do seguro automotivo.
- Traduzir a performance do modelo em resultados financeiros para a Insurance All.

**Step 10. Deploy Modelo to Production:**
- Criar as classes para publicação do projeto.
- Testa as classes localmente.
- Publica a API no Heroku Cloud.
- Criação do APP Script no Google Sheets para consultar o modelo em produção.
- Implementar o botão que consulta a propensão de compra dos clientes no Google Sheets e testar a solução
- Treinar a Equipe para que possa utilizar o modelo.

## 4. Principais Insights dos dados

Durante a análise exploratória de dados, foram gerados alguns insights para o time de negócio, através da validação das Hipóteses.

#### H1 - 50% dos clientes com mais de 40 anos aceitariam o seguro de carro.

<img src="https://github.com/wrferreira1003/health-insurance-cross-sell.pa004/blob/main/reports/figures/H1.png?raw=true" alt="h1_validacao" title="Interesse vs Idade" align="center" height="380" class="center"/>

Hipótese Falsa, apenas 17.19% dos clientes acima de 40 anos aceitariam fazer um seguro de veiculos

#### H2 - 20% dos Clientes que ja são assegurado aceitaria adquirir um novo seguro.

<img src="https://github.com/wrferreira1003/health-insurance-cross-sell.pa004/blob/main/reports/figures/h2.png?raw=true" alt="h2_validacao" title="Interesse Vs Clientes que ja tem seguro" align="center" height="380" class="center"/>

Hipótese Falsa, apenas %0.09 dos clientes que ja tem seguro aceitaria um novo seguro.

#### H3 - Acima de 20% dos Clientes com veiculo acima de 2 anos de idade teria interesse no seguro segundo a pesquisa.

<img src="https://github.com/wrferreira1003/health-insurance-cross-sell.pa004/blob/main/reports/figures/h3.png?raw=true" alt="h3_validacao" title="Interesse Vs Clientes cujo o veiculo tem mais de 2 anos" align="center" height="380" class="center"/>

Hipotese Verdadeira, 29.21% dos clientes que teria veiculo com idade acima de 2 anos, teria interesse em um novo seguro veicular.

## 5. Modelo de Machine Learning aplicado

Na curva de ganho abaixo, são exibidos os 4 modelos com as melhores configurações de hiperparâmetros. Também é exibido o modelo perfeito, que ordenaria todos os interessados em sequência no topo da lista. A linha preta seria o baseline, representando a lista aleatória desordenada.

Curva de Ganhos Acumulados: Ordena por probabilidade a variavel de interesse (Comprar o seguro de automovel), cruza o percentual da base de clientes com o percentual de clientes propensos a comprar.
Ex: 40% da base de clientes (x), ordenada pela probabilidade de compra (y), contem 80% de todos os interessados em seguro veicular.

<img src="https://github.com/wrferreira1003/health-insurance-cross-sell.pa004/blob/main/reports/figures/ml.png?raw=true" alt="Curva de Ganho Todos os modelos" title="Curva de Ganhos Acumulados - Comparação dos modelos" align="center" height="380" class="center"/>

Na curva Lift abaixo, os 4 modelos somando ao modelo perfeito e o baseline também são Exibidos.

Lift Curve: Representa a diferença entre a curva de ganho e a lista aleatória. Resumindo, informa quanto o modelo é melhor que a lista aleatória.
Ex: Abragendo 50% da lista ordenada, o modelo é 2,4 vezes melhore que a lista aleatória.

<img src="https://github.com/wrferreira1003/health-insurance-cross-sell.pa004/blob/main/reports/figures/lift.png?raw=true" alt="Curva Lift" title="Lift Curve - Comparação dos modelos" align="center" height="380" class="center"/>

O Melhor modelo portando foi o XGBoost Classifier, e por este motivo foi selecionado para deploy em produção.

## 6. Performance do modelo.
Com o uso dos dados de teste (Dados nunca vistos pelo modelo), é feita a simulação de performace do modelo em ambiente de produção

As curvas de ganho cumulativo e lift dos dados de teste são apresentados abaixo:

|Precision@|Xgboost classifier (train)|Xgboost classifier (test)
|----------------|:---------------:|:------------------:|
| 10% | 0.37 | 0.40 |
| 20% | 0.35 | 0.36 |
| 30% | 0.32 | 0.32 |
| 40% | 0.28 | 0.28 |

|Recall@|Xgboost classifier (train)|Xgboost classifier (test)
|----------------|:---------------:|:------------------:|
| 10% | 0.31 | 0.33 |
| 20% | 0.56 | 0.58 |
| 30% | 0.77 | 0.79 |
| 40% | 0.92 | 0.93 |

Como podemos observar nas tabelas acima que comparando-se o modelo de treino e validação com o modelo de teste, as métricas permaneceram muito parecidas.

Essas informações demonstra que o modelo tem uma otima capacidade de generalização, significando que é capaz de aprender com dados nunca vistos.

## 7. Resultados de Negócio.

Chegamos na etapa mais importante do projeto, onde pegamos todos esses codigos e metricas utilizada e transformamos em resultados financeiros.

Dos 76.220 clientes, 9340 estão interessados em seguros de veiculo, (12,25% do total)

Primeiramente, vamos assumir que o valor do seguro de automovel, será o Ticket medio para um seguro de saude anual da Insurance All. 
Valor medio: $31669.

As questões de negócios serão respondidas com base nas premissas acima.

### Qual a porcentagem de clientes interessados em seguro veicular, o call center conseguirá contatar fazendo 20 mil ligações?

<img src="https://github.com/wrferreira1003/health-insurance-cross-sell.pa004/blob/main/reports/figures/20k.png?raw=true" alt="20k calls" title="Resultado com 20 mil ligações" align="center" height="380" class="center"/>

Para lista aleatória:
- A equipe de vendas contata 26% dos interessados em seguro veicular: 2.451 clientes ( Ver ganho: Cruzamento da Linha preta x Verde)
==> Receita estimada: 2.451 * 31.669 = US$ 77,62 milhoes por ano.

Pela lista ordenada (Modelo):
- A equipe de vendas contata 71% dos interessados em seguro veicular: 6.631 clientes ( Ver ganho: Cruzamento da Linha azul x Verde)
==> Receita estimada: 6.631 * 31.669 = US$ 210,19 milhoes por ano.

Resultado: O modelo é 2,7 vezes melhor que a lista aleatória (ver Lift: Linha azul x verde).

Portando a receita estimada é 2,7 vezes maior que a lista aleatória: 132,57 milhões.

### Se a capacidade do call center aumentar para 40 mil ligações, qual a porcentagem de clientes interessados em adquirir um seguro veicular o call center conseguirá contatar?

<img src="https://github.com/wrferreira1003/health-insurance-cross-sell.pa004/blob/main/reports/figures/40k.png?raw=true" alt="40k calls" title="Resultado com 40 mil ligações" align="center" height="380" class="center"/>

Para lista aleatória:
- A equipe de vendas contata 52% dos interessados em seguro veicular: 4.902 clientes ( Ver ganho: Cruzamento da Linha preta x Verde)
==> Receita estimada: 4902 * 31.669 = US$ 155,24 milhoes por ano.

Pela lista ordenada (Modelo):
- A equipe de vendas contata 99,5% dos interessados em seguro veicular: 9.294 clientes ( Ver ganho: Cruzamento da Linha azul x Verde)
==> Receita estimada: 9.294 * 31.669 = US$ 294,24 milhoes por ano.

Resultado: O modelo é 1,9 vezes melhor que a lista aleatória (ver Lift: Linha azul x verde).

Portando a receita estimada é 1,9 vezes maior que a lista aleatória: 139,00 milhões.

### Quantas ligações o call center precisa fazer para contatar 80% dos clientes interessados em adquirir um seguro veicular?

<img src="https://github.com/wrferreira1003/health-insurance-cross-sell.pa004/blob/main/reports/figures/80k.png?raw=true" alt="80% dos interessados" title="Resultados com 80% dos interessados" align="center" height="380" class="center"/>

Para lista aleatória:
- A equipe de vendas precisa fazer 60.976 ligações para atingir 80% dos clientes da lista, então atingirá 80% dos interessados em seguro veicular.

Pela lista ordenada (Modelo):
- A equipe de vendas precisa fazer 23.800 ligações, para entrar em contato com 31% dos clientes da lista, então atingirá 80% dos interessados em seguro veicular ( Ver ganho: Cruzamento da Linha azul x Verde).

### Planilha Funcional em google Sheets

<img src="/reports/figures/sheetsInsurance.gif" alt="cumulative gains curve and lift curve" title="Demonstração da solução" align="center" height="600" class="center"/>

Acesso a planilha: [Google Sheets - Health Insurance Ranking](https://docs.google.com/spreadsheets/d/1GDrjfPd5_KkQ0gzT9xHguRRWQLnlVc-gcvluawM1iNQ/edit?usp=sharing)

# 8. Conclusões do projeto

Com base nos resultados de negócio, conclui-se que o objetivo do projeto foi alcançado.

Com a solução de dados entregue, a Insurance All possui agora uma vantagem competitiva frente aos seus concorrentes, reduzindo o custo de aquisição de clientes, e aumentando o seu faturamento.

Pelo fato da solução implementada via planilha pode ser utilizada para novos clientes que ainda nem foram conquistados, é esperado um incremento ainda maior no faturamento esperado.

É possivel ainda aproveitar a solução para simular perfis de clientes, funcionalidade que é de grande valia para a empresa.

# 9. Melhorias Futuras

- Criar mais features a partir dos já existente, buscando gerar mais insumos para o aprendizado dos modelos. 
- Melhorar os metodos de seleção de Features, com a Utilização do Boruta ou RFECV por exemplo.

## 10 Referêrencias
* O Dataset foi obtido no [Kaggle](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction).
* A imagem utilizada é de uso livre e foi obtida no [Pexels](https://www.pexels.com).
