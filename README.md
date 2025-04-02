# Modelo para avaliação dos filmes do Netflix

👩‍💻 Autor: Kelly Ferreira

🛠️ Linguagem: Python

📈 Desenvolvido durante a [Trilha Data Science - ADA Tech Santander Coders](https://ada.tech/certificado?code=91beda22-296b-ad92-1553-3580486bc487)

Fonte do Dataset: [Kaggle](https://www.kaggle.com/datasets/heptapod/titanic)

## Objetivo do Modelo

Utilizar os parâmetros de **características morfológicas** das células a fim de identificar padrões associados ao câncer de mama

## 📚Bibliotecas utilizadas/ aplicabilidade

🔹 Pandas

O `pandas` foi usado para manipulação e análise dos dados, facilitando a leitura do arquivo e o pré-processamento das variáveis. 

🔹 MatplotLib

O `matplotlib.pyplot` foi usado para a apresentação gráfica e visualização das informações.

## 🧮Desenvolvimento das análises

🔹 Carregamento do dataset e remoção da primeira coluna:

`df = pd.read_csv('netflix.csv')
df = df.drop(df.columns[0], axis=1)  
df.head()`

🔹Visualização das colunas/linhas da tabela:

`df.head()`

-----adicionar tabela aqui------

🔹Geração do **Gráfico 1** -  Ranking de Filmes

`eixo_x = df['Score'].value_counts().keys()
eixo_y = df['Score'].value_counts().values
plt.bar(eixo_x, eixo_y)
plt.title('Ranking de Filmes')
plt.xticks(rotation=45)
plt.xlabel('Nota do Ranking')
plt.ylabel('Número de filmes')
plt.show()`

Onde:

`df['Score'].value_counts().keys()`: para visualizar os valores únicos das notas dos filmes   

`df['Score'].value_counts().values` para contagem dos filmes que possuem cada nota
        
 `plt.bar()` para criação do gráfico de barras
       
🔹Personalização do gráfico
    
`plt.title('Ranking de Filmes')`para adicionar título ao gráfico
        
 (`plt.xticks(rotation=45)`) para realizar a rotação dos rótulos em 45 graus do eixo X e facilitar a leitura
        
`plt.xlabel('Nota do Ranking')
plt.ylabel('Número de filmes')` para adicionar títulos aos eixos.
        
🔹Exibição do gráfico
    
`plt.show()`: 

----ADICIONAR O GRÁFICO AQUI---

🔹Geração do **Gráfico  2** - Filmes Produzidos por Ano

`plt.scatter(eixo_x, eixo_y)
plt.title('Filmes produzidos por ano')
plt.xticks(rotation=45)
plt.xlabel('Ano do Filme')
plt.ylabel('Número de filmes')
plt.show()`

----inserir gráfico aqui---

🔹Geração do **Gráfico  3** - Filmes Produzidos por Ano (Gráfico de Dispersão)

 (`plt.scatter()`) criação de  um gráfico de dispersão com os mesmos dados do gráfico de linha anterior.
 
 📝 Diferente do gráfico de linha, que conecta os pontos, o gráfico de dispersão **apresenta cada ponto individualmente**.

----inserir gráfico aqui---

🔹Geração do **Gráfico  4** - Quantidade de filmes por diretor

`df['Director'].value_counts().head(10).plot(kind='barh')
plt.title('Quantidade de Filmes por Diretor')
plt.xlabel('Número de Filmes')
plt.ylabel('Diretor')
plt.show()`

----inserir gráfico aqui---

🔹Geração do **Gráfico  5** - Ranking de Notas por diretor

`top_directors = df.groupby('Director')['Score'].mean().sort_values(ascending=False).head(10)
top_directors.plot(kind='barh')
plt.title('Ranking de Notas por Diretor')
plt.xlabel('Média da Nota')
plt.ylabel('Diretor')
plt.show()`

🔹Geração do **Gráfico  6** - Notas ao Longo dos Anos

`df.groupby('Year')['Score'].mean().plot(kind='line', marker='o')
plt.title('Notas ao Longo dos Anos')
plt.xlabel('Ano')
plt.ylabel('Nota Média')
plt.grid()
plt.show()`

🔹Geração do **Gráfico  7** - 10 Filmes Mais bem Avaliados

Para facilitar a visualização, foram concatenados os dados de filmes + diretor:

`import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv('netflix.csv')
df = df.drop(df.columns[0], axis=1)
top_filmes = df.sort_values(by='Score', ascending=False).head(10)
top_filmes['Filme_Diretor'] = top_filmes['Movie Title'] + '\n(' + top_filmes['Director'] + ')'
plt.figure(figsize=(10, 6))
plt.barh(top_filmes['Filme_Diretor'], top_filmes['Score'], color='royalblue')
plt.xlabel('Nota')
plt.ylabel('Filme (Diretor)')
plt.title('Top 10 Filmes Mais Bem Avaliados de Todos os Tempos')
plt.gca().invert_yaxis()  # Inverter para mostrar o melhor no topo
plt.show()`


##  📝Considerações Finais

🔹 No gráfico 1  é possível visualizar a distribuição das notas dos filmes e quantos filmes receberam determinada pontuação, sendo possível constatar que a maior parte encontra-se com nota entre 90 e 94;

🔹No gráfico 2 é possível visualizar que houve um salto no número de filmes produzidos no período entre 2010 e 2020;

🔹No gráfico 3, apesar de serem trabalhados os mesmos dados do gráfico 2,  é possível visualizar de forma mais detalhada as alterações de quantidade de filmes produzida ao longo dos anos.

🔹No gráfico 4, pode-se visualizar que Peter Jackson foi o diretor com o maior número de filmes e Remi Weekes, o diretor com o menor número de filmes;

🔹No gráfico 5, pode-se visualizar que Peter Jackson foi o diretor com o maior número de filmes e Remi Weekes, o diretor com o menor número de filmes;

🔹No gráfico 6, não se observa uma diferença considerável entre as notas dos diretores;

🔹No gráfico 7, é possível observar uma estabilidade na média de notas após os anos 2000, onde não se alcançam mais notas próximas às conquistadas na década de 1970;

🔹No gráfico 8, dentre os 10 filmes mais bem avaliados, também não é considerável a diferença entre eles.

💡 Com os dados apresentados, podemos observar uma tendência de baixa das notas em relação à década de 1970, necessitando de dados complementares para identificar as possíveis causas e que o número de filmes produzidos. Apesar de Remi Weekes ser o diretor com menos filmes lançados, foi o diretor mais bem avaliados dentre os demais e, em contrapartida, Peter Jackson não aparece no ranking dos 10 filmes mais bem avaliados.










