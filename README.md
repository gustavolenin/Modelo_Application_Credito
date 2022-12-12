# Home Credit Risk Default

![image](https://user-images.githubusercontent.com/69591172/203203610-148f0702-134f-4ff4-a657-9f28b8d24198.png)

Este projeto consiste na resolução da competição [Home Credit Default Risk](https://www.kaggle.com/competitions/home-credit-default-risk) disponível no Kaggle.

### Instruções do Desafio:

Muitas pessoas lutam para obter empréstimos devido a históricos de crédito insuficientes ou inexistentes. E, infelizmente, essa população é frequentemente aproveitada por credores não confiáveis.

O Crédito Habitação busca ampliar a inclusão financeira para a população desbancarizada, proporcionando uma experiência de empréstimo positiva e segura. Para garantir que essa população carente tenha uma experiência de empréstimo positiva, o Home Credit utiliza uma variedade de dados alternativos - incluindo informações de telecomunicações e transações - para prever a capacidade de pagamento de seus clientes.

Embora o Home Credit esteja atualmente usando vários métodos estatísticos e de aprendizado de máquina para fazer essas previsões, eles estão desafiando os Kagglers a ajudá-los a desbloquear todo o potencial de seus dados. Isso garantirá que os clientes capazes de pagar não sejam rejeitados e que os empréstimos sejam concedidos com um principal, vencimento e calendário de pagamento que capacitará seus clientes a serem bem-sucedidos.

## Metodologia de Projeto: CRISP-DM 
![image](https://user-images.githubusercontent.com/69591172/203208546-41e1b3bf-9883-4e86-b1d0-26aaed2fd3e5.png)

### Etapas: 

##### 1- Business Understanding

A Home Credit é uma instituição financeira fundada em 1997 na República Tcheca, atualmente sediada na Holanda e operando em 9 países.
Empresas que trabalham com modelagem de risco de crédito devem possuir modelos com alto desempenho pois é de extrema importância a correta predição dos bons e maus pagantes. Isso pois visando o máximo lucro deve-se diminuir ao máximo a quantidade de inadimplência. Além disso, deve-se buscar uma solução eficiente com o objetivo de tornar a utilização do modelo viável ou seja que não tenha um custo computacional demasiado.

**Objetivo**: Identificar corretamente a capacidade de pagamento dos clientes.

**Critérios de Sucesso do projeto**: 
* Maximizar a identificação de clientes bons pagantes e também dos clientes maus pagantes.
* Maximizar a ROC AUC (métrica escolhida para avaliar o modelo de machine learning).

##### 2- Data Understanding

Arquivos application_{train|test}.csv consistem nas tabelas principais de treino e teste.

Arquivo bureau.csv consiste nos dados referentes a empréstimos anteriores. Todos os créditos anteriores do cliente fornecidos por outras instituições financeiras que foram relatados ao Credit Bureau (para clientes que possuem empréstimo em nossa amostra). Para cada empréstimo em nossa amostra, existem tantas linhas quanto o número de créditos que o cliente tinha no Credit Bureau antes da data de coleta do dado.

O arquivo bureau_balance.csv consiste nos saldos mensais dos créditos anteriores no Bureau de Crédito.
Esta tabela tem uma linha para cada mês de histórico de cada crédito anterior relatado ao Credit Bureau, ou seja, a tabela tem empréstimos de créditos anteriores relativos a meses onde temos algum histórico observável para os créditos anteriores.

O arquivo POS_CASH_balance.csv consiste em instantâneos de saldos mensais de POS anteriores (ponto de venda) e empréstimos que o requerente tinha com Crédito Habitação. Esta tabela tem uma linha para cada mês de histórico de cada crédito anterior no Crédito à Habitação (crédito ao consumo e empréstimos em dinheiro vivo) relacionados com empréstimos na nossa amostra, ou seja, a tabela tem empréstimos de créditos anteriores relativos a meses em que temos algumas linhas históricas observáveis para os créditos anteriores.

O arquivo credit_card_balance.csv consiste em instantâneos mensais do saldo dos cartões de crédito anteriores que o requerente possui com Crédito Habitação.
Esta tabela tem uma linha para cada mês de histórico de todos os créditos anteriores no Crédito à Habitação (crédito ao consumidor e empréstimos em dinheiro) relacionados com empréstimos na nossa amostra, ou seja, a tabela tem empréstimos de cartões de crédito anteriores relativos a meses em que temos algum histórico observável para as linhas de cartão de crédito anteriores.

O arquivo previous_application.csv consiste em todos os pedidos anteriores de crédito à habitação de clientes que têm crédito na nossa amostra.
Há uma linha para cada inscrição anterior relacionada a empréstimos em nossa amostra de dados.

O arquivo installment_payments.csv consiste histórico de amortização dos créditos anteriormente desembolsados no Crédito Habitação relativos aos empréstimos da nossa amostra. Há a) uma linha para cada pagamento feito mais b) uma linha para cada pagamento perdido.
Uma linha equivale a um pagamento de uma prestação ou uma prestação correspondente a um pagamento de um crédito de Crédito Habitação anterior relativo a empréstimos na nossa amostra.

O arquivo HomeCredit_columns_description.csv consiste nas descrições para as colunas nos vários arquivos de dados.

![image](https://user-images.githubusercontent.com/69591172/203211719-747b356e-f9cd-4c3f-938b-ef320ba7150c.png)

[Clique aqui](https://github.com/gustavolenin/Home_Credit_Default_Risk/blob/main/notebook/understanding_data.ipynb) para visualizar o arquivo onde realiza-se o entendimento dos dados.

##### 3- Data Preparation

Nesta etapa, foram realizadas algumas agregações nos DataFrames: bureau, bureau_balance, POS_CASH_balance, credit_card_balance, previous_application e installments_payments, em seguida houve o merge para concatenar os dados em um único DataFrame. 

Além disso, fez-se necessário tratamento de valores ausentes, bem como optou-se pela criação de novas features.

Deve-se destacar que a etapa de imputação de dados ocorreu após o split do conjunto de dados em treino e teste com o objetivo de evitar data leakage.

##### 4- Modeling

Nesta seção, foi realizado um processo de seleção de variáveis utilizando o Random Forest reduzindo em aproximadamente 8% o número de variáveis cujo impacto na variável alvo, segundo o método aplicado, era desprezível. Dessa forma, há redução do custo computacional durante o processo de treinamento do modelo. Além disso, deve-se mencionar também que tendo conhecimento disso se torna possível o monitoramento das variáveis que possuem maior grau de importância, bem como otimizar o processo de extração de dados.

Após a seleção de variáveis, foram testados 5 algoritmos de machine learning (Logistic Regression, Random Forest, XGBoost, LightGBM e Catboost) com o objetivo de verificar qual possuia o melhor desempenho de acordo com a métrica técnica escolhida. No processo de escolha, além de considerar os critérios técnicos, foi considerada também o grau de explicabilidade do modelo.

Em seguida, houve um processo de tunagem visando maximizar o desempenho tendo como parâmetro a métrica técnica escolhida (ROC-AUC).

##### 5- Evaluation

Embora o Catboost tenha desempenhado melhor de acordo com o parâmetro ROC-AUC, o pequeno ganho no parâmetro ROC-AUC não justifica a utilização desse modelo. Isso ocorre devido ao baixo grau de explicabilidade quando comparado à regressão logística, fato que dificulta bastante a aplicação do Catboost para a modelagem de risco de crédito. Dessa forma, a Regressão Logística foi o algoritmo escolhido.

##### 6- Deployment

Nesta seção, realizou-se a exportação do modelo via Pickle gerando um arquivo deve ser colocado em produção visando gerar valor ao negócio.

-------------------------------------------------------------------------------------------------

Para visualizar melhor o notebook [clique aqui](https://nbviewer.org/github/gustavolenin/Home_Credit_Default_Risk/blob/main/notebook/home_credit_default_risk.ipynb)
