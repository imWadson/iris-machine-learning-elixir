# Iris Machine Learning com Elixir

Este projeto é o resultado dos meus estudos com o livro *Machine Learning in Elixir* (super recomendo, aliás!), onde mergulhei no mundo do machine learning usando Elixir, uma linguagem que eu já achava incrível pelo seu estilo funcional e agora vejo como poderosa até para ciência de dados. Aqui, você vai encontrar um notebook Livebook que implementa um modelo de classificação para o clássico dataset Iris, aquele com flores e medidas de pétalas e sépalas que todo mundo usa para aprender ML. 😄

Meu objetivo com este projeto foi entender como construir um pipeline de machine learning do zero: carregar dados, processá-los, treinar um modelo, e interpretar os resultados, tudo isso com ferramentas modernas do ecossistema Elixir. Foi uma jornada e tanto, e espero que este repositório seja útil para quem está começando ou quer ver como ML funciona em Elixir!

## O que tem aqui?

Este repositório contém um notebook Livebook (`Classifying Flowers.livemd`) que guia você pelo processo de construção de um modelo de classificação supervisionada para o dataset Iris. Aqui vai um resumo do que estudei e implementei:

- **Dataset Iris**: Um conjunto de dados com 150 amostras de três espécies de flores (setosa, versicolor e virginica), cada uma com 4 características (comprimento e largura de sépala e pétala). É um problema de classificação multiclasse, perfeito para iniciantes.
- **Pré-processamento**: Usei a biblioteca Explorer para carregar os dados e normalizar as features, garantindo que o modelo não ficasse confuso com escalas diferentes. Aprendi a usar `across` para aplicar transformações em várias colunas de uma vez, o que achei bem interessante!
- **Conversão para tensores**: Transformei os dados em tensores com Nx, a biblioteca de computação numérica do Elixir. Também codifiquei os rótulos como one-hot para o treinamento (ex.: `[1, 0, 0]` para setosa).
- **Modelo de rede neural**: Criei uma rede neural simples com Axon, começando com uma camada de entrada para as 4 features e uma camada densa com 3 neurônios (um para cada classe) com ativação softmax. É basicamente uma regressão logística multinomial, mas foi ótimo para entender como redes neurais funcionam.
- **Treinamento supervisionado**: Treinei o modelo com um algoritmo de aprendizado supervisionado, usando a função de perda `categorical_cross_entropy` (porque é classificação multiclasse) e o otimizador SGD (gradiente descendente estocástico). Configurei 10 épocas, e o modelo ajustou 15 parâmetros (12 pesos + 3 biases).
- **Resultados**: Após o treinamento, consegui uma acurácia de cerca de 93% no conjunto de teste (dependendo da divisão dos dados). Ver o modelo prever corretamente as espécies foi bem gratificante!

## Bibliotecas Usadas

O projeto usa algumas bibliotecas incríveis do ecossistema Elixir:

- **Explorer**: Para manipulação de dados, como carregar CSVs, normalizar features, e dividir o dataset em treino/teste. É como o pandas do Python, mas com aquele toque funcional do Elixir.
- **Nx**: A base para computação numérica, permitindo trabalhar com tensores (arrays multidimensionais)

- **Axon**: Usada para definir e treinar a rede neural. Axon torna a construção de modelos super intuitiva, com uma API que lembra Keras, mas em Elixir puro.
- **Livebook**: O ambiente interativo onde tudo acontece. Escrevi o notebook `.livemd`, que mistura código, explicações, e até visualizações. É perfeito para experimentar e aprender.

## Tipo de Treinamento

O treinamento é **supervisionado**, o que significa que o modelo aprende a partir de dados rotulados. No caso do Iris, cada amostra vem com a espécie correta


## Como Executar

Quer rodar o notebook e ver o modelo em ação? É bem simples:

1. **Instale o Livebook**:
   - Siga as instruções em [livebook.dev](https://livebook.dev/) para instalar localmente ou use uma instância online.
   - No terminal, você pode rodar:
     ```bash
     mix escript.install hex livebook
     livebook server
     ```