# Descrição do Projeto
Este repositório contém exemplos práticos desenvolvidos durante a disciplina de Processamento de Linguagem Natural (PLN) da Fatec Mauá. O objetivo da matéria é proporcionar uma compreensão de como os computadores podem analisar, compreender e interpretar a linguagem humana, por meio de técnicas e ferramentas de PLN, como tokenização, lematização, vetorização e embeddings.

## Aula 2: Fundamentos da Linguística

### Exemplo 1 - Demonstração de Segmentação, Tokenização e Árvore de Dependência
Neste exemplo, o código utiliza a biblioteca **SpaCy** para segmentação de frases, tokenização, e visualização das relações das palavras. Inicialmente é carregado o modelo pré-treinado usando o comando `spacy.load()`, pois contêm informações sobre a gramática e o vocabulário das línguas. Depois ocorre a etapa em que o texto é dividido em frases com o método `frase.sents` que usa pontuações para segmentar o texto. Após essa etapa, o texto é processado com `nlp()` e permite a visualização dos tokens, sendo de cada palavra, classes gramaticais e/ou relações das palavras dentro da frase. Por fim, ocorre a exibição da árvore de dependência (`displacy.render()`) para facilitar a compreensão de como cada palavra se conecta a outras. 

### Exemplo 2 - Tokenização em Português com NLTK
Neste exemplo, a biblioteca **NLTK** é usada para segmentar e tokenizar um texto em português. Primeiro, é solicitado que o usuário insira uma frase em português, esta é processada pela função `nlp()`, que transforma o texto em um objeto chamado **doc**. Depois, examina cada palavra do texto e exibe sua classe gramatical e a palavra da qual ele depende. Por fim, árvore de dependência é exibida.

---

## Aula 3 - Bibliotecas e Corpora

### Exemplo 1 - Utilização da Biblioteca NLTK com Corpora
**Corpora** são grandes coleções de texto e está contida na biblioteca NLTK. No exemplo, usa o corpus "Machado" e através do método `machado.raw()` retorna o conteúdo de um arquivo dentro do corpus.

### Exemplo 2 - Contagem de Palavras com o Corpus Brown
Com o **Corpus Brown** usado no exemplo, é possível acessar palavras em uma categoria específica, como **news**. O código utiliza a função `FreqDist()` para contar quantas vezes cada palavra aparece em uma categoria, permitindo identificar palavras mais frequentes em um contexto.

### Exemplo 3 - Eliminação de Palavras Irrelevantes
As **stopwords** são palavras que não agregam muito valor semântico ao texto, como preposições, artigos e conjunções, pois isso são removidas. No exemplo é filtrado as palavras irrelevantes de um conjunto de palavras retiradas do **Corpus Bronw**. Após a remoção, é contado as palavras mais frequentes no corpus **news**.

---

## Aula 4 - Limpeza de Dados Textuais

### 4.1 Normalização de Texto e Remoção de Ruído
Nessa etapa trata-se de limpar o texto, removendo caracteres especiais, pontuações e normalizando o uso de maiúsculas e minúsculas. O código utiliza expressões regulares (`r'[^A-Za-zÀ-ÿ\s]'`) para substituir todos os caracteres que não sejam letras ou espaços por uma string vazia. Em seguida, o texto é convertido para minúsculas (`.lower()`) para garantir uniformidade.
 
### 4.2 Tokenização
No código, o **NLTK** é utilizado para dividir o texto em palavras com a função `word_tokenize()`. Depois é calculado o número total de tokens com `len()`.

### 4.3 Remoção de StopWords
Um conjunto de stopwords em português é carregado com `stopwords.words('portuguese')`, depois o texto tokenizado é filtrado para remover essas palavras, por fim é mostrado o número de tokens após a remoção das stopwords.

### 4.4 Stemming e Lematização
- **Stemming** reduz as palavras às suas raízes.
- **Lematização** normaliza as palavras para suas formas base, levando em conta o contexto e a gramática.
No código o **RSLPStemmer** é usado para realizar o stemming em português. Depois, as palavras são reduzidas aos seus radicais com a função `stem()`.

### 4.5 Utilizando Todo o Processo de Limpeza
Neste exemplo, o processo completo de limpeza de dados textuais é realizado em um texto de exemplo. Isso inclui a limpeza do texto, tokenização, remoção de stopwords e stemming das palavras.

---

## Aula 5 - Representação de Texto

### Exemplo 1 - Implementando o BoW (Bag of Words)
O **Bag of Words (BoW)** é uma técnica de vetorização de texto que cria um modelo de vetor onde cada palavra corresponde a uma coluna da matriz, a presença ou ausência de cada palavra é indicada por valores binários. O **CountVectorizer** do **scikit-learn** é utilizado para criar a matriz BoW a partir de uma lista de documentos. Depois a função `fit_transform()` é usada para transformar o texto em uma matriz de contagens. Depois é exibida com `toarray()`.

### Exemplo 2 - Implementando BoW com TF-IDF
**TF-IDF** é uma variação do BoW que mostra a importância das palavras. Como o anterior, o **CountVectorizer** é usado para criar a matriz BoW, depois  o **TfidfVectorizer** é utilizado para aplicar a técnica de TF-IDF e por fim o vocabulário e as matrizes são exibidos.

