# Research Findings Summary: NLP Text Pre-processing

## 1. Origins and Challenges of NLP

### Historical Timeline (Four Eras)
- **1940-1969: Early Explorations**
  - Machine Translation (MT) was the driving force
  - Rule-based systems with handcrafted linguistic rules
  - First speech systems developed
  - Cyril Cleverdon's Cranfield tests (1957-1967) introduced benchmarking
  - Key figures: David Glenn Hays (ACL founder), Raj Reddy (Turing award winner)

- **1970-1992: Hand-built Symbolic Systems**
  - Terry Winograd's SHRDLU system
  - Formal and Unification-based Grammars (Martin Kay, Fernando Pereira, Stuart Shieber)
  - Increasing formalization of NLP systems
  - Focus on parsing and semantic composition

- **1993-2012: Statistical/Probabilistic NLP**
  - Shift from rule-based to statistical methods
  - Supervised Machine Learning approaches
  - Data-driven models replaced handcrafted rules

- **2013-Present: Deep Learning Era**
  - Neural networks and deep learning revolution
  - Unsupervised/Self-supervised learning
  - Transformer architectures (BERT, GPT)
  - Large Language Models (LLMs)

### Major Challenges in NLP
1. **Language Ambiguity**: Words with multiple meanings (polysemy), context-dependent interpretation
2. **Phrasing Ambiguities**: Same phrase can be evaluated in multiple ways
3. **Training Data Quality**: Need for diverse, representative, annotated corpora
4. **Misspellings and Grammatical Errors**: Linguistic noise in real-world text
5. **Bias in NLP Algorithms**: Demographic biases in training data
6. **Multilingualism**: Handling 7000+ languages worldwide
7. **False Positives and Uncertainty**: Model confidence and reliability
8. **Continuous Conversations**: Context maintenance in dialogue systems

## 2. Regular Expressions

### Core Concepts
- Pattern matching language for text manipulation
- Used for searching, matching, and manipulating strings
- Essential for text cleaning and preprocessing

### Common Operations
- Character classes and quantifiers
- Anchors (^ for start, $ for end)
- Groups and backreferences
- Lookahead and lookbehind assertions

### NLP Applications
- Tokenization boundaries
- Extracting email addresses, URLs, phone numbers
- Removing HTML tags
- Pattern-based information extraction
- Text validation and cleaning

## 3. Words - Corpora - Text Normalization

### Corpora (Plural of Corpus)
**Definition**: A large and structured set of texts used for linguistic analysis and NLP model training

**Types of Corpora**:
1. **Annotated Corpora**: Contains linguistic annotations (POS tags, parses, named entities)
2. **Unannotated Corpora**: Raw text without annotations
3. **Historical Corpora**: Texts from different historical periods
4. **Temporal Corpora**: Texts collected over time for language evolution studies
5. **Sentiment-Annotated Corpora**: Texts labeled with sentiment/emotion information
6. **Multilingual Corpora**: Parallel texts in multiple languages

**Applications**:
- Lexicography (dictionary creation)
- Language teaching and learning
- Speech processing and synthesis
- Machine translation training
- Statistical language modeling

### Text Normalization Techniques

**1. Tokenization**
- Breaking text into smaller units (tokens)
- Types: Word tokenization, sentence tokenization, subword tokenization
- Modern approaches: Byte-Pair Encoding (BPE), SentencePiece

**2. Lowercasing**
- Converting all text to lowercase for consistency
- Example: "NEW YORK" → "new york"

**3. Punctuation Removal**
- Eliminating special characters and punctuation marks
- Example: "I'm happy!!!" → "im happy"

**4. Stopword Removal**
- Removing extremely common words (the, is, am, are, of, to, in)
- Reduces noise and focuses on content words
- Domain-specific stopword lists improve results

**5. Stemming**
- Rule-based reduction of words to root form
- **Porter Stemmer**: 5-step algorithm, most popular
  - Step 1: Handles plurals and participles (caresses → caress)
  - Step 2: Deals with suffixes like -ational, -ness
  - Step 3: Reduces complex suffixes
  - Step 4: Checks for -al, -ance, -ence
  - Step 5: Final adjustments (removing -e, changing -ll to -l)
- Fast but may produce non-words (studies → studi)

**6. Lemmatization**
- Dictionary-based reduction to valid root form (lemma)
- Uses vocabulary and morphological analysis
- **WordNet Lemmatizer**: Based on WordNet lexical database
  - Groups words by synonymy and semantics
  - Requires POS tags for accuracy (noun, verb, adjective, adverb)
  - Examples: better → good, studies → study, mice → mouse
- More accurate but slower than stemming

**7. Part-of-Speech (POS) Tagging**
- Assigning grammatical categories to words
- Essential for accurate lemmatization
- Helps disambiguate word meanings

## 4. Minimum Edit Distance

### Definition
The minimum number of single-character operations (insertions, deletions, substitutions) required to transform one string into another.

### Levenshtein Distance
- Most common type of edit distance
- All operations have equal cost (typically 1)
- Operations:
  - **Insertion**: Add a character
  - **Deletion**: Remove a character
  - **Substitution**: Replace one character with another

### Example
Transforming "kitten" → "sitting":
1. kitten → sitten (substitute 'k' with 's')
2. sitten → sittin (substitute 'e' with 'i')
3. sittin → sitting (insert 'g')
**Edit Distance = 3**

### Dynamic Programming Solution (Wagner-Fischer Algorithm)
- Builds a matrix of size (m+1) × (n+1)
- Matrix[i][j] = edit distance between first i characters of string1 and first j characters of string2
- Recurrence relation:
  - If characters match: matrix[i][j] = matrix[i-1][j-1]
  - Else: matrix[i][j] = 1 + min(deletion, insertion, substitution)

### Applications in NLP
- Spell checking and correction
- DNA sequence alignment (bioinformatics)
- Plagiarism detection
- Machine translation evaluation
- Fuzzy string matching
- Speech recognition error analysis

## Key Insights for Educational Presentation

1. **Evolution Pattern**: NLP evolved from rule-based → statistical → neural approaches, with each era building on previous insights

2. **Preprocessing Pipeline**: Raw text → Cleaning (regex) → Normalization (tokenization, stemming/lemmatization) → Analysis-ready format

3. **Stemming vs Lemmatization Trade-off**: Speed vs Accuracy - choose based on application requirements

4. **Edit Distance Intuition**: Dynamic programming reuses solutions to subproblems, making exponential problem tractable in O(m×n) time

5. **Corpus Quality**: "Garbage in, garbage out" - quality of training data directly impacts model performance
