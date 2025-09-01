Portfólio de Dados: Análise da Imigração para o Canadá (1980-2013)
1. A Missão: Entendendo os Fluxos Migratórios
Olá! Este projeto é uma análise exploratória de dados sobre a imigração de diversos países para o Canadá entre os anos de 1980 e 2013. O objetivo é utilizar as bibliotecas de visualização de dados do Python (Matplotlib, Seaborn e Plotly) para transformar dados brutos em uma narrativa visual clara e informativa.

A análise busca responder a perguntas como:

Como evoluiu a imigração brasileira para o Canadá ao longo dessas três décadas?

Qual a posição do Brasil no ranking de imigração em comparação com seus vizinhos sul-americanos?

Quais são os principais países de origem dos imigrantes no Canadá nesse período?

Fonte dos Dados: O dataset utilizado é o "Canada.xlsx", contendo informações sobre a imigração anual por país de origem.

2. A Preparação: Limpeza e Organização dos Dados
Antes de qualquer visualização, os dados passaram por um processo de preparação para garantir a consistência e facilitar a análise. As principais etapas foram:

Carregamento dos Dados: Utilização da biblioteca Pandas para carregar o arquivo.

Definição do Índice: A coluna 'País' foi transformada no índice do DataFrame para facilitar a localização de dados.

Seleção de Período: Os dados anuais de 1980 a 2013 foram isolados para a análise de séries temporais.

Criação de Subconjuntos: Foram criados DataFrames específicos para o Brasil e para os países da América do Sul, permitindo análises focadas.

3. A Análise: Insights Visuais
Nesta seção, apresento as principais descobertas da análise, cada uma acompanhada por uma visualização de dados.

Insight 1: A Jornada Brasileira para o Canadá
Para entender a trajetória da imigração brasileira, foi criado um gráfico de linhas que mostra a evolução do número de imigrantes ano a ano.

Descoberta: O fluxo migratório do Brasil para o Canadá não é constante. Observamos picos e vales ao longo do período, com um crescimento mais acentuado a partir dos anos 2000, indicando um interesse crescente dos brasileiros pelo Canadá nas últimas décadas da análise.

<img width="717" height="436" alt="image" src="https://github.com/user-attachments/assets/0b5c3a61-01f9-44d3-8eab-138f687c36a8" />


![Gráfico da Imigração do Brasil para o Canadá]

Insight 2: O Brasil no Contexto Sul-Americano
Para contextualizar a imigração brasileira, foi criado um gráfico de barras comparando o volume total de imigrantes de todos os países da América do Sul.

Descoberta: O Brasil se posiciona como o quarto maior país emissor de imigrantes da América do Sul para o Canadá no período analisado. A Colômbia lidera com uma margem significativa, seguida por Peru e Argentina. Isso mostra que, embora relevante, a imigração brasileira não é a maior do continente.

<img width="1045" height="455" alt="image" src="https://github.com/user-attachments/assets/31621ed5-6ce1-4925-92d1-dccbbb756e80" />


![Gráfico Comparativo da América do Sul]

Insight 3: O Cenário Global
Para ter uma visão macro, foi gerado um gráfico com os 10 países que mais enviaram imigrantes para o Canadá.

Descoberta: A análise global revela que os principais fluxos migratórios para o Canadá vêm de países da Ásia, como Índia, China e Filipinas. Isso coloca a imigração sul-americana em perspectiva, mostrando que ela representa uma fatia menor do total de imigrantes recebidos pelo Canadá.

<img width="895" height="430" alt="image" src="https://github.com/user-attachments/assets/2ebf89d0-2a6a-451a-8f2f-1e410f2a50f2" />


![Gráfico do Top 10 Países]

4. As Conclusões: Próximos Passos
Esta análise exploratória revelou padrões importantes sobre a imigração para o Canadá. Vimos a evolução do fluxo brasileiro, o comparamos com seus vizinhos e o situamos no cenário global.

Próximos Passos Sugeridos:

Dashboard Interativo: Utilizar o conhecimento de Plotly para criar um dashboard completo onde o usuário possa selecionar diferentes países ou continentes e explorar os dados dinamicamente.

Análise Preditiva: Aplicar modelos de séries temporais (como ARIMA) para tentar prever as tendências futuras de imigração, com base nos dados históricos.

