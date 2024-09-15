# Harris/Trump Debate Analysis

## Overview

This project is focused on analyzing speeches through various Natural Language Processing (NLP) techniques using R. The main goal is to extract insights from speeches, such as readability, word patterns (n-grams), and sentiment, in order to understand the language used, complexity, and tone of the content.

## Features

### 1. **Readability Analysis**
   - We calculate several readability metrics to evaluate how easy or difficult the speech is to read and understand:
     - **Flesch-Kincaid Grade Level**: Indicates the U.S. school grade level required to understand the text.
     - **SMOG Index**: Estimates the years of education needed to comprehend the text, with a focus on complex words.
     - **Coleman-Liau Index**: Another metric that evaluates reading difficulty based on the length of words and sentences.
   - These metrics help us assess whether the speech is suitable for its target audience (general public, professionals, etc.).

### 2. **N-gram Analysis (Bigrams and Trigrams)**
   - We extract **bigrams** (two-word combinations) and **trigrams** (three-word combinations) to:
     - Identify common phrases and key topics.
     - Understand the patterns of language used in the speech.
     - Highlight specific areas of emphasis or repetition in the text.
   - The frequency of n-grams helps to focus on the most important themes and recurring ideas throughout the speech.

### 3. **Sentiment Analysis**
   - Using the **AFINN lexicon**, we perform sentiment analysis to determine the overall emotional tone of the speech:
     - Words are scored based on positivity or negativity, and the aggregate score represents the overall sentiment.
     - Sentiment analysis provides insight into whether the speech is more positive, negative, or neutral in tone.

## How It Works

1. **Text Tokenization**: The speech is tokenized into individual words and n-grams (bigrams, trigrams).
2. **Stop Word Removal**: Common stop words (e.g., "the", "is", "and") are removed to focus on the most meaningful terms.
3. **Readability Scores**: Readability metrics such as Flesch-Kincaid, SMOG, and Coleman-Liau are computed using the `textstat_readability` function and custom formulas where necessary.
4. **N-gram Analysis**: We calculate the frequency of bigrams and trigrams using term frequency and visualize the most common phrases.
5. **Sentiment Analysis**: The sentiment of the speech is assessed using predefined lexicons (such as AFINN), providing a score based on the emotional content of the words.

## Example Usage

Here’s an example of how the code can be used to process a speech and generate readability scores:

```r
# Load libraries
library(quanteda)
library(textstat)
library(tidytext)
library(dplyr)

# Load the speech
speech_text <- "Your speech text goes here..."

# Create a corpus from the speech
corpus_speech <- corpus(speech_text)

# Compute readability scores
readability_scores <- textstat_readability(corpus_speech, measure = c("Flesch.Kincaid", "SMOG", "Coleman.Liau"))

# Print the results
print(readability_scores)
```

## Readability Score Interpretation

- **Flesch-Kincaid Grade Level**: Indicates the U.S. school grade level required to understand the text (e.g., a score of 8.1 means the text is suitable for someone with an 8th-grade education).
- **SMOG Index**: Typically higher than Flesch-Kincaid, this score focuses on the number of complex words (words with 3+ syllables) and is often used in technical or health-related content.
- **Coleman-Liau Index**: Measures readability based on sentence length and character count, often used in academic texts.


## Requirements

- R (version >= 4.0.0)
- Required R packages: `quanteda`, `textstat`, `tidytext`, `dplyr`, `ggplot2` (for visualization)

