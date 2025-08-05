# Semantic Change Analysis of Colonial Terminology in Dutch Newspapers (1860-1960)

This repository contains code and data to analyse the semantic evolution of colonial terminology in a dataste of Dutch newspapers using Word2Vec embeddings and POS analysis. We examine semantic change in colonial terminology across two major Dutch newspapers:
- **Algemeen Handelsblad** (liberal perspective, 1860-1960)
- **De Telegraaf** (conservative to far-right, 1893-1960)

The study spans three time periods: 1860-1899, 1900-1939, and 1940-1960, focusing on how colonial terminology evolved across different ideological contexts and historical events.

### Data Collection & Preprocessing

- **`multithreaded_delpher.py`**: Scrapes newspaper articles from the Delpher digital archive using their API with multithreading for efficient data collection for the 1880-1960 period. For the 1860-1879 data, you can download from Delpher: https://www.delpher.nl/over-delpher/delpher-open-krantenarchief/download-teksten-kranten-1618-1879#b1741.
  
- **`data_cleaning.py`** to preprocesses raw text data by:
  - Removing punctuation, symbols, and numerical characters
  - Filtering words shorter than 3 characters
  - Removing function words (articles, prepositions, conjunctions) and punctuations.
  
  If your data are in English, you can directly use the model training configurations in config.yaml setting the preprocessing skip to False (see model_training).

### Embeddings Analysis

- **`model_training`** to train Word2Vec models for each newspaper and time period. The code is adapted from `https://github.com/Living-with-machines/DiachronicEmb-BigHistData/tree/main`.
  
- **`handelsblad_change.py`** & **`telegraaf_change.py`** to perform embeddings-based analysis:
  - Cosine similarity analysis
  - Nearest neighbours analysis
  - Classification of change patterns (divergence, stability, parallel change)

### Connotation Analysis

- **`pos_tagging.py`**:
  - Assigning POS tags to all words using spaCy Dutch model (nl_core_news_sm)
    
- **`connotation_analysis.py`**:
  - Extracting adjective modifiers for keywords nouns 
  - Extracting nouns for keywords adjectives

## 🤝 Contributing

This repository is associated with academic research. For questions or collaboration inquiries, please contact jiaqi.zhu@dh.huc.knaw.nl.
