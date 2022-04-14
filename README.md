<html>
<h3> Apresentação do projeto:
<h5>
O projeto se trata de uma hipotética situação, onde a empresa (de E-commerce) Olist gostaria de melhorar seus negócios por meio de Data Science. Em primeiro lugar, essa empresa define qual problema está tentando resolver. No caso, ela identificou que é cinco vezes mais caro adquirir novos vendedores do que reter os atuais. Logo, o problema é aumentar a taxa de retenção de vendedores para diminuir custos. Uma possível solução de Data Science é construir um modelo de Machine Learning para prever o churn (a rotatividade). Depois, esse modelo é avaliado por meio de métricas de negócios e testes estatísticos e, por fim, é implementado.

No arquivo entitulado `analise_exploratoria_churn_sellers_olist` encontra-se uma análise exploratória de nível iniciante com o propósito de encontrar insights nos dados disponibilizados, responder algumas dúvidas de negócio com base na exploração (utilizando Python e SQL) e preparar uma base de dados contendo as principais características para a próxima etapa do projeto: *Feature Engineering*. No mesmo aquivo está também disponibilizado o relatório da análise e um dashboard com as informações mais importantes encontrads.
  
  
  
  <html>

A base de dados possui um total de 91.342 vendas distintas, trazendo um total de R$ 14.891.744,80 ao longo de 22 meses (Out2016 até Ago2018) e apresenta  3.025 vendedores e 88.572 clientes/compradores

Característica | Qtd Total
---------------|----------
Vendas         | 91.342
Vendedores     | 3.025
Clientes       | 88.572

No entanto, os dois primeiros meses Out2016 e Dez2016 possuem pouquíssimas vendas na base e justamente por esse motivo, algumas análises foram feitas a partir de 2017.

Meses de 2016| Qtd de Vendas
-------------|--------------
Outubro      | 283
Dezembro     | 1


Quanto aos dados duplicados, forão encontradas e removidas 10.492 observações. E sobre os dados ausentes, apenas as colunas review_comment_title e review_comment_message apresentam porcentagens significantes com 88.43% e 58.93% respectivamente.

Ranking | Variável                   | % Faltante 
--------|----------------------------|-------------
1       | Título da avaliação        | 88.43
2       | Comentário da avaliação    | 58.93
3       | Data de entrega do produto | 2.13

<br>

Dentre os pedidos, a classe *delivered* (entregue) é a classe majoritária com 98% das vendas, seguida de shipped (enviado) com 1%. As formas de pagamento mais frequêntes são Cartão de Crédito (75%) e Boleto (19%). Quando olhamos para os parcelamentos, vimos que as vendas não parceladas correspondem a metade (50%) de todas as vendas, e que, as vendas com até 4 parcelas representam um total de 79%. No entanto, quando observamos a mediana dos valores das vendas distintas (R$ 102.86), fica fácil entender os números acima.

<br>

Quanto aos produtos, mais especificamente suas categorias, Cama_Mesa_Banho é a mais vendida apresentando 9.38% de todas as vendas (porém conta com uma nota média relativamente baixa nas avaliações). As outras 72 categorias dividem os 90,62%.
A base conta com 31.233 produtos distintos.
No entanto, se analisarmos as categorias visando lucratividade, Beleza_Saude é a categoria com a maior soma (R$ 1.532.127,56)	e uma média alta de 4.24 nas avaliações (5 é o máximo).

Ranking | Categoria              | % de Vendas  | Média Aval
--------|------------------------|--------------|-----------
1       | cama_mesa_banho        | 9.38         |3.92
2       | beleza_saude           | 9.04         |4.19
3       | esporte_lazer          | 7.69         |4.19
4       | informatica_acessorios | 6.59         |4.05
5       | relogios_presentes     | 5.93         |4.06

<br>

Os Estados que não possuem vendedores cadastrados são: Alagoas, Amapá, Tocantins, Roraima. No entanto, quando olhamos para os clientes (compradores) vimos que todos os 26 Estados mais o DF estão contidos nos dados.

Ainda sobre os dados regionais, as 5 cidades (de um total de 599) com mais vendas na base (Top Ranking) são: 

Ranking | Cidade            | Soma das Vendas (R$) 
--------|-------------------|---------------------
1       | São Paulo         | 2.935.165,17
2       | Ibitinga          | 809.908,51
3       | Curitiba          | 519.757,39
4       | Rio de Janeiro    | 376.027,63
5       | Guarulhos         | 347.864,46


Há também um crescimento constante com o evoluir dos meses, apresentando um pico nas vendas no mês de Novembro, provavelmente atribuído ao evento da Black Friday (O mês apresenta também a maior proporção de reclamações, 37%).

<br>

Se tratando da adesão de novos vendedores e clientes, fica observado uma oscilação quando olhamos para a quantidade de novos vendedores a cada mês, e um constante aumento em novos clientes que passaram a utilizam a plataforma da empresa.

Quando analisado apenas as vendas distintas e entregues de 2017, algumas informações saltam na tela como: Janeiro trás a maior *média por pedido*, Outubro por sua vez apresenta a *maior mediana*, Novembro ficando tanto com a *maior soma dos pedidos* quanto com a *maior quantidade de itens vendidos*.
Inclusive fica observado que a maior parte das vendas ocorre entre as 10:00 e as 22:00 horas.

Mês      | Estatísticas Top 1       | Valor da estatística
---------|--------------------------|---------------------
Janeiro  | Média por pedido         | 172,73
Outubro  | Mediana dos pedidos      | 104,03
Novembro | Soma das vendas          | 1.062.700,18
Novembro | Soma de Itens Vendidos   | 6.561

<br>

Uma relação de duas variáveis encontrada nos dados tem haver com a *soma total de vendas de cada Estado* e o seu *valor médio de frete*. Com auxílio do gráfico observamos uma possível correlação negativa de nível moderado entre as duas características (com correlação de Pearson de -0.58)

<br>

O ticket médio (quantidade média de produtos por pedido) não parece apresentar uma tendência de crescendo ao longo do tempo em nenhuma das 5 regiões do país.
Por falar nas regiões, o Norte apresenta a maior porcentagem de frete em relação ao custo total do pedido, representando cerca de 15% de toda a compra (apresenta também a menor soma de vendas, e essa relação negativa se mantém conforme explicado acima).

<br>

A distribuição das notas de avaiação dos pedidos mostra a nota máxima de 5 em aproximadamente 60% dos pedidos. A pior avaliação (1) fica com 9,74%.
Neste quesito os Boletos são a forma de pagamento com maiores reclamações.

Avaliações | % de Avaliações
-----------|----------------
Ótima      | 59.20
Boa        | 19.60
Normal     | 8.30
Ruim       | 3.14
Péssima    | 9.74

<br>

Submetidos os dados a um modelo de Random Forest usando o método de permutação vimos que as características físicas dos produtos possuem alta relevância entre àqueles produtos Top Ranking de vendas, enquanto as variáveis financeiras (como preço ou frete) possuem pouca importância. É possível observar também que feactures informativas como a *descrição* e o *nome do produto* são mais importantes neste caso do que a quantidade de fotos ou o preço.

<br>

Por fim, quando analisado a precisão (acurácia) na data prevista de entrega disponibilizada no ato da compra, vimos mesmo com uma margem de 7 dias (caso o site erre em 7 dias para mais ou para menos, ainda assim é contado como acerto)
o sistema de predição erra em aproximadamente 70% dos pedidos.

</html>
</html>
