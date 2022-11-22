# Credit_Risk_Prediction

![image](https://user-images.githubusercontent.com/69591172/203203610-148f0702-134f-4ff4-a657-9f28b8d24198.png)

Este projeto consiste na resolução da competição Home Credit Default Risk disponível no Kaggle.

### Instruções do Desafio:

Muitas pessoas lutam para obter empréstimos devido a históricos de crédito insuficientes ou inexistentes. E, infelizmente, essa população é frequentemente aproveitada por credores não confiáveis.

O Crédito Habitação busca ampliar a inclusão financeira para a população desbancarizada, proporcionando uma experiência de empréstimo positiva e segura. Para garantir que essa população carente tenha uma experiência de empréstimo positiva, o Home Credit utiliza uma variedade de dados alternativos - incluindo informações de telecomunicações e transações - para prever a capacidade de pagamento de seus clientes.

Embora o Home Credit esteja atualmente usando vários métodos estatísticos e de aprendizado de máquina para fazer essas previsões, eles estão desafiando os Kagglers a ajudá-los a desbloquear todo o potencial de seus dados. Isso garantirá que os clientes capazes de pagar não sejam rejeitados e que os empréstimos sejam concedidos com um principal, vencimento e calendário de pagamento que capacitará seus clientes a serem bem-sucedidos.

## Metodologia de Projeto: CRISP-DM 
![image](https://user-images.githubusercontent.com/69591172/203208546-41e1b3bf-9883-4e86-b1d0-26aaed2fd3e5.png)

### Etapas: 

##### 1- Business Understanding

##### 2- Data Understanding

Arquivos application_{train|test}.csv consistem nas tabelas principais de treino e teste.

Arquivo bureau.csv consiste nos dados referentes a empréstimos anteriores. Todos os créditos anteriores do cliente fornecidos por outras instituições financeiras que foram relatados ao Credit Bureau (para clientes que possuem empréstimo em nossa amostra). Para cada empréstimo em nossa amostra, existem tantas linhas quanto o número de créditos que o cliente tinha no Credit Bureau antes da data do pedido.

O arquivo bureau_balance.csv consiste nos saldos mensais dos créditos anteriores no Bureau de Crédito.
Esta tabela tem uma linha para cada mês de histórico de cada crédito anterior relatado ao Credit Bureau - ou seja, a tabela tem (#empréstimos na amostra * # de créditos anteriores relativos * # de meses onde temos algum histórico observável para os créditos anteriores) linhas.

O arquivo POS_CASH_balance.csv consiste instantâneos de saldos mensais de POS anteriores (ponto de venda) e empréstimos em numerário que o requerente tinha com Crédito Habitação. Esta tabela tem uma linha para cada mês de histórico de cada crédito anterior no Crédito à Habitação (crédito ao consumo e empréstimos em numerário) relacionados com empréstimos na nossa amostra – ou seja, a tabela tem (#empréstimos na amostra * # de créditos anteriores relativos * # de meses em que temos algumas linhas históricas observáveis para os créditos anteriores).

O arquivo credit_card_balance.csv consiste instantâneos mensais do saldo dos cartões de crédito anteriores que o requerente possui com Crédito Habitação.
Esta tabela tem uma linha para cada mês de histórico de todos os créditos anteriores no Crédito à Habitação (crédito ao consumidor e empréstimos em dinheiro) relacionados com empréstimos na nossa amostra – ou seja, a tabela tem (#empréstimos na amostra * # de cartões de crédito anteriores relativos * # de meses em que temos algum histórico observável para as linhas de cartão de crédito anteriores).

O arquivo anterior_aplicativo.csv consiste todos os pedidos anteriores de crédito à habitação de clientes que têm crédito na nossa amostra.
Há uma linha para cada inscrição anterior relacionada a empréstimos em nossa amostra de dados.

O arquivo parcelas_pagamentos.csv consiste histórico de amortização dos créditos anteriormente desembolsados no Crédito Habitação relativos aos empréstimos da nossa amostra. Há a) uma linha para cada pagamento feito mais b) uma linha para cada pagamento perdido.
Uma linha equivale a um pagamento de uma prestação OU uma prestação correspondente a um pagamento de um crédito de Crédito Habitação anterior relativo a empréstimos na nossa amostra.

O arquivo HomeCredit_columns_description.csv consiste nas descrições para as colunas nos vários arquivos de dados.

##### 3- Data Preparation

##### 4- Modeling

##### 5- Evaluation

##### 6- Deployment
