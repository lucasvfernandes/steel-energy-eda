<p align="center">
  <img src="assets/logo.png" alt="Logo do Projeto Steel Industry" width="600">
</p>

Este repositório contém um projeto de estudo de caso focado na Análise Exploratória de Dados (EDA) do consumo energético em uma instalação da indústria siderúrgica. O objetivo principal é investigar padrões de consumo, eficiência operacional, emissões de carbono e riscos de custos tarifários utilizando Python.

## Fonte dos Dados
Os dados brutos utilizados nesta análise foram obtidos através da plataforma Kaggle e representam medições contínuas (intervalos de 15 minutos) do consumo elétrico industrial ao longo de um ano completo.
- **Dataset Original:** [Steel Industry Energy Consumption on Kaggle](https://www.kaggle.com/datasets/csafrit2/steel-industry-energy-consumption/data)

## Contexto e Objetivos
Indústrias siderúrgicas estão entre as operações de maior intensidade energética do mundo. A eficiência no uso da energia elétrica não apenas reduz custos operacionais massivos, mas também é vital para o cumprimento de metas de sustentabilidade (ESG). 

Este projeto busca responder às seguintes questões de negócio:
1. Qual é a correlação matemática entre o consumo de energia e a emissão de CO2?
2. Como a fábrica gerencia sua carga elétrica ao longo do dia, especialmente em horários de pico tarifário?
3. Qual é o nível de risco financeiro associado à ineficiência do maquinário (energia reativa e fator de potência)?

## Metodologia Aplicada
O projeto foi desenvolvido seguindo as melhores práticas de manipulação e análise estatística de dados:
* **Limpeza e Estruturação de Dados (ETL):** Padronização de nomenclatura, tratamento de formatos de data/hora (parsing de strings para objetos *datetime*), separação de variáveis contínuas em dimensões temporais (Data e Hora) e arredondamentos técnicos.
* **Engenharia de Features:** Transformação de variáveis categóricas nominais sobre a capacidade da fábrica (Carga Leve, Média e Máxima) em variáveis ordinais numéricas para possibilitar o cálculo de correlação de Pearson.
* **Análise Estatística e Visualização:** Criação de matrizes de correlação limpas (remoção de duplicatas e autocorrelações), gráficos de dispersão com linhas de tendência linear, curvas de carga sazonal e distribuições de frequência.

## Principais Descobertas e Insights de Negócio

### 1. Relação Direta entre Consumo e Impacto Ambiental
A matriz de correlação revelou um coeficiente de **0.99** entre o uso de energia (kWh) e as emissões de CO2. Isso comprova estatisticamente que a mitigação do impacto ambiental da instalação é estritamente dependente de melhorias na eficiência elétrica, descartando outras variáveis secundárias.
* Além disso, identificou-se uma correlação positiva forte (**0.61**) entre o Nível de Carga Operacional e o Consumo de Energia, validando a proporcionalidade do esforço do maquinário.

<p align="center">
  <img src="assets/heatmap_correlacao.png" alt="Tabela Estilizada de Correlações Fortes" width="800">
</p>

### 2. Sazonalidade Diária e Deslocamento de Carga (Peak Shaving)
A análise da curva de carga diária demonstra uma gestão ativa dos custos tarifários. A operação atinge seu consumo máximo (aprox. 55 kWh) às 16h, seguido por uma queda intencional para a faixa de 33 kWh às 18h. Isso indica uma estratégia clara de redução de carga para evitar as penalidades financeiras do "Horário de Ponta" da rede elétrica.

<p align="center">
  <img src="imagens/curva_carga.png" alt="Gráfico de Linha da Curva de Carga Diária com Horário de Ponta Destacado" width="800">
</p>

### 3. Risco Operacional Severo (Fator de Potência)
A descoberta mais crítica do estudo diz respeito à qualidade da energia consumida. Ao analisar a distribuição do Fator de Potência (Lag), constatou-se que a instalação operou abaixo do limite regulatório de segurança (92%) em **60.41%** das medições anuais. 
Do ponto de vista financeiro, isso significa que a fábrica está exposta a multas severas por energia reativa excedente na maior parte do seu tempo operacional. A instalação de bancos de capacitores seria a recomendação técnica imediata para mitigar este passivo financeiro.

<p align="center">
  <img src="imagens/histograma.png" alt="Histograma do Fator de Potência com Linha de Risco Legal" width="800">
</p>

## Tecnologias Utilizadas
* **Linguagem:** Python 3
* **Manipulação de Dados:** Pandas, NumPy
* **Visualização de Dados:** Matplotlib, Seaborn
