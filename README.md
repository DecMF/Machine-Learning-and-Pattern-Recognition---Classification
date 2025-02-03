# Predição Salarial de Profissionais de Dados no Brasil

Este projeto foi desenvolvido como parte da disciplina **MO444**, ministrada pela professora **Sandra**, e contou com a colaboração de **Rafael Simionato(IC/Unicamp)**. O objetivo é explorar modelos de regressão e classificação para prever o salário de profissionais da área de dados no Brasil, evitando overfitting e analisando diferentes abordagens de modelagem.

## Objetivo do Projeto
Realizar predições do salário de profissionais da área de dados no Brasil, com base nos dados da pesquisa **State of Data Brazil 2023**, levando em consideração variáveis como perfil demográfico, formação, experiência e atuação no setor. Foram aplicadas técnicas de tratamento de dados, análise exploratória, regressão linear e regressão logística para melhor compreensão do problema e das variáveis preditoras.

## Base de Dados
A base de dados utilizada foi extraída do [State of Data Brazil 2023](https://www.kaggle.com/datasets/datahackers/state-of-data-brazil-2023). Os dados refletem uma pesquisa realizada com profissionais brasileiros da área de Ciência de Dados, coletando informações sobre:

- Perfil demográfico;
- Situação profissional;
- Conhecimentos técnicos;
- Faixa salarial.

O dataset contém diversas variáveis, como idade, gênero, formação acadêmica, tempo de experiência, linguagens utilizadas, setor de atuação, entre outras. O conjunto de dados foi dividido em:

```
train_data.csv
test_data.csv
```

O conjunto de validação foi gerado a partir do conjunto de treino (Holdout), e o conjunto de teste foi reservado apenas para inferência e avaliação final.

## Tratamento de Dados
Antes da modelagem, realizamos diversas etapas de pré-processamento:

- **Tratamento de valores ausentes**: Algumas variáveis foram imputadas usando métodos estatísticos e KNN;
- **Análise de correlação**: Exclusão de variáveis com alta correlação para evitar multicolinearidade;
- **Remoção de outliers**: Identificação e remoção de valores extremos que poderiam afetar os modelos;
- **Codificação de variáveis categóricas**: Aplicação de **one-hot encoding** e **label encoding** dependendo do tipo de variável;
- **Normalização**: Aplicada a algumas variáveis para melhorar o desempenho dos modelos.

## Modelagem

### Regressão Linear
Foi implementada uma **regressão linear** para prever o salário dos profissionais. Utilizamos dois métodos para ajuste do modelo:

1. **Descida do Gradiente**: Implementação manual da otimização por gradiente, armazenando o histórico da função de custo para análise do comportamento do modelo;
2. **Equação Normal**: Implementação analítica para encontrar diretamente os coeficientes da regressão.

A regressão linear segue a seguinte formulação:

- **Equação Normal:**
  \[
  \theta = (X^T X)^{-1} X^T y
  \]
  Essa equação fornece uma solução fechada para os coeficientes do modelo sem necessidade de iterações.

- **Gradiente Descendente:**
  \[
  \theta_j := \theta_j - \alpha \frac{\partial J(\theta)}{\partial \theta_j}
  \]
  Onde \( \alpha \) é a taxa de aprendizado e o custo minimizado é dado por:
  \[
  J(\theta) = \frac{1}{2m} \sum_{i=1}^{m} (h_{\theta}(x^{(i)}) - y^{(i)})^2
  \]
  Esse método otimiza iterativamente os coeficientes até a convergência.

#### Resultados da Regressão Linear
- O modelo implementado **from-scratch** demonstrou uma suavidade na minimização da métrica de loss (RMSE);
- A curva de aprendizado indicou uma queda acentuada nas primeiras 50 épocas, seguida por uma estabilização;
- Comparação entre métodos mostrou que o **gradiente descendente** aproximou bem os resultados da **equação normal**;
- Foram testados diferentes valores de **learning rate**, identificando o melhor valor para um balanceamento entre convergência e estabilidade.

### Regressão Logística
A segunda parte do projeto envolveu a **classificação da faixa salarial** dos profissionais utilizando **regressão logística**. Aqui, buscamos prever categorias salariais em vez de valores contínuos.

#### Resultados da Regressão Logística
- Mesmo após testes com diferentes configurações de hiperparâmetros, o modelo apresentou baixa acurácia e F1-Score;
- A matriz de confusão revelou dificuldades do modelo em classificar corretamente certas faixas salariais;
- Recomenda-se testar modelos mais sofisticados, como árvores de decisão e redes neurais, para melhorar a performance.

## Conclusões
Os experimentos revelaram alguns insights importantes:

- Modelos de regressão linear via gradiente descendente e equação normal tiveram desempenhos próximos;
- A escolha do learning rate impacta significativamente a convergência do gradiente descendente;
- A regressão logística apresentou dificuldades na classificação das faixas salariais, sugerindo a necessidade de modelos mais complexos;
- Algumas variáveis demonstraram grande influência na previsão salarial, enquanto outras tiveram pouco impacto.

## Próximos Passos
- Testar outros modelos preditivos, como árvores de decisão e redes neurais;
- Refinar a engenharia de features para melhorar a qualidade das variáveis utilizadas;
- Realizar mais experimentos com hiperparâmetros para otimizar o desempenho dos modelos.

## Créditos
Este projeto foi desenvolvido por **Decio Miranda Filho** e **Rafael Simionato** no contexto da disciplina **MO444** da Unicamp, sob orientação da professora **Sandra Avilla**.



