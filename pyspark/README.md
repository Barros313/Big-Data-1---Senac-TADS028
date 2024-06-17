# Relatório 2a Entrega - [Infrações de Trânsito em Recife (2023)](http://dados.recife.pe.gov.br/es/dataset/registro-das-infracoes-de-transito/resource/c269789d-da47-4dde-8ce7-42fba10fe8e2)

Este relatório apresenta uma análise detalhada das infrações de trânsito registradas na cidade do Recife ao longo do ano de 2023. O dataset estudado está disponível na base de dados do site da Prefeitura do Recife.

## Grupo

*  Gabriel Barros
*  Hugo Vasconcelos
*  Giovanni Santos
*  Doublas Oliveira

## Inicialização do ambiente

| Depêndencias utilizadas | Descrição |
|-|-|
| pyspark | API para criação e análise do dataset utilizado |
| urllib | Download do arquivo CSV pela api disponibilizado no site da prefeitura |
| pandas | Vizualização de dados |
| matplotlib | Criação de gráficos |

Ao gerar o dataframe utilizando spark foi utilizado parâmetros de 'encoding', para corrigir erros de caractere, e 'sep' para separar os atributos entre as colunas

`encoding = 'ISO-8859-1'`
`sep = ';'`

`df = spark.read.csv('infracoes.csv', encoding='ISO-8859-1', sep=';', header=True, inferSchema=True)`

## Tratamento de Dados

Para tratar dados utilizamos os comandos disponíveis pelo import `pyspark.sql.functions`. O que foi feito:

| Processo realizado | Resultado |
|-|-|
| Procurar por valores nulos | O dataset já não possui valores nulos |
| Padronizar colunas | Passando todos os atributos das colunas que contém `string` para maiúsculo utilizando `upper()` |
| Procurar por valores não numéricos | A única coluna com valores numéricos é a coluna infração, e todas as colunas possuem valores numéricos |
| Verificando valores na coluna Amparo Legal | Foram encontrados 4 valores errados na coluna, todos foram substituídos por INDEFINIDO |
