# The Evolution and Expression of Morality in Song Lyrics

This repository contains the code and data accompanying the paper **“The Evolution and Expression of Morality in Song Lyrics”**, prepared for submission to *Scientific Reports*.  
It provides scripts, datasets, and Jupyter notebooks used to analyse moral trends in music lyrics across six decades, employing models for moral foundation prediction, sentiment and emotion extraction, and topic modelling.



## 📘 Summary

This project investigates how moral values have evolved in song lyrics from **1960 to 2023**, using two main datasets:  
1. **WASABI Dataset (1960–2010)** – a large-scale, metadata-rich corpus of over 2 million songs.  
2. **Billboard Year-End Songs Dataset (1960–2023)** – a curated collection of commercially successful tracks.  

Transformer-based models fine-tuned for **Moral Foundations Theory (MFT)** prediction were applied to quantify ten moral dimensions in lyrics.  
Analyses explore temporal evolution, artist gender, genre differences, and correlations between moral foundations, sentiment, emotion, and lyrical topics.


## 📂 Repository Structure

```
├── data/
│
├── notebooks/
│   ├── billboard/
│   └── wasabi/
│
├── requirements.txt
└── README.md
```


## 📊 Datasets

### **1. WASABI Dataset (1960–2010)**
For data access and API documentation, please refer to:  
🔗 https://wasabi.i3s.unice.fr/apidoc/

We queried English-language songs between 1960–2010, retrieving metadata (artist, genre, lyrics, release year, etc.).  
This dataset offers a comprehensive and balanced resource for analysing long-term lyrical and moral trends.

### **2. Billboard Year-End Songs (1960–2023)**
The Billboard dataset was created by scraping **Wikipedia Year-End Hot 100** charts (1960–2023) and fetching lyrics via the **Genius API**.  
It contains approximately **5,580 songs** (≈87 per year).  

Dataset path:  
[Dataset/data/billboard/](https://github.com/vjosapreniqi/Lyrics-Moral-Evolution/blob/master/Dataset/Billboard_Year_End_1960_2023.csv)

> *Note:*  
> To comply with copyright restrictions, full song lyrics retrieved via the Genius API are **not included** in this repository.  
> Only derived data (e.g., moral scores, sentiment, and emotion features) and metadata are provided.  
> You can reproduce the lyrics collection process using the provided notebooks and your own Genius API key.


## 💻 Notebooks Overview

The repository separates code by dataset (**WASABI** / **Billboard**) using consistent methods.  
Each Jupyter Notebook includes data processing, visualisations, and model outputs.

### **Billboard Code**
**Folder:** `/notebooks/billboard/`

| Notebook | Description |
|-----------|--------------|
| *Billboard_Get_Top_100_Year_End_Songs.ipynb* | Scrapes Wikipedia Year-End Hot 100 charts (1960–2023) to collect song titles and artist information. |
| *Billboard_Get_Artists_Gender_Genre_Song_Lyrics.ipynb* | Retrieves artist gender and genre from the MusicBrainz API and fetches lyrics from the Genius API. |
| *Billboard_Moral_Evolution_Gender_Genre_Analysis.ipynb* | Performs temporal analyses using Generalised Additive Models (GAMs) to explore changes in moral foundations over time by artist gender and genre. |

### **WASABI Code**
**Folder:** `/notebooks/wasabi/`

| Notebook | Description |
|-----------|--------------|
| *Extracting_Sentiment_Emotion_Features_for_WASABI_Lyrics.ipynb* | Extracts sentiment and emotion features (valence, arousal, dominance) using the VADER and NRC lexicons. |
| *MFT_Regression_and_Correlations.ipynb* | Performs regression and correlation analyses between moral foundations and lyrical features (topics, sentiment, emotions, similarity). |
| *LDA_Topic_Modelling_WASABI_Lyrics.ipynb* | Applies Latent Dirichlet Allocation (LDA) to extract key lyrical themes such as *Love and Emotions*, *Violence and Darkness*, and *Spiritual and Dreamy*. |
| *WASABI_Moral_Evolution_Gender_and_Genre_Analysis.ipynb* | Analyses moral evolution trends using GAMs, stratified by artist gender and music genre. |


## 💡 Predicting Moral Foundation Scores

To reproduce or extend the moral predictions used in this work, please refer to the **MoralBERT** repository:  
🔗 [Predict moral scores with MoralBERT](https://github.com/vjosapreniqi/MoralBERT/blob/main/MoralBert/Predict_mft_scores_from_the_MoralBERT_weights.ipynb)

Pre-trained models for lyrics are available on Hugging Face:  
🔗 [Hugging Face Models – vjosap](https://huggingface.co/vjosap)


## ⚙️ Methods Summary

- **Moral Foundation Prediction:** via *MoralBERT SL* — fine-tuned on GPT-4–generated synthetic lyrics and annotated social media data.  
- **Sentiment & Emotion Extraction:** using **VADER** and **NRC Word–Emotion Lexicons**.  
- **Topic Modelling:** via **LDA** (k = 6 topics, optimised using Cv coherence metric).  
- **Temporal Modelling:** via **Generalised Additive Models (GAMs)** for non-linear trend estimation.  
- **Regression & Correlation:** via **XGBoost** models and **Spearman rank correlations**.  
- **Lyrical Similarity:** using **DistilBERT embeddings** and **FAISS** approximate nearest neighbour search.

