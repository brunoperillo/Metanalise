# Metanalise

 O arquivo `Tarefa Metanalise.pdf` descreve o estudo e a análise do estudo.

## Metanálise dos efeitos da intervenção com vitamina E na mortalidade em adultos

Este projeto consiste em uma metanálise que tem como objetivo analisar os efeitos da intervenção com vitamina E na mortalidade em adultos. O estudo combina os resultados de estudos clínicos randomizados sobre esse tema específico.

## Dados

Os dados utilizados neste projeto estão disponíveis no arquivo `vite1.csv`. Esse arquivo contém as informações dos estudos, incluindo o tamanho da amostra, os eventos de mortalidade e as informações relevantes para a análise.
A imagem a seguir apresenta os dados dos Estudos Incluídos na Metanálise
![image](https://github.com/brunoperillo/Metanalise/assets/25699466/0eae959e-5b47-4765-be83-232dafca5b7d)
- A tabela de dados é composta por sete colunas e descrita por:
- "estudo": representa o nome ou identificador único de cada estudo incluído na análise.
- "ano": indica o ano em que o estudo foi realizado ou publicado.
- "evtto": refere-se ao número de eventos (por exemplo, mortes) observados no grupo de intervenção (vitamina E).
- "ntto": representa o tamanho da amostra do grupo de intervenção (vitamina E), ou seja, o número total de participantes nesse grupo.
- "evcont": indica o número de eventos (por exemplo, mortes) observados no grupo de controle (placebo).
- "ncont": representa o tamanho da amostra do grupo de controle (placebo), ou seja, o número total de participantes nesse grupo.
- "idade": fornece uma descrição da faixa etária ou idade dos participantes do estudo, como "Maior que 60" ou "Menor que 60".

## Análise

O código para a análise dos dados está disponível no arquivo `metanalise.R`. Esse arquivo contém o script em R que realiza a metanálise, utilizando técnicas estatísticas apropriadas para combinar os resultados dos estudos incluídos.

A análise dos dados é realizada usando o pacote `metafor` no R. Abaixo está um exemplo de código que ilustra como carregar os dados do arquivo CSV e realizar a análise de metanálise:

```R
# Carregar o pacote metafor
library(metafor)

# Carregar os dados do arquivo CSV
dados <- read.csv("vite1.csv")

# Realizar a análise de metanálise para dados categóricos (proporções)
meta_analysis <- metabin(event = dados$evtto, n = dados$ntto, event.e = dados$evcont, n.e = dados$ncont, method = "Inverse", sm = "OR")

# Exibir os resultados da metanálise
summary(meta_analysis)
forest(meta_analysis)
```

Certifique-se de ajustar o caminho e o nome do arquivo CSV (`"vite1.csv"`) de acordo com o nome real e a localização do seu arquivo de dados.


Gráfico de Forest: Resultados da Metanálise com Modelo de Efeito Comum e Efeito Aleatório
![image](https://github.com/brunoperillo/Metanalise/assets/25699466/e7ec3448-ce2b-44ba-9ffd-a990606c51f5)



## Pré-requisitos

- R versão 3.5 ou superior
- Pacote `metafor` versão 2.1.0 ou superior

## Instalação

1. Certifique-se de ter o R instalado em sua máquina local.
2. Abra o arquivo `metanalise.R` em uma IDE ou no console do R.
3. Instale o pacote `metafor` caso ainda não esteja instalado, utilizando o seguinte comando no console do R:

   ```R
   install.packages("metafor")
