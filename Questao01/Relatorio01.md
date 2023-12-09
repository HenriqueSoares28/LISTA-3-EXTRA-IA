# Relatório questão 1 - LISTA EXTRA 3

## Aluno:
Henrique França Carvalho Soares

[LINK PARA O CODIGO](https://github.com/HenriqueSoares28/LISTA-3-EXTRA-IA)

#### Introdução
O objetivo deste projeto era desenvolver um modelo de aprendizado de máquina para classificar textos, determinando se estes abordam o tema "grãos" ou não, utilizando os dados disponíveis nos arquivos CSV "ReutersGrain-train.csv" e "ReutersGrain-test.csv".

#### Etapas Realizadas

1. **Leitura Inicial dos Dados**
   - Os arquivos CSV foram inicialmente lidos usando a função `pd.read_csv` do Pandas.
   - Foi encontrado um erro de tokenização, indicando inconsistências no número de campos entre as linhas.

2. **Primeira Tentativa de Limpeza de Dados**
   - Utilizamos `error_bad_lines=False` para ignorar linhas problemáticas.
   - Descobrimos que a maioria das linhas foi descartada, deixando um conjunto de dados muito reduzido.

3. **Segunda Tentativa de Limpeza de Dados**
   - Aumentamos o número de colunas esperadas e concatenamos todas as colunas de texto em uma única coluna.
   - Convertemos a última coluna em rótulos numéricos e removemos valores nulos.
   - Ainda assim, restaram poucos dados válidos.

4. **Construção e Treinamento do Modelo**
   - Construímos um pipeline utilizando o TfidfVectorizer e o classificador Naive Bayes.
   - O modelo foi treinado com sucesso, mas a avaliação revelou uma precisão de 100%, o que foi considerado enganoso devido ao tamanho reduzido do conjunto de teste.

5. **Nova Tentativa de Leitura e Formatação dos Dados**
   - Tentamos ler os dados novamente com um número maior de colunas e detecção automática de delimitadores.
   - Apesar de uma leitura bem-sucedida, todos os dados válidos foram perdidos após a limpeza, resultando em conjuntos de dados vazios.

#### Motivo do Erro
O principal problema encontrado foi a inconsistência na formatação dos arquivos CSV. As linhas dos arquivos não seguiam um padrão uniforme de delimitadores ou número de campos, o que levou a erros de tokenização e dificuldades na leitura e limpeza dos dados. Este problema foi exacerbado pelo fato de que as técnicas padrão de leitura de CSV não conseguiram lidar eficazmente com essas inconsistências, resultando em perda de dados significativa durante as tentativas de limpeza.

#### Conclusão
As inconsistências nos dados apresentaram desafios significativos, impedindo a construção de um modelo de classificação eficaz. Seria necessário uma inspeção manual dos dados ou a consulta à fonte dos dados para uma melhor compreensão da estrutura e formato esperados, permitindo uma abordagem mais informada para a limpeza e preparação dos dados. 