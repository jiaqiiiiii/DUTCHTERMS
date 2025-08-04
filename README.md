# Semantic Change Analysis of Colonial Terminology in Dutch Newspapers (1860-1960)

This repository contains the code and data documentation for our paper analysing the semantic evolution of colonial terminology in Dutch newspapers using Word2Vec embeddings and connotation analysis.

## 📖 Overview

We examine semantic change in colonial terminology across two major Dutch newspapers:
- **Algemeen Handelsblad** (liberal perspective, 1860-1960)
- **De Telegraaf** (conservative to far-right, 1893-1960)

The study spans three time periods: 1860-1899, 1900-1939, and 1940-1960, focusing on how colonial terminology evolved across different ideological contexts and historical events.

## 🗂️ Repository Structure

```
├── scripts/
│   ├── multithreaded_delpher.py    # Delpher API scraping script
│   ├── pos_tagging.py              # POS tagging and keyword analysis
│   ├── handelsblad_change.py       # Semantic change analysis for Handelsblad
│   ├── telegraaf_change.py         # Semantic change analysis for Telegraaf
│   ├── data_cleaning.py            # Text preprocessing for model training
│   └── model_training.py           # Word2Vec model training script
├── models/
│   ├── handelsblad_1860_1899.model # Word2Vec models (6 total)
│   ├── handelsblad_1900_1939.model
│   ├── handelsblad_1940_1960.model
│   ├── telegraaf_1893_1899.model
│   ├── telegraaf_1900_1939.model
│   └── telegraaf_1940_1960.model
├── data/
│   └── delpher_files_list_1880s_as_example.csv  # Example filenames from Delpher
└── README.md
```

## 🔧 Scripts Description

### Data Collection & Preprocessing

- **`multithreaded_delpher.py`**: Scrapes newspaper articles from the Delpher digital archive using their API with multithreading for efficient data collection for the 1880-1960 period.For the 1860-1880 data, you can download from Delpher: [
](https://www.delpher.nl/over-delpher/delpher-open-krantenarchief/download-teksten-kranten-1618-1879#b1741)

- **`data_cleaning.py`**: Preprocesses raw text data by:
  - Removing punctuation, symbols, and numerical characters
  - Filtering words shorter than 3 characters
  - Removing function words (articles, prepositions, conjunctions)
  - Standardising text for model training

### Model Training

- **`model_training.py`**: Trains Word2Vec models for each newspaper and time period using:
  - Vector size: 300 dimensions
  - Training epochs: 3
  - Separate models for each temporal period

### Analysis Scripts

- **`pos_tagging.py`**: Conducts connotation analysis by:
  - Adding POS tags to all words using the spaCy Dutch model
  - Highlighting specific colonial keywords when used as nouns
  - Extracting adjective modifiers for connotative analysis
  - Analysing usage patterns over time

- **`handelsblad_change.py`** & **`telegraaf_change.py`**: Perform embeddings-based analysis:
  - Cosine similarity calculations across time periods
  - Nearest neighbours analysis for semantic change detection
  - Orthogonal Procrustes alignment for cross-temporal comparison
  - Classification of change patterns (divergence, stability, parallel change)

## 📊 Data

### Target Keywords
We analyse 25 colonial/racial terminology variants, including:
- `blanke`, `neger`, `creool`, `inlander`, `primitief`, `koeli`
- And their plural/variant forms (see `pos_tagging.py` for complete list)

### Dataset Statistics
- **Temporal coverage**: 1860-1960 (100 years)
- **Newspapers**: Algemeen Handelsblad (full period), De Telegraaf (1893-1960)
- **Content type**: Articles only (excluding advertisements and announcements)
- **Time periods**: 1860-1899, 1900-1939, 1940-1960

*Note: Due to copyright restrictions, we cannot publish the full newspaper corpus. The `delpher_files_list_1880s_as_example.csv` file contains example filenames from our 1880s dataset to demonstrate data structure.*

## 🛠️ Requirements

```bash
# Core dependencies
pandas
spacy
gensim  # for Word2Vec
scikit-learn  # for Procrustes alignment
tqdm
numpy
matplotlib  # for visualisation
```

### spaCy Model
```bash
python -m spacy download nl_core_news_sm
```

## 🚀 Usage

### 1. Data Collection
scripts/multithreaded_delpher.py

### 2. Data Preprocessing
scripts/data_cleaning.py

### 3. Model Training
scripts/model_training.py

### 4. Semantic Change Analysis
# Analyze Handelsblad
scripts/handelsblad_change.py

# Analyze Telegraaf  
scripts/telegraaf_change.py

### 5. Connotation Analysis
scripts/pos_tagging.py

## 📈 Methodology

### Embeddings-based Analysis
1. **Model Training**: Separate Word2Vec models for each newspaper and time period
2. **Alignment**: Orthogonal Procrustes method to align different vector spaces
3. **Similarity Measurement**: Cosine similarity across time periods (reference = 1 for first period)

### Connotation Analysis
1. **POS Tagging**: spaCy Dutch model for grammatical analysis
2. **Keyword Extraction**: Colonial terms used as nouns
3. **Modifier Analysis**: Adjectives modifying target keywords
4. **Temporal Tracking**: Frequency changes of connotative adjectives over time

## 📚 Historical Context

### Time Period Significance
- **1860-1899**: Commercial exploitation phase of Dutch colonialism
- **1900-1939**: Implementation of Ethical Policy (1901) marking ideological transition
- **1940-1960**: Japanese occupation (1942-1945) and decolonisation struggles

## ⚖️ Data Ethics & Limitations

- **Temporal Imbalance**: De Telegraaf missing initial 33 years (1860-1893)
- **Copyright**: Full newspaper corpus cannot be shared publicly
- **Historical Context**: Analysis of historical terminology for academic research purposes
- **Bias Acknowledgment**: Different editorial perspectives may influence language patterns

## 📄 Citation

```bibtex
[The paper citation will go here]
```

## 🤝 Contributing

This repository is associated with academic research. For questions or collaboration inquiries, please contact jiaqi.zhu@dh.huc.knaw.nl.
