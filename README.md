# Spelling correction using Language Modelling 

## Description
This project uses a statistical language model and the concept of edit distance to identify and correct spelling mistakes in sentences. The sentences are compared against the SUBTLEXus lexicon, which is a frequency dictionary of written American English compiled from a corpus of 51 million words.

The main steps of the project are as follows:

1) **Running a Statistical Language Model**: A language model is defined and trained on a pre-processed corpus. The model calculates the vocabulary of the training corpus, updates n-gram counts, computes n-gram probabilities, and evaluates sentences based on their perplexity.
2) **Loading the Data**: The pre-processed corpus, sentences with typos, and the SUBTLEXus lexicon are loaded.
3) **Identifying Mistyped Words**: Each sentence is scanned for words not present in the SUBTLEXus lexicon. These words are considered mistyped. A dictionary mapping the sentence IDs to the mistyped words is created and stored in a JSON file.
4) **Correcting Mistyped Words**: The edit distance (Levenshtein distance) between each mistyped word and all words in the SUBTLEXus lexicon is calculated. The three closest words (or more, in the case of ties) in terms of edit distance are identified as the correction candidates. The sentence IDs, correction candidates, and their corresponding edit distances are stored in a dictionary and saved in a JSON file.

### Edit Distance Calculation  
This part of the project calculates the 'distance' between a misspelled word and potential correct words in the vocabulary. This is achieved by using the edit distance calculation functionality of the NLTK library. The edit distance is the number of one-character changes (insertions, deletions, or substitutions) needed to transform one word into another.

### Word Frequency Counts
In this part, the frequency of potential correct words in the SUBTLEXus corpus is used to prioritize higher frequency words over lower frequency ones. This is based on the idea that more commonly used words are more likely to be the intended correct words.

### Perplexity Calculation
This part of the project uses a trigram language model to calculate the perplexity of sentences that are created by replacing the misspelled word with a potential correct word. The best word is chosen based on the lowest perplexity, which represents the word that makes the sentence most probable under the language model.
