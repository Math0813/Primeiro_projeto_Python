
# Análise de Vendas

## Descrição do Projeto

Este projeto tem como objetivo analisar os dados de vendas de uma empresa, buscando identificar os produtos mais vendidos, o faturamento de cada produto e a loja/cidade que obteve o maior faturamento. Através de uma série de etapas de análise, foram extraídos insights úteis para otimizar as estratégias de vendas da empresa.

---

## Tecnologias Utilizadas

- **Python 3.7+**
- **Bibliotecas:**
  - `pandas`: Para manipulação e análise de dados.
  - `plotly.express`: Para visualização de dados interativa (gráficos).

---

## Como Executar

### Em Ambientes Locais (VS Code, PyCharm)

1. **Instale o Python:**  
   - Baixe em [https://www.python.org/](https://www.python.org/).  
   - Certifique-se de marcar "Add Python to PATH" durante a instalação.

2. **Instale as bibliotecas necessárias:**  
   No terminal, execute o seguinte comando:
   ```bash
   pip install pandas plotly
   
3. **Salve o código em um arquivo .py e execute no terminal:**

   python nome_do_script.py

### Em Ambientes Online (Google Colab, Kaggle)
**Google Colab**
As bibliotecas pandas e plotly já estão pré-instaladas. Basta importar e carregar os dados.
**Kaggle Notebooks**
Carregue seus arquivos de vendas utilizando o caminho correto:

tabela_total = pd.read_csv("../input/vendas-dados/vendas.csv")
____________________________________________
### Passos da Análise
**1. Leitura dos arquivos de vendas:**

O código percorre a pasta Vendas e lê todos os arquivos que contêm "vendas" no nome.
Todos os arquivos são combinados em um único DataFrame para análise posterior.

**2. Cálculo do Produto Mais Vendido (em quantidade):**

O código agrupa as vendas por produto e calcula a quantidade total vendida.

**3. Cálculo do Produto que Mais Faturou:**

O faturamento de cada produto é calculado multiplicando a "Quantidade Vendida" pelo "Preço Unitário".
A lista de produtos é ordenada por faturamento, identificando quais produtos geraram mais receita.

**4. Identificação da Loja/Cidade com Maior Faturamento:**

A análise é expandida para identificar qual loja ou cidade teve o maior faturamento.
A análise é visualizada em um gráfico interativo utilizando Plotly.

_____________________________________________________
## Exemplo de Código 

import os
import pandas as pd

# Lista os arquivos na pasta de vendas
lista_arquivo = os.listdir("/content/drive/MyDrive/curso basico de python/Curso Básico de Python/Vendas")

# Cria uma lista para armazenar as tabelas
tabelas = []

# Itera sobre os arquivos
for arquivo in lista_arquivo:
    if "vendas" in arquivo.lower():  # Verifica se "vendas" está no nome do arquivo
        # Lê o arquivo CSV
        tabela = pd.read_csv(f"/content/drive/MyDrive/curso basico de python/Curso Básico de Python/Vendas/{arquivo}")
        tabelas.append(tabela)  # Adiciona a tabela à lista

# Combina todas as tabelas em um único DataFrame
tabela_total = pd.concat(tabelas, ignore_index=True)

# Exibe o DataFrame final
display(tabela_total)

_________________________________________________

## Gráficos Interativos

A análise também inclui a criação de gráficos interativos para visualizar as informações de forma clara e dinâmica. Um exemplo de gráfico gerado pelo código é o gráfico de faturamento por loja:

import plotly.express as px

# Criação de um gráfico de barras para visualizar o faturamento por loja
grafico = px.bar(tabela_lojas, x=tabela_lojas.index, y="Faturamento")
grafico.show()

