# 🚦 [Infrações de Trânsito em Recife (2023)](http://dados.recife.pe.gov.br/es/dataset/registro-das-infracoes-de-transito/resource/c269789d-da47-4dde-8ce7-42fba10fe8e2) 

## 👥 Equipe

- Gabriel Barros
- Hugo Vasconcelos
- Giovanni Santos
- Douglas Oliveira

## 📁 Diretórios

|Entrega|Pasta|Descrição|
|-|-|-|
|1a Unidade|[/sqlite](https://github.com/Barros313/Big-Data-1---Senac-TADS028/tree/main/sqlite)| Análise do dataset utilizando sqlite e pandas |
|2a Unidade|[/pyspark](https://github.com/Barros313/Big-Data-1---Senac-TADS028/tree/main/pyspark)|Análise do dataset utilizando pyspark|

## 📊 Sobre o Dataset

Este banco de dados tem grande importância para o tráfego e a segurança da região de Recife. Estudando estes dados podemos ter benefícios como:
1. **Identificação de áreas de risco:** Analisando as localidades com maior incidência de infrações, as autoridades podem identificar áreas de risco que requerem medidas especiais de segurança viária, como instalação de sinalização adicional, redução de velocidade ou melhorias na infraestrutura.
2. **Planejamento de políticas de trânsito:** Com base nos tipos e frequência das infrações, as autoridades podem planejar e implementar políticas de trânsito mais eficazes, como campanhas educativas, fiscalização intensificada em áreas críticas e alterações na legislação de trânsito.
3. **Melhoria da mobilidade urbana:** Compreender os padrões de infrações pode ajudar a melhorar a mobilidade urbana, identificando gargalos no tráfego e áreas onde são necessárias melhorias na infraestrutura viária, como novas rotas, faixas exclusivas para transporte público ou áreas de estacionamento adicionais.
4. **Avaliação de programas de segurança viária:** O banco de dados pode ser usado para avaliar a eficácia de programas de segurança viária em curso, ajudando a determinar se as medidas implementadas estão reduzindo o número de infrações e aumentando a segurança nas vias.
5. **Previsão e prevenção de acidentes:** Analisando os dados das infrações, é possível identificar padrões que podem indicar situações de risco e ajudar na previsão e prevenção de acidentes de trânsito, através da implementação de medidas preventivas adequadas.

### Análise Exploratória

| Descrição | Valor |
|-----------|-------|
| Quantidade de Registros | 459713 |
| Variáveis Disponíveis | 8 |

### Dicionário de Dados

| Campo | Descrição | Tipo | Tamanho |
|-------|-----------|------|---------|
| datainfracao | Data em que ocorreu a infração | DATE | 10 |
| horainfracao | Hora de registro da infração | DATE | 10 |
| dataimplantacao | Data da implantação da multa | DATE | 10 |
| agenteequipamento | Forma de autuação | CHAR | 50 |
| infracao | Código da Infração | NUMBER | 10 |
| descricaoinfracao | Descrição da infração | CHAR | 200 |
| localcometimento | Local onde ocorreu a infração | CHAR | 200 |
| amparolegal | Amparo legal para registro da infração | CHAR | 50 |
