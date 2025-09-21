# Informational-Retrieval
Informational Retrieval project: This is a project submitted by three students. 

**File Content Description:**

Corpus: The folder contains the corpus used for the boolean retrieval model.

Outputs: The folder contains screenshots of all the outputs obtained while using test cases.

VSM.py: The python file where the ranked retrieval using vector space model is being implemented.

## Search System Overview

### Features Implemented:
1. **Document Ranking**:  
   The system ranks documents based on their relevance to the query. The ranking is performed using **TF-IDF** scores, where documents with higher term relevance are prioritized. If multiple documents share the same relevance, they are sorted by their document ID (ascending order).

2. **Spelling Matching using Soundex**:  
   To improve query matching, **Soundex** is employed to handle slight spelling variations in names and keywords. For example, even if a query like "Ridhima" is misspelled, the system can still identify relevant documents by matching similar-sounding terms.

## CELL BY CELL EXPLAINATION FOR OUR CODE ## 

# CELL 1 
The code allows you to upload text files and organizes them into a folder named ./Corpus:
Creates the ./Corpus directory if it doesn't already exist.
Prompts the user to upload their text files.
Moves the uploaded files into the ./Corpus directory for easy access.

# CELL 2 
The code handles the extraction of a ZIP file containing corpus documents. It specifies the path to the ZIP file and an output folder where the files will be extracted. If the output directory doesn't exist, it creates it. The ZIP archive is then extracted, and a confirmation message is displayed. After extraction, the code lists all the files inside the extracted folder and sets that path as the corpus directory for further processing.

# CELL 3 
The code implements a complete text-based document search system with preprocessing, TF-IDF weighting, vector similarity, and Soundex-based name matching.
The system begins by loading and preprocessing all documents from the specified corpus folder. Each document is cleaned (lowercased, punctuation removed, stopwords removed, and stemmed) and indexed. It then calculates document vectors using lnc (logarithmic term frequency + cosine normalization) and query vectors using ltc (log tf × idf + cosine normalization) weighting.
For search queries, the input is preprocessed similarly. It performs exact term matching and also applies the Soundex algorithm to match proper names based on phonetic similarity improving name recall even when spellings differ.
The system computes cosine similarity between the query vector and all document vectors, ranks them by relevance, and returns the top 10 results sorted by score and document ID. It also creates a postings file showing term frequencies across documents.

## NOW IN THESE 3 CELLS (4,5,6) WE HAVE SHOWN NOVELTY ( NEW IDEAS) WHICH MAKES OUR MODEL BETTER 
# CELL 4 
**Snippet Generation with Highlighted Query Terms**
The code generates short, context-rich snippets from documents that contain the user's query terms. It scans each document for occurrences of the query words, then extracts a small window of words around each match.
Matched terms are highlighted using **bold** formatting, and up to three such snippets are shown per document. This helps users quickly see how and where their query is relevant within each document.

# CELL 5 
**Query Expansion with WordNet Synonyms**
To improve search flexibility and recall, the system includes query expansion using synonyms from the WordNet lexical database. When a user enters a query, each term is automatically expanded with a few relevant synonyms. This allows the search engine to retrieve documents containing not only the exact query terms but also related words with similar meanings.
## For example, a query like food may be expanded to include words like nutrient, meal, or solid food, making the search results more comprehensive.
This feature helps match documents that are semantically related, even if they don’t contain the exact words typed by the user.

# CELL 6 
## Visualization of Top Terms by TF-IDF Score
This part of the system performs TF-IDF vectorization on the document corpus to identify the most important terms across all documents. The TF-IDF (Term Frequency-Inverse Document Frequency) scores highlight terms that are frequent in particular documents but less common across the entire corpus, helping to surface distinctive words.
The top 20 terms with the highest cumulative TF-IDF scores are then visualized in a horizontal bar chart, providing a clear and intuitive overview of the most significant keywords in the dataset. 
