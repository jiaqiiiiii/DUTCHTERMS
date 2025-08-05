# Semantic Change Analysis of Colonial Terminology in Dutch Newspapers (1860-1960)

This repository contains the code and data documentation for our paper analysing the semantic evolution of colonial terminology in Dutch newspapers using Word2Vec embeddings and connotation analysis.

## 📖 Overview

We examine semantic change in colonial terminology across two major Dutch newspapers:
- **Algemeen Handelsblad** (liberal perspective, 1860-1960)
- **De Telegraaf** (conservative to far-right, 1893-1960)

The study spans three time periods: 1860-1899, 1900-1939, and 1940-1960, focusing on how colonial terminology evolved across different ideological contexts and historical events.

## 🔧 Scripts Description

### Data Collection & Preprocessing

- **`multithreaded_delpher.py`**: Scrapes newspaper articles from the Delpher digital archive using their API with multithreading for efficient data collection for the 1880-1960 period. For the 1860-1879 data, you can download from Delpher: https://www.delpher.nl/over-delpher/delpher-open-krantenarchief/download-teksten-kranten-1618-1879#b1741.
  
- **`data_cleaning.py`**: Preprocesses raw text data by:
  - Removing punctuation, symbols, and numerical characters
  - Filtering words shorter than 3 characters
  - Removing function words (articles, prepositions, conjunctions)
  - Standardising text for model training

### Embeddings model

- **`model_training.py`**:
- Trains Word2Vec models for each newspaper and time period using:
  - Vector size: 300 dimensions
  - Training epochs: 3
  - Separate models for each temporal period

### Analysis Scripts

- **`pos_tagging.py`**:
  - Adding POS tags to all words using the spaCy Dutch model
  - Highlighting specific colonial keywords when used as nouns
- **`connotation_analysis.py`**:
  - Extracting adjective modifiers for connotative analysis
  - Analysing usage patterns over time

- **`handelsblad_change.py`** & **`telegraaf_change.py`**:
- Perform embeddings-based analysis:
  - Cosine similarity calculations across time periods
  - Nearest neighbours analysis for semantic change detection
  - Orthogonal Procrustes alignment for cross-temporal comparison
  - Classification of change patterns (divergence, stability, parallel change)

## 🤝 Contributing

This repository is associated with academic research. For questions or collaboration inquiries, please contact jiaqi.zhu@dh.huc.knaw.nl.
