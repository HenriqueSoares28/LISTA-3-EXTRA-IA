# Relatório questão 2 - LISTA EXTRA 3

## Aluno:
Henrique França Carvalho Soares

[LINK PARA O CÓDIGO](https://github.com/HenriqueSoares28/LISTA-3-EXTRA-IA)

#### Introdução
Este projeto visa desenvolver um modelo de aprendizado de máquina para a classificação de comentários de texto, identificando diferentes formas de toxicidade, como toxicidade severa, obscenidade, ameaça, insulto e ódio contra identidades. Utilizamos para isso os dados disponibilizados nos arquivos CSV "test.csv", "test_labels.csv" e "train.csv".

#### Etapas Realizadas

1. **Preparação Inicial e Leitura dos Dados**
   - Utilizamos o NLTK para baixar listas de stopwords e tokenizers, essenciais para o pré-processamento de texto.
   - Carregamos os dados de treino e teste usando a função `pd.read_csv` do Pandas.
   - Removemos do DataFrame `test_labels` as linhas com rótulos inconsistentes (-1), que não seriam úteis para o treinamento e avaliação do modelo.

2. **Pré-processamento dos Dados**
   - Dividimos os dados de treinamento em conjuntos de características (X) e rótulos (y) e aplicamos a mesma divisão aos dados de teste.
   - Criamos uma função `preprocess_text` para limpar e preparar o texto dos comentários, removendo stopwords, pontuações e opcionalmente aplicando stemming.

3. **Vetorização do Texto**
   - Utilizamos `TfidfVectorizer` para converter o texto dos comentários em uma matriz de características TF-IDF, uma representação numérica que reflete a importância das palavras no contexto do conjunto de dados.

4. **Treinamento do Modelo**
   - Inicializamos um classificador `BinaryRelevance` com `MultinomialNB` (Naive Bayes multinomial) para lidar com a classificação multirrótulo.
   - Treinamos o modelo com os dados de treinamento vetorizados.

5. **Avaliação do Modelo**
   - Realizamos a predição nos dados de teste e calculamos métricas de avaliação como precisão, recall e pontuação F1, que são importantes para entender o desempenho do modelo em diferentes aspectos.

#### Desafios e Considerações
- **Pré-processamento de Texto:** A qualidade do pré-processamento de texto tem um impacto significativo na eficácia do modelo. A escolha de incluir ou excluir o stemming pode afetar o desempenho.
- **Vetorização:** A limitação do número de características (`max_features`) em `TfidfVectorizer` é um ponto de equilíbrio entre performance e precisão. Muitas características podem levar a um modelo mais preciso, mas também mais lento e potencialmente propenso a overfitting.
- **Classificação Multirrótulo:** O desafio de prever múltiplos rótulos simultaneamente é significativamente maior do que a classificação binária ou multiclasse padrão.

#### Conclusão
Este projeto demonstrou a aplicação de técnicas de processamento de linguagem natural e aprendizado de máquina para classificar comentários de texto em categorias de toxicidade. A abordagem adotada, embora desafiadora, é crucial para moderar e entender o discurso em plataformas online. Os resultados obtidos oferecem uma base sólida para futuras melhorias e ajustes, buscando otimizar a precisão e a eficácia do modelo em identificar e categorizar comentários tóxicos.