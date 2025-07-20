# WSCariri-DE: Um dataset enriquecido de séries temporais eólicas para o semiárido Paraibano

Este repositório contém o dataset **WSCariri-DE**, um conjunto de dados de velocidade do vento com granularidade horária para a localidade de São João do Cariri (PB), no semiárido brasileiro.

## 📜 Descrição

O dataset **WSCariri-DE** fornece uma série temporal contínua e validada, cobrindo o período de 1 de janeiro de 2006 a 31 de dezembro de 2009. Ele foi criado para solucionar o desafio das falhas temporais presentes nos dados públicos da estação anemométrica do projeto SONDA, que originalmente possuía 3.197 horas de dados ausentes (9,12% do total).

A metodologia de criação envolveu a integração dos dados observados em solo (SONDA) com dados de reanálise atmosférica da fonte NASA POWER. As lacunas foram preenchidas utilizando um modelo de Machine Learning (Random Forest), escolhido por sua robustez e estabilidade na imputação de falhas extensas. O resultado é um ativo de dados completo e confiável, pronto para suportar novas pesquisas em energia renovável.

## 👥 Autores

* Isaac Gomes Veras 
* Dr. Alex Sandro da Cunha Rêgo 
* Dr. Damires Yluska de Souza Fernandes 
* Dr. Thiago Gouveia

## 🔑 Palavras-chave

energia eólica, séries temporais, machine learning, imputação de dados, semiárido paraibano, velocidade do vento

---

## 📊 Características do Dataset

* **Nome do Arquivo**: `WSCariri-DE.csv`
* **Formato**: CSV (Comma-Separated Values)
* **Total de Registros**: 35.064 
* **Granularidade Temporal**: Horária 
* **Período Coberto**: 01/01/2006 a 31/12/2009 
* **Geolocalização**: Estação São João do Cariri, Paraíba, Brasil 
    * **Latitude**: -7,3817° (07° 22' 54" S) 
    * **Longitude**: -36,5272° (36° 31' 38" O) 

## 📂 Estrutura do Arquivo (`WSCariri-DE.csv`)

O arquivo CSV contém três colunas principais:

* `datetm`: Data e hora da observação no fuso horário local, em formato de texto (`YYYY-MM-DD HH:MM:SS`).
* `SONDAWS50`: A variável principal do dataset. Representa a velocidade do vento (em m/s) a 50 metros de altura, originária da estação SONDA. As falhas temporais nesta série foram preenchidas pelo modelo Random Forest.
* `NASAWS50`: A velocidade do vento (em m/s) a 50 metros de altura, originária da base de dados de reanálise atmosférica NASA POWER. Esta série foi utilizada como a principal variável exógena para treinar o modelo de imputação.

## ⚙️ Metodologia de Criação

O dataset foi gerado através de um pipeline de seis etapas:

1.  **Aquisição e Organização**: Coleta automatizada dos dados da SONDA (período 2006-2009) e da NASA POWER.
2.  **Análise Exploratória**: Diagnóstico da qualidade dos dados, identificação de 3.197 falhas na série SONDA e de um viés sistemático de 1,72 m/s entre as fontes.
3.  **Pré-processamento**: Limpeza de dados (remoção de valores negativos), padronização do índice temporal e reamostragem da série SONDA para uma granularidade horária.
4.  **Integração**: Unificação das séries tratadas em um único dataframe.
5.  **Modelagem e Imputação**: Comparação de modelos SARIMAX e Random Forest, com a escolha do RF por sua estabilidade em preencher lacunas longas.
6.  **Criação do Dataset Final**: Aplicação do modelo RF treinado para preencher todas as lacunas e gerar o arquivo `WSCariri-DE.csv`.

## 💡 Aplicações Potenciais

Este conjunto de dados pode ser utilizado para:

* Análise de viabilidade de projetos eólicos e cálculo da Produção Anual de Energia (AEP).
* Caracterização robusta do recurso eólico da região (e.g., ajuste de distribuição de Weibull).
* Estabelecer uma linha de base climatológica para correlacionar com novas campanhas de medição.
* Servir como benchmark de alta qualidade para o treinamento e validação de modelos de previsão de curto prazo (nowcasting).

## ✍️ Como Citar

Se você utilizar este dataset em sua pesquisa, por favor, cite o artigo original:

> Veras, I. G., Rêgo, A. S. C., Fernandes, D. Y. S., & Gouveia, T. (2025). *WSCariri-DE: Um dataset enriquecido de séries temporais eólicas para o semiárido Paraibano*. [Nome da Revista, se aplicável].

## 🙏 Agradecimentos

Agradecemos ao projeto Prediction Of Worldwide Energy Resources (POWER) do Langley Research Center da National Aeronautics and Space Administration (NASA), financiado pela NASA Earth Science Division, pela disponibilização dos dados de reanálise atmosférica que foram fundamentais para o desenvolvimento deste trabalho.