Análise Geoespacial: Criar um mapa coroplético para visualizar a intensidade da imigração por país de origem em um mapa-múndi.

Ferramentas Utilizadas:

Linguagem: Python



# **Análise da Imigração para o Canadá (1980-2013)**

# 1. Preparação do Ambiente e Carga dos Dados

# Importando a biblioteca pandas para manipulação e análise de dados.
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px

# Carregando o conjunto de dados de imigração para o Canadá.
df = pd.read_csv('/content/imigrantes_canada.csv')

# Para facilitar a busca e seleção de dados, o nome do país será definido como o índice do DataFrame.
df.set_index('País', inplace=True)

# Criando uma lista com os anos do período de análise para facilitar a filtragem das colunas.
anos = list(map(str, range(1980, 2014)))

# 2. Foco da Análise: A Imigração Brasileira

# O objetivo inicial é explorar a trajetória da imigração brasileira para o Canadá.
# Para isso, foi criada uma série temporal com os dados do Brasil.
brasil = df.loc['Brasil', anos]

# Convertendo a série para um DataFrame para facilitar a manipulação com as bibliotecas de visualização.
brasil_dict = {'ano': brasil.index.tolist(), 'imigrantes': brasil.values.tolist()}
dados_brasil = pd.DataFrame(brasil_dict)


# 3. Visualizando a Série Histórica com Matplotlib

#  3.1. Evolução da Imigração Brasileira (1980-2013)
# O primeiro passo é criar um gráfico de linhas para observar a tendência da imigração brasileira ao longo do tempo.
# Isso ajuda a identificar picos, quedas e padrões gerais.

plt.figure(figsize=(10, 6)) # Ajustando o tamanho para melhor legibilidade.
plt.plot(dados_brasil['ano'], dados_brasil['imigrantes'])

# Adicionando elementos para contextualizar o gráfico.
plt.title('Imigração do Brasil para o Canadá (1980-2013)')
plt.xlabel('Ano')
plt.ylabel('Número de Imigrantes')

# Para não poluir o eixo X, serão exibidos apenas os rótulos a cada 5 anos.
plt.xticks(['1980', '1985', '1990', '1995', '2000', '2005', '2010'])

plt.grid(linestyle='--', alpha=0.6) # Adicionando um grid suave para facilitar a leitura dos valores.
plt.show()


# ## 3.2. Comparativo: Brasil vs. Outros Países da América do Sul
# Como a imigração brasileira se compara à de seus vizinhos sul-americanos?
# A criação de subplots permite uma visualização comparativa eficiente.

# Selecionando os países para comparação.
paises_sul_americanos = ['Brasil', 'Colômbia', 'Argentina', 'Peru']

# Criando a figura e os eixos para os subplots.
fig, axs = plt.subplots(2, 2, figsize=(15, 10))
fig.suptitle('Comparativo da Imigração de Países da América do Sul para o Canadá (1980-2013)', fontsize=16)

# Ajustando o espaçamento para evitar sobreposição de títulos.
fig.subplots_adjust(hspace=0.4, wspace=0.3)

# Iterando para criar cada gráfico.
axs[0, 0].plot(df.loc['Brasil', anos])
axs[0, 0].set_title('Brasil')

axs[0, 1].plot(df.loc['Colômbia', anos])
axs[0, 1].set_title('Colômbia')

axs[1, 0].plot(df.loc['Argentina', anos])
axs[1, 0].set_title('Argentina')

axs[1, 1].plot(df.loc['Peru', anos])
axs[1, 1].set_title('Peru')

# Aplicando melhorias a todos os subplots para consistência visual.
for ax in axs.flat:
    ax.set_xlabel('Ano')
    ax.set_ylabel('Nº de Imigrantes')
    ax.xaxis.set_major_locator(plt.MultipleLocator(5)) # Marcador a cada 5 anos.
    ax.grid(True, linestyle='--', alpha=0.5)

# Definindo a mesma escala no eixo Y para uma comparação justa.
ymin, ymax = 0, 8000
for ax in axs.ravel():
    ax.set_ylim(ymin, ymax)

plt.show()

# ## 3.3. Destaque: Qual o volume total de imigração por país?
# Para responder a essa pergunta, um gráfico de barras é ideal.
# A análise focará nos países da América do Sul para entender a posição do Brasil na região.