### Exemplo 3 - Pré-processamento Completo e Representação de Texto
Esse exemplo aplica todo o processo de pré-processamento, incluindo a limpeza do texto, tokenização, remoção de stopwords e lematização e representação do texto em formato de matriz, usando BoW.

---

## Aula 6 - Representação de Texto com Embeddings

### Exemplo 1 - Word2Vec
**Word2Vec** é uma técnica de embeddings de palavras que mapeia palavras em vetores num espaço contínuo. No exemplo, o **Gensim** é utilizado para treinar um modelo sobre um corpus de frases. Depois, a similaridade entre duas palavras é calculada com `model.wv.similarity()`, que retorna um valor entre 0 e 1.

### Exemplo 2 - GloVe
**GloVe** (Global Vectors for Word Representation) é uma técnica de embeddings que se baseia em matrizes de simultaneidade de palavras.  No código, o **KeyedVectors** da é utilizado para carregar um modelo pré-treinado do GloVe. Depois, a similaridade entre palavras é calculada com o método `similarity()`. Por fim, exibe as palavras mais próximas do termo `king` com `most_similar()`.

### Exemplo 3 - FastText
**FastText** é uma variação do Word2Vec, desenvolvida pelo Facebook. No código, o modelo **FastText** é carregado a partir de um arquivo, depois calcula-se a similaridade entre palavras e exibe mais próximas de `gato`.

---

## Aula 7 - Modelagem de Tópicos com Latent Dirichlet Allocation (LDA)
### Exemplo 1 - Implementação de LDA no Corpus de Notícias
Neste exemplo, o corpus Reuters é utilizado para realizar a modelagem de tópicos. Os dados passam por um processo de pré-processamento, que inclui a remoção de stopwords, lematização e tokenização dos textos. A partir disso, é criado um dicionário que mapeia todas as palavras do corpus, e cada documento é transformado em um conjunto de índices associados ao dicionário. O modelo LDA é treinado utilizando a biblioteca Gensim, com um número predefinido de tópicos. Após o treinamento, os tópicos extraídos são apresentados, destacando as palavras mais representativas de cada tópico e suas respectivas probabilidades.

### Visualização dos Tópicos
Para visualizar os tópicos gerados, utiliza-se o pacote `pyLDAvis`, que permite criar uma interface interativa. Essa visualização facilita a exploração dos tópicos gerados pelo modelo, mostrando a relação entre os tópicos e as palavras que os compõem.

### Exemplo 2 - Aplicação de LDA em um Corpus Customizado
Neste segundo exemplo, é realizado um processo de modelagem de tópicos utilizando um corpus customizado, criado manualmente ou carregado de um arquivo externo. O procedimento segue os mesmos passos do primeiro exemplo: o corpus é pré-processado, tokenizado, e é gerado um dicionário. Em seguida, o modelo LDA é treinado com os textos customizados, permitindo ajustar o número de tópicos de acordo com a necessidade. Após o treinamento, são exibidos os tópicos, apresentando as palavras-chave de cada tópico e probabilidades associadas.

---

## Aula 08 - Introdução a Machine Learning para PLN
### Exemplo 01 - Aplicação do modelo de Naive Bayes em um texto
Neste exemplo, é demonstrado como aplicar o modelo de Naive Bayes para classificação de sentimentos em textos. Começa com a criação de um corpus de frases rotuladas como positivas ou negativas. O processo de pré-processamento é realizado utilizando expressões regulares para limpar e normalizar o texto. Após o pré-processamento, são calculadas as probabilidades condicionais e probabilidades para cada classe (positiva ou negativa). O modelo é então treinado, e utiliza o cálculo da probabilidade de um novo texto com base nas palavras presentes, retornando a classe mais provável para o sentimento do texto.

### Exemplo 02 - Classificação com Support Vector Machine (SVM)
Neste exemplo, a `Support Vector Machine (SVM)` é utilizada para classificar textos em categorias de sentimentos. O corpus de exemplo contém frases rotuladas, e o modelo é treinado a partir da representação dos textos utilizando o método TF-IDF para vetorização. O código divide os dados em conjuntos de treinamento e teste e treina o modelo SVM com o kernel linear. Ao final, o modelo é avaliado com a precisão da classificação, usando a métrica de classification_report do scikit-learn.

### Exemplo 03 - Comparando os classificadores: Naive Bayes vs SVM
Neste exemplo, é feita a comparação entre dois algoritmos de aprendizado de máquina para a tarefa de classificação de sentimentos: `Naive Bayes` e `Support Vector Machine (SVM)`. O dataset utilizado é o corpus de críticas de filmes do `NLTK`. O código realiza o pré-processamento dos textos, aplicando técnicas como `TF-IDF` para vetorização e LabelEncoder para transformação das classes em valores numéricos. Em seguida, os modelos são treinados e avaliados em um conjunto de teste, e as performances de ambos os classificadores são comparadas usando a função `classification_report`.

---

# Instruções
Para executar os códigos:
1. Entrar no arquivo cuja extensão é .ipynb
2. Clicar em "Open in Colab"
3. Em "Arquivo", faça uma cópia para o seu Drive
   Nesta etapa, precisa estar logado com o seu gmail.
4. Na lateral esquerda, clique no botão de executar em cada bloco de código
