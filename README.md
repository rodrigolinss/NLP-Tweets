# Kaggle Competition: Natural Language Processing with Disaster Tweets

Este projeto apresenta uma solução para a competição (["Natural Language Processing with Disaster Tweets"](https://www.kaggle.com/competitions/nlp-getting-started)) do Kaggle. O desafio consiste em classificar tweets como genuínos ou não sobre desastres reais.

## Abordagem Principal: TF-IDF e Regressão Logística

A solução implementada neste notebook se baseia em uma combinação eficaz de técnicas clássicas de Processamento de Linguagem Natural (PLN) e Aprendizado de Máquina, demonstrando que, em muitos casos, abordagens simples podem ser bastante competitivas.

O processo pode ser resumido da seguinte forma:

* **Preparação do Texto:** Os tweets são inicialmente submetidos a uma série de etapas de limpeza e normalização para remover elementos irrelevantes e padronizar o conteúdo.
* **Representação Numérica:** O texto é então transformado em uma forma numérica, que os modelos de aprendizado de máquina podem processar. A técnica utilizada para essa conversão é o TF-IDF (Term Frequency-Inverse Document Frequency).
* **Classificação:** Finalmente, um modelo de Regressão Logística é treinado para realizar a classificação dos tweets.

**Resultados:**

A abordagem descrita alcançou um score de 0.79313 na competição, evidenciando a eficácia de modelos bem ajustados para essa tarefa.

## Implementação Detalhada

O código é organizado para seguir um fluxo lógico e claro:

1.  **Configuração Inicial:** O notebook começa com a instalação das bibliotecas necessárias e a importação dos módulos relevantes do Python.
2.  **Carregamento dos Dados:** Os conjuntos de dados de treinamento (`train.csv`) e teste (`test.csv`) fornecidos pela competição são carregados na memória usando a biblioteca pandas.
3.  **Pré-processamento:** A função `preprocess_text` é definida e aplicada para limpar os tweets. As principais etapas de limpeza incluem:
    * Conversão para minúsculas
    * Remoção de URLs e tags HTML
    * Remoção de números e pontuação
    * Remoção de stopwords (palavras muito comuns que não contribuem para o significado)
    * Remoção de espaços extras
4.  **Divisão e Vetorização:** Os dados de treinamento são divididos em conjuntos de treinamento e validação para permitir a avaliação do modelo. O `TfidfVectorizer` é então utilizado para gerar a representação TF-IDF do texto. Este vetorizador é configurado para:
    * Limitar o número máximo de features (`max_features`) para controlar a complexidade do modelo.
    * Utilizar apenas palavras individuais (unigramas) nesta versão inicial.
5.  **Treinamento do Modelo:** Um modelo de Regressão Logística é instanciado e treinado com os dados de treinamento vetorizados. O número máximo de iterações (`max_iter`) é definido para garantir a convergência do algoritmo.
6.  **Avaliação:** O modelo treinado é avaliado no conjunto de validação, utilizando métricas como acurácia, F1-score e um relatório de classificação detalhado.
7.  **Persistência do Modelo:** O modelo treinado e o vetorizador TF-IDF são salvos em um arquivo, permitindo que sejam reutilizados sem a necessidade de re-treinamento.
8.  **Geração do Arquivo de Submissão:** As previsões são geradas para o conjunto de teste, e um arquivo `submission.csv` é criado no formato esperado pelo Kaggle. A ordem das previsões é cuidadosamente mantida para corresponder aos IDs dos tweets no conjunto de teste.
9.  **Conclusão:** O notebook finaliza com uma análise dos resultados e uma discussão sobre a eficácia da abordagem implementada.

Este README fornece um guia completo para entender e reproduzir a solução desenvolvida para a competição.