# Filtrando o DataFrame original para a região 'América do Sul'
america_sul = df[df['Região'] == 'América do Sul']

# Ordenando os dados para criar um ranking claro.
america_sul_sorted = america_sul.sort_values(by='Total', ascending=True)

# Criando uma lista de cores para destacar o Brasil.
# Esta é uma técnica de storytelling visual: guiar o olhar do leitor para o ponto de interesse.
cores = ['green' if pais == 'Brasil' else 'silver' for pais in america_sul_sorted.index]

# Criando o gráfico de barras horizontais.
fig, ax = plt.subplots(figsize=(12, 8))
ax.barh(america_sul_sorted.index, america_sul_sorted['Total'], color=cores)

# Título informativo que já traz a principal conclusão.
ax.set_title('Brasil foi o 4º país da América do Sul com mais imigrantes para o Canadá (1980-2013)', loc='left', fontsize=16)
ax.set_xlabel('Número Total de Imigrantes')
ax.set_ylabel('') # O eixo Y já tem os nomes dos países.

# Adicionando os valores exatos em cada barra para maior precisão.
for i, v in enumerate(america_sul_sorted['Total']):
    ax.text(v + 100, i, str(v), color='black', ha='left', va='center')

# Limpando o visual do gráfico para focar na informação (decluttering).
ax.set_frame_on(False) # Remove a moldura.
ax.get_xaxis().set_visible(False) # Remove o eixo X, já que os valores estão nas barras.
ax.tick_params(axis='both', which='both', length=0) # Remove os traços dos ticks.

# Salvando o gráfico para uso no relatório ou apresentação.
fig.savefig('imigracao_america_sul_ranking.png', dpi=300, bbox_inches='tight')

plt.show()


# ## 4. Análise dos Maiores Fluxos Migratórios com Seaborn
# Seaborn permite criar gráficos esteticamente agradáveis com poucas linhas de código.
# Aqui, o objetivo é identificar os 10 países que mais enviaram imigrantes para o Canadá.

# Preparando os dados: ordenando e selecionando o top 10.
top_10 = df.sort_values(by='Total', ascending=False).head(10)

# Configurando o estilo visual dos gráficos Seaborn.
sns.set_theme(style='whitegrid')

# Criando a figura e o gráfico de barras.
fig, ax = plt.subplots(figsize=(10, 6))
sns.barplot(data=top_10, y=top_10.index, x='Total', orient='h', palette='viridis')

# Adicionando contexto com títulos e rótulos.
ax.set_title('Top 10 Países por Volume de Imigração para o Canadá (1980-2013)', loc='left', fontsize=16)
ax.set_xlabel('Número Total de Imigrantes')
ax.set_ylabel('')

# O comando despine() remove as bordas superior e direita, deixando o visual mais limpo.
sns.despine()

plt.show()


# ## 5. Criando Visualizações Interativas com Plotly
# Gráficos interativos são excelentes para portfólios online, pois permitem que o usuário explore os dados.
# Vamos recriar a análise da América do Sul de forma interativa.

# Reformatando os dados para o formato que o Plotly espera (long format).
df_america_sul_clean = america_sul.drop(['Continente', 'Região', 'Total'], axis=1)
america_sul_final = df_america_sul_clean.T
america_sul_final.index.name = 'Ano'
america_sul_final = america_sul_final.reset_index()

# O Plotly Express facilita a criação de gráficos complexos.
# O argumento 'color' automaticamente cria uma linha para cada país.
fig = px.line(america_sul_final,
              x='Ano',
              y=america_sul_final.columns[1:], # Seleciona todas as colunas de países.
              title='Imigração da América do Sul para o Canadá (1980-2013)',
              markers=True) # Adiciona marcadores para destacar os pontos de dados anuais.

# Customizando o layout para melhor apresentação.
fig.update_layout(
    xaxis_title='Ano',
    yaxis_title='Número de Imigrantes',
    xaxis={'tickangle': -45},
    legend_title_text='Países'
)

# Salvando o gráfico interativo como um arquivo HTML.
fig.write_html('imigracao_interativa_america_sul.html')

fig.show()

Bibliotecas de Análise: Pandas

Bibliotecas de Visualização: Matplotlib, Seaborn, Plotly
