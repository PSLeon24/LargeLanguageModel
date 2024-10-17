# TextMining
NLP, BERT, transformer, etc

# Text Preprocessing Step
1. Cleaning
   - noise removal, stopword removal
2. Tokenization
   - 주어진 텍스트를 원하는 단위(token)로 나누는 작업, 일반적으로는 단어 토큰화(word tokenization)를 의미함.
     - 문장 토큰화(sentence tokenization), 단어 토큰화(word tokenization), ...
3. Normalization: stemming(어간 추출), lemmatize(표제어 추출)
   - 같은 의미를 가진 동일한 단어임에도 불구하고 다른 형태로 쓰여진 단어들을 통일시켜서 표준 단어로 만드는 작업
4. POS-Tagging
   - 토큰화한 단어에 대해 품사를 파악해 부착하는 것

## Cleaning
- noise & stopword removal(nltk의 stopwrds)
  - 길이가 짧은 단어들은 정규표현식을 써서 쉽게 제거 가능(영어에서 길이가 3 미만인 단어들은 삭제하는 것이 일반적)
  - 리스트를 활용하여 불용어 사전을 따로 만들어서 쉽게 제거할 수 있음

## Tokenization using NLTK
- Sentence Tokenization(nltk의 sent_tokenize)
  - 여러 문장으로 이루어진 텍스트를 각 문장으로 나누는 것(주로 . ! ? 등을 기준으로 분리)
- Word Tokenization(nltk의 word_tokenize)
  - 대상이 되는 텍스트를 단어 단위로 분리하는 작업
  - 한국어 텍스트를 정확하게 토큰화하려면 공백을 이용한 분리만으로는 부족함(의미를 가지는 최소단위가 형태소)
- Tokenizer using regular expression(nltk의 RegexpTokenizer)
  - 대상 문자열로부터 원하는 패턴의 문자열을 검색하여 세밀하게 토큰화할 수 있음

## Normalization
- Stemming: 어형이 변형된 단어로부터 접사 등을 제거하고 그 단어의 어간을 분리해 내는 작업(포터 스테머, 랭카스터 스테머, etc)
  - 어형: 단어의 형태
  - 어간(stem): 어형변화에서 변화하지 않는 부분, 용언의 바뀌지 않는 부분
    - 용언: 문장 안에서 서술하는 구실을 하는 동사와 형용사
    - 어형변화: 어떤 단어가 동일한 어간을 가지고 동일한 품사를 유지하면서, 그 어미를 여러 가지로 변화시켜 그에 따라 문법적 기능도 변화하는 현상
      - 통시적 어형변화, 공시적 어형변화
  - Poter Stemmer
    - 영어분야에서의 사실상의 표준 스테밍 알고리즘
    - 변환된 단어가 올바른 단어가 아니더라도, 동일한 형태로 변환되므로 분석의 의도를 충족시킬 수 있음
- Lemmatization
  - 주어진 단어를 기본형으로 변환하는 작업(WordNetLemmatizer)
- Stemming vs Lemmatization
  - 사전에 나오는 단어인지 아닌지의 차이로 구분 가능
  - 어간을 형태적으로 분리해내기만 하는 것은 stemming, 단어의 기본형을 찾는 것은 lemmatization

## POS-tagging(Part-of-Speech Tagging)
- nltk의 pos_tag()
- 우리말의 주요 품사
  |품사|설명|
  |---|---|
  |명사|이름을 나타내는 낱말|
  |대명사|이름을 대신해 가리키는 낱말|
  |수사|수량이나 순서를 가리키는 낱말|
  |조사|도와주는 낱말|
  |동사|움직임을 나타내는 낱말|
  |형용사|상태나 성질을 나타내는 낱말|
  |관형사|체언을 꾸며 주는 낱말|
  |부사|주로 용언을 꾸며 주는 낱말|
  |감탄사|놀람, 느낌, 부름, 대답을 나타내는 낱말|

- 공용 품사 태그 집합
  |품사|설명|예|
  |---|---|---|
  |adj|adjective|new, good, high, special, big, local|
  |adp|adposition|on, of, at, with, by, into, under|
  |adv|adverb|really, already, still, early, now|
  |conj|conjunction|and, or, but, if, while, although|
  |det|determiner, article|the, a, some, most, every, no, which|
  |noun|noun|year, home, costs, time, Africa|
  |num|numeral|twenty-four, fourth, 1991, 14:24|
  |prt|particle|ata, on, out, over, per, that, up, with|
  |pron|pronoun|he, their, her, its, my, I, us|
  |verb|verb|is, say, told, given, playing, would|
  |.|punctuation marks|. , ; !|
  |x|other|ersatz, esprit, dunno, gr8, univeristy

- 펜 트리뱅크 태그 집합(Penn Treebank Tagset)
![image](https://github.com/PSLeon24/TextMining/assets/59058869/1427c0df-f62d-484a-948d-6cb5a99c09df)

## Practice
- Hugging Face: A model hub community providing tools and resources for NLP and ML.
  - A community-driven model hub
  - "Transformer" library
- A tour of Transformer Applications : Text Classification, Named-Entity Recognition, Text Generation, Summarization, Question Answering

# 용어 정리
- 텍스트 마이닝(text mining): 자연어 처리 기법을 이요해 텍스트를 정형화된 데이터로 변환하고, 머신러닝 기법을 적용해 우리가 관심이 있는 어떤 사건을 예측하고자 하는 방법론
  - 이때, 정형화된 데이터는 '일정한 길이의 벡터'
- 임베딩(embedding): 주어진 텍스트를 일정한 길이의 벡터로 변환하는 것
- 희소(sparse)하다: 벡터의 크기가 큰 경우 벡터를 구성하는 많은 값이 0이고 극히 일부만 0이 아닌 값을 가질 때를 뜻함
- 밀집(dense)돼 있다: 벡터의 크기가 작은 경우 벡터를 구성하는 대부분이 값이 0이 아닌 값들로 이루어져 있을 때를 뜻함
- 말뭉치(corpus): 자연어 처리나 텍스트 마이닝을 위해 유사한 문서들을 모아 놓은 집합(e.g., 영화 리뷰 분석을 위해 대상 리뷰들을 모아 놓은 것)
- 단어 경계(word boundary): 공백과 같이 단어를 구분해 주는 것들
- 불용어(stopword): 의미 없는 특수문자 등과는 별도로, 실제 사용되는 단어이지만 분석에는 별 필요가 없는 단어들
  - 빈도가 너무 적거나 혹은 빈도가 너무 많아서 별 필요가 없는 단어
