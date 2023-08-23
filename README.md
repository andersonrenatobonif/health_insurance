# 1- Problema de Negócio

O cliente é uma seguradora que atua apenas comseguro de vida e que pretende lançar uma nova modalidade de serviço para seguro de automóveis. O novo serviço será vendido primeiramente aos atuais clientes utilizando a estratégia de cross sell e por isso o cliente solicitou a criação de um modelo preditivo para ordenar a lista de clientes de acordo com a maior propensão de compra. 

O cliente fez uma pesquisa para os clientes atuais perguntando quem teria interesse em adquirir o novo serviço e forneceu um arquivo csv com algumas características de cada cliente e a label com a resposta sobre o interesse, 1 para quem tem interesse e 0 para quem não tem interesse.

As informações compartilhadas pelo cliente nesse arquivo são as seguintes:

- id: Identificador único para cada cliente
- Gender: Gênero do cliente
- Age: Idade do cliente
- Driving_License: 0 se não tem habilitação e 1 se tem habilitação
- Region_Code: Identificador único da região do cliente
- Previously_Insured: 1 se o cliente já possui seguro veicular e 0 se não possui
- Vehicle_Age: Idade do veículo
- Vehicle_Damage: 1 se o cliente já sofreu acidente veicular no passado e 0 se nunca sofreu acidente veicular no passado.
- Annual_Premium: O valor que o cliente precisa pagar como prêmio no ano
- Policy_Sales_Channel: Código anonimizdo do canal de vendas. Agentes diferentes, por correio, por telefone, pessoalmente, etc.
- Vintage: Número de dias que essa pessoa é cliente 
- Response: 1 se o cliente está interessado e 0 se não está interessado





# 2- Estratégia da Solução

- Não é um problema de classificação convencional, mas sim de Learn to Rank, logo, as métricas tradicionais de classificação não se aplicam. O objetivo aqui é ordenar a lista da maneira que maximize a conversão com mínimo de contatos possível.

- A estratégia que segui para realizar esse projeto foi analisar os dados e treinar os modelos de classificação e a partir da probabilidade pe pertencer a determinada classe trazida pelos modelos, criei uma coluna com score de cada e ordenei em ordem decrescente.

Para executar esse projeto utilizei os seguintes passos:

- Passo 1 - Descrição dos Dados: Renomeação de colunas, mudanças de tipos, preenchimento/exlusão de dados faltantes, visão inicial das variáveis numéricas e categóricas.

- Passo 2 - Feature Engineering: Criação das hipóteses a serem validadas na EDA, criação de novas features necessárias na EDA.

- Passo 3 - Filtragem dos Dados: Filtragem das linhas e colunas de acordo com o entendimento do negócio.

- Passo 4  - Análise Exploratória de Dados: Análise de variável resposta, análise únivariada das variáveis numéricas e categóricas, análise bivariada através das hipóteses criadas no passo anterior, correlação de pearson, método V de Cramer.

- Passo 5 - Preparação dos Dados: Aplicãção das transformações e dummização das variáveis.

- Passo 6 - Seleção das Features: Foi aplicado o algoritmo Boruta para selecionar as variáveis que mais explicam a variável resposta.

- Passo 7 - Modelos de Machine Learning: Treinamento, teste e avaliação de 5 modelos de machine learning.

- Passo 8 - Fine Tunning: Busca por hiperparâmetros que possam melhorar o modelos selecionado no passo anterior

- Passo 9 - Business Performance: Tradução dos resultados do modelo para aplicação no negócio, a previsão realizada e quão confiável a mesma será para o diretor realizar as tomadas de decisão.

- Passo 10 - Deploy do modelo em produção: Colocar o modelo na Cloud e criar a conexão do modelo como bot no telegram através da API.



# 3- Top 3 Insights de Dados

- Pessoas sem habilitação tem maior propensão de compra.

- Pessoas que já sofreram acidentes veiculares tem maior propensão a compra.

- Pessoas tem mais propensão a comprar quando o prêmio anual é de até 40.000.

	- Usar essas informações para direcionar campanhas de marketing e atendimento direcionado.



# 4- O produto final do projeto

Os funcionários do cliente usam o google planilha para realizar o acompanhamento e a tratativa dos clientes, então o projeto foi pensado para integrar o modelo a planilha para predição e ordenação dos clientes na mesma.

Foi adicionado um botão onde o funcionário pode gerar o score e ordenação dos clientes que adiciona a planilha.

A planilha pode ser acessado através desse link <a href="https://docs.google.com/spreadsheets/d/1y2yzBCq8rhPkdMPjnO-RbAwoIwsDB0yMYAWmvkysvqo/edit?usp=sharing" target="_blank"    class="icon solid fa-chart-line"><span class="label">Google sheets do modelo em produção</span></a>



# 5- Conclusão

O objetivo desse projeto foi alcançado, os funcionários tem acesso a um modelo de gera um ordenãção pelo menos 2,5x (duas vezes e meia) melhor que uma ordenação aleatória e percorrendo 60% da lista terá atingido 100% dos clientes interessados.

Aplicando esse modelo ele poderá tomar decisões com uma variação máxima de menos de 1% quando observamos a soma de receita de todas as lojas. 




# 7- Próximos passos

- Coletar mais dados e melhorar o modelo para ordenar melhor e alcançar os clientes interessados mais rapidamente.
