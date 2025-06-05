## Translator for Russian-Tatar language pair


This project focuses on fine-tuning NLLB200 600M model for Russian ↔ Tatar translation.

**Project Structure**

1. **Data preprocessing /Data **[data]
   - Files: [data/Data_cleaning.ipynb]
   - Purpose: To preprocess data for better training quality

2. **Data**
	- Files: [data/tat_ru_300k_cleaned_parallel_corpus.xlsx]
	- Purpose: Preprocessed data via [Data_cleaning.ipynb] for training

3. **Model Training **
   - Files: [Fine_tuning_NLLB200_600.ipynb]
   - Purpose: To fine-tune NLLB200 600M for russian↔tatar translation
   
4. **Metrics Evaluation (metrics)**
   - Files: [Translation_testing.ipynb]
   - Purpose: To evaluate the performance of the model using sacreBLEU and chrF++ metrics

---
**Dataset**

We compiled a Russian-Tatar parallel corpus from multiple sources, initially comprising 402,188 sentence pairs. After preprocessing, the dataset was reduced to 311,289 pairs. The test set includes 2,009 sentence pairs from FLORES-200 dataset.

---
**Model**

**NLLB-200-distilled-600M**: Selected model was trained on over than 200 languages, a large number of which are Turkic languages, including Tatar

---
**Results**

Evaluation on the FLORES-2000 benchmark revealed that, for the Russian→Tatar (RU→TT) direction, our approach yielded a sacreBLEU improvement of +1.349 points relative to the baseline, whereas the chrF++ score declined by −0.829 points. In the reverse (Tatar→Russian) direction, both sacreBLEU and chrF++ metrics indicated a net degradation in translation quality compared to the baseline system. Although precise interpretation of these mixed results remains elusive, we hypothesize that a substantial mismatch between the training and evaluation corpora—particularly regarding sentence-length distributions and contextual complexity—has hindered consistent gains across both metrics and language pairs. Specifically, the FLORES-2000 test set comprises a higher proportion of longer, syntactically complex sentences than our cleaned training data, which was heavily filtered to exclude sentences over 25 words and non-Tatar content. Consequently, while the model may have learned to translate shorter, more homogeneous sentences effectively (reflected in the sacreBLEU gain for RU→TT), it may have underperformed on longer, multi-clausal structures, leading to the observed drop in chrF++.

---
**Conclusion**

In this study, we assembled and preprocessed a parallel Russian-Tatar corpus, and leveraged it to fine-tune a modified NLLB-200 600M model. Looking ahead, we intend to undertake several enhancements aimed at reducing domain-shift and improving overall translation fidelity

**References**

Refer to the project documentation for a detailed list of references and further reading on the techniques used.
