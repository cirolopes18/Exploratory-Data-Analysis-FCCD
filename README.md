# O Projeto
Projeto de Análise Exploratória de Dados resultado do 1º Hackathon da Formação Completa em Ciência de Dados do Anwar Hermuche. O objetivo foi promover o desenvolvimento dos alunos em relação aos aspectos fundamentais de uma EDA. O dataset utilizado foi de um conjunto de imóveis e algumas de suas características, como valor do aluguel, condomínio, se aceita pets etc. Tínhamos que, obrigatoriamente, responder 18 perguntas levantadas pelo Anwar. Ele pontuou quatro critérios de avaliação: (i) Qualidade e Profundidade da Análise de Dados, (ii) Criatividade, (iii) Apresentação e Visualização de Dados, (iv) Aplicabilidade e Relevância no Mundo Real. 

# O Dataset
Foram avaliados 10.692 imóveis e 13 features: cidade, área, cômodos, banheiros, vagas de garagem, andares, se aceita animais, se é mobiliado, valor do condomínio, valor do aluguel, valor do imposto sobre propriedade, valor do seguro contra incêndio, valor total mensal.

# Exploratory Data Analysis (FCCD)
Dentre as 18 perguntas levantadas pelo Anwar para estrurarmos uma análise completa, destaco as análises abaixo. Para uma avaliação completa, a leitura da análise do projeto é fundamental, uma vez que ele (e o respectivo storytelling) é estruturado para elucidar as principais conclusões a respeito do dataset.

1. Por que avaliar o valor do aluguel como uma das principais variáveis a serem explicadas?

Sabemos que a decisão de onde morar depende da análise do custo total com a moradia. Porém, o componente que mais pesa no valor total é o aluguel. Logo, faz mais sentido iniciar a análise por ele. Pela análise do histograma e pelas estatísticas descritivas, vemos que a variável de participação do valor do aluguel no valor total possui média de 0,76 e mediana de 0,76. Além disso, vemos que mais de 75% das observações possuem valor maior do que 67,47% (1º quartil). Ou seja, para a maior parte dos imóveis, o aluguel é o fator de maior peso no custo total.

<p align="center">
  <img src="https://github.com/cirolopes18/Exploratory-Data-Analysis-FCCD/assets/148280600/cd2b48dc-dce4-4145-a6b6-dd04ec9c3fb2">
</p>

2. O valor do aluguel é diferente entre as cidades da amostra (São Paulo, Rio de Janeiro, Belo Horizonte, Porto Alegre e Campinas)?

Em um primeiro momento, vamos analisar comparativamente as cidades em um mesmo gráfico. Por premsisa, estamos ordenando as caixas de acordo com a ordem crescente das medianas dos valores de aluguel por cidade. 

Desta forma, as cidades já aparecem ordenadas no eixo X, o que deixa claro duas questões: (i) São Paulo é a cidade que possui maior mediana no valor do aluguel (indícios de ser a cidade com aluguel mais caro do país na nossa amostra) e (ii) é a cidade que, na nossa amostra, possui os imóveis com maiores valores de aluguel. Ainda dentro da segunda questão, provavelmente são os outliers de São Paulo que tornam a visualização das informações pouco legível. Isto é, precisamos de mais alguma manipulação para gerar um insight mais legível e confiável.

<p align="center">
  <img src="https://github.com/cirolopes18/Exploratory-Data-Analysis-FCCD/assets/148280600/2808781a-1340-4a33-a60e-31d7a5d0cdd1">
</p>

As perguntas que surgem são: (i) a média do aluguel em São Paulo é, de fato, maior do que as demais cidades? (ii) A média das demais cidades, com base em sua distribuição, são estatisticamente diferentes? Devemos responder as por meio de um teste de hipóteses. Qual cenário temos? Assumindo que a amostra de cada cidade é independente das demais, temos que realizar testes de hipóteses para médias, onde desconhecemos os desvios-padrão populacionais. Fazemos isso para toda comparação de valores, o que pode ser visto em detalhes no projeto

3. O imóvel estar mobiliado influencia no valor do aluguel?

Vendo pelo boxplot, observamos que para imóveis não-mobiliados, a dispersão dos valores de aluguel é maior. Apesar de a mediana do aluguel para móveis mobiliados ser maior (3500,00 vs. 2400,00), assim como a média (4882,29 vs. 3578,58), um teste de hipótese para médias de duas amostras é uma avaliação indispensável a ser feita.

<p align="center">
  <img src="https://github.com/cirolopes18/Exploratory-Data-Analysis-FCCD/assets/148280600/e2940b3b-24f7-427f-a23e-1eb5a17d2081">
</p>

4. Existe correlação entre área e valor do aluguel?

No primeiro gráfico abaixo vemos o que os outliers de área fazem com o gráfico de dispersão fique pouco legível. No projeto, fizemos uma análise prévia para indicar, a priori, o fato de valores de área acima de 10000 serem potenciais outliers. Iremos, somente para fins de análise complementar, retirar esses pontos e ver o impacto sobre o gráfico de dispersão e sobre o índice de correlação de Pearson. Vale ressaltar que não é definitiva esta exclusão, pois, apesar de os valores serem discrepantes, ainda temos que confirmar que eles de fato se configuram como outliers.

<p align="center">
  <img src="https://github.com/cirolopes18/Exploratory-Data-Analysis-FCCD/assets/148280600/16f882dc-e4b9-43d0-992f-0da594b32145">
</p>

<p align="center">
  <img src="https://github.com/cirolopes18/Exploratory-Data-Analysis-FCCD/assets/148280600/be519c9f-910b-4dd7-a56b-997d4f6c72e6">
</p>

Primeiro, mesmo com a exclusão parcial dos valores discrepantes, vemos que existe uma concentração de pontos nos seguintes intervalos no plano cartesiano: Aluguel = (0,15000), Area = (0, 1000). Qualquer afirmação sobre uma correlação linear positiva seria insuficiente se fosse feita somente após avaliação do gráfico. 

Segundo, com a exclusão parcial, o índice de correlação salta de 0,18 (correlação fraca) para 0,66 (correlação forte). Se olharmos para os valores discrepantes de aluguel no projeto, temos valores abaixo de 10.000,00 para imóveis com área maior do que 10000 m² (são todos apartamentos em prédios de, no mínimo, 3 andares; que apartamento é esse??). 

Com ressalvas, há, portanto indícios de que, quanto maior a área do imóvel, maior o valor de aluguel a ser cobrado.

# Comentários Finais

A primeira pergunta é mais para direcionar a análise. Isto é, qual é a minha variável-alvo? Qual é aquela variável que busco correlacionar com as demais? As demais perguntas envolvem hipóteses mais difundidas sobre o valor do aluguel, principalmente quando o morador está procurando um novo imóvel: será que escolho um imóvel mobiliado? Será que o valor do aluguel na cidade que estou olhando é maior do que nas outras cidades (uma proxy para começar a avaliar custo de vida na cidade)? Será que na cidade em questão o tamanho do imóvel impacta muito no valor do aluguel, de forma a limitar a escolha a imóveis menores? Enfim, as outras análises presentes no projeto concedem um conjunto mais robusto de insights para entendimento do cenário e tomada de decisão. 

Este projeto que fiz foi o vencedor do Hackathon! Comentários são mais do que bem-vindos. Vocês podem me encontrar no Linkedin ou e-mail. 

Abraços.
