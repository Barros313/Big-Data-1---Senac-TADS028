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

## Análise de Dados

### Infrações por mês

#### Gráfico em barra de infrações por mês

Foi utilizado funções do pyspark para agrupar e contar o número de ocorrências iguais em casa mês e depois substituído o valor da coluna pelo seu respectivo mês para mostrar no gráfico

![image](https://github.com/Barros313/Big-Data-1---Senac-TADS028/assets/118929483/634f005f-0e42-45da-87c5-27a628b98786)

Baseado nos dados extraídos é possível perceber que o mês onde mais é cometido infrações é Janeiro.

#### Infrações por mês ordenado pelo maior número de ocorrências

Principal infração de cada mês e sua respectiva quantidade de ocorrências

| Mês |	Descrição da Infração |	Quantidade de ocorrências |
|-|-|-|
| 01 - Janeiro |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	17834
| 04 - Abril |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	17310
| 03 - Março |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	16156
| 05 - Maio |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	15593
| 02 - Fevereiro |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	14026
| 06 - Junho |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	13447
| 10 - Outubro |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	8823
| 07 - Julho |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	8569
| 09 - Setembro |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	8203
| 08 - Agosto |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	7440
| 11 - Novembro |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	7241

Baseado nos dados é possível perceber que a infração mais comum é de excesso de velocidade, mais especificamente em até 20%.

## Infrações por hora

### Gráfico em barra da infrações de hora

Utilizado funções do pyspark para agrupare contar o número de ocorrências por hora

![image](https://github.com/Barros313/Big-Data-1---Senac-TADS028/assets/118929483/f4dde335-7e67-4c53-9c51-a4d44b06f4c3)

Baseado nos dados desse gráfico é possível observar que os horários que mais ocorrem infrações é entre às 08:00 e às 11:00 e 14:00 e às 15:00

### Os 5 horários com a maior quantidade de infrações únicas cometidas

| Horário cometimento | Infração mais cometida | Quantidade de ocorrência |
|-|-|-|
| 15:00 - 15:59 |	ESTACIONAR O VEÍCULO EM DESACORDO COM AS CONDIÇÕES REGULAMENTADAS - ESTACIONAMENTO ROTATIVO. |	16578 |
| 10:00 - 10:59 |	ESTACIONAR O VEÍCULO EM DESACORDO COM AS CONDIÇÕES REGULAMENTADAS - ESTACIONAMENTO ROTATIVO. |	12635 |
| 13:00 - 13:59	|  TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	12394 |
| 14:00 - 14:59 |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	12047 |
| 12:00 - 12:59 |	TRANSITAR EM VELOCIDADE SUPERIOR À MÁXIMA PERMITIDA PARA O LOCAL EM ATÉ 20% (VINTE POR CENTO). |	11386 |

Com base nos dados da tabela acima é possível perceber que apesar da infração de excesso de velocidade ser a mais cometida no geral, a infração mais cometida por horário é a de estacionar em estacionamento rotativo de forma irregular no final da manhã e no meio da tarde.

### Gráfico em barra com o comparativo entre as 5 infrações mais comuns

![image](https://github.com/Barros313/Big-Data-1---Senac-TADS028/assets/118929483/b68c09f5-fc59-4384-a2e5-f97041705203)
