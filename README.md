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

# Instruções
Para executar os códigos:
1. Entrar no arquivo cuja extensão é .ipynb
2. Clicar em "Open in Colab"
3. Em "Arquivo", faça uma cópia para o seu Drive
   Nesta etapa, precisa estar logado com o seu gmail.
4. Na lateral esquerda, clique no botão de executar em cada bloco de código
