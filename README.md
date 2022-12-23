# **ECE GY 7123 Deep Learning**

## Final Project
## **COMPORT**: a Confidence-score Mechanism for Post-processing OCR-ed Tibetan-manuscripts


### Student Name:


*   Xiaoyu Wang
*   Yiren Dai

### Institute: 
*   ECE Department, Tandon School of Engineering, NYU

### GitHub Codebase Directory Summary:

- **best_model**: we saved the best test accuracy model file in this folder
- **data**: we uploaded the RAW data and tokenizer data in this folder
- **project_codebase**:
  - Jupyter_Notebook_Version: Jupyter Notebook Version execution code
    - confidence_score_mechanism_transformer: The Confidence Score Mechanism Transformer model we implemented for this project
    - original_transformer: The Original Transformer which we used as comparison model.
  - Python_Version: Python Version execution code
    - confidence_score_mechanism_transformer: The Confidence Score Mechanism Transformer model we implemented for this project
    - original_transformer: The Original Transformer which we used as comparison model.
- **visualization**: we saved the best test accuracy model's:
  - Heat Map
  - Word Cloud

### Abstract of this project:

Scholars in the humanities rely heavily on ancient manuscripts to study history, religion, and socio-political structures in the past. Many efforts have been devoted to digitizing these precious manuscripts using OCR technology, but most manuscripts were blemished over the centuries so that an Optical Character Recognition (OCR) program cannot be expected to capture faded graphs and stains on pages. We present a neural spelling correction model built on Google OCR-ed Tibetan Manuscripts to auto-correct OCR-ed noisy output. Our project is divided into four sections: dataset, model architecture, training and analysis. First, we feature-engineered our raw Tibetan etext corpus into two sets of structured data frames -- a set of paired toy data and a set of paired real data. Then, we implemented a Confidence Score mechanism into the Transformer architecture to perform spelling correction tasks. According to the Loss, BLEU score and Character Error Rate, our Transformer + Confidence Score model proves to be superior to Transformer, LSTM-2-LSTM and GRU-2-GRU architectures. Finally, to examine the robustness of our model, we analyzed erroneous tokens, visualized Attention and Self-Attention heatmaps, and explored important neurons in our model.

### Introduction of this project:
Problem description: For scholars in the humanities, recognizing words in ancient manuscripts is an essential but time-consuming task. In recent years, Optical Character Recognition (OCR) technology has extensively promoted the digitization process of ancient characters. However, many spelling errors exist in digitized electronic text corpora; therefore, it is unreliable to use these materials for research. Moreover, some handwritten Tibetan texts, such as "པ" and "བ", "ད" and "ང", are hard to distinguish even for the naked eyes, not to mention about OCR program. Scholars rely on domain knowledge and the context to identify correct spellings. 
Current popular spell-correcting systems cannot correct Tibetan text or auto-correct OCR-ed output. The OCR output contains the confidence score for each character. 
Typically characters with a confidence score above 80% have an overall accuracy of close to 100% based on human validation, while characters with a low confidence score (e.g. 30%) require manual review. Recent NLP development in Transformer architecture (Vaswani et al., 2017), which consists of a multi-head self-attention mechanism stacked with an encoder/decoder structure, has proven to be adept at correcting errors in English text and performing context-based grammar error correction based on incorrect characters/words (Junczys-Dowmunt et al., 2018; Lichtarge et al., 2018; Zhao et al., 2019). Inspired by this idea, we add additional confidence scoring mechanisms to the standard Transformer architecture to  improve the performance of Transformer and recognition accuracy. Via the Confidence Score mechanism, the model can take use of the noisy OCR -ed sentences and the confidence score of each token in the encoder and output the correct sentences in the decoder. The initial error rate of paired training data was 25%, and our best model reduced it to 12.26%. Moreover, our model can also be applied to all languages with post-processing and auto-correcting OCR texts.

### Literature Survey of this project:
Although recent advances have been demonstrated successful for real-world language tasks, there are few attempts to apply them to Tibetan studies. Deep seq2seq architectures, such as Transformer, have significantly optimized translation tasks. Transformer is primarily driven by an attention mechanism with stack encoders and decoders. Each component contains multiple self-attention layers, followed by a position feedforward layer, a normalization layer, and other residual connections. The decoder block is concerned and connected to the encoder output through these self-attentional and feedforward layers. These complex attention mechanisms show rich language comprehension abilities in contrast to the more complicated RNNs or CNNs on English-to-German and English-to-French translation (Vaswani et al., 2017).
Many recent neural Grammatical Error Correction  (GEC) models have been trained on the same type of Transformer architecture (Junczys-Dowmunt et al., 2018; Lichtarge et al., 2018; Zhao et al., 2019). Correcting spelling errors in the OCR Tibetan corpus is similar to the GEC task. Previous GEC systems (Choe et al., 2019) were trained on synthetic data in which real noise functions were used to generate erroneous corpora. Low-quality machine translation and data deficiency were treated by randomly inserting/replacing/removing markers or swapping adjacent words with a uniform distribution. These noise functions could replicate real-world conditions; then the corpus was used to train the Transformer architecture. Inspired by this, we propose a similar methodology to enhance the Tibet dataset. In addition, previous work (Zhao et al. 2019) has implemented a copy mechanism into the Transformer architecture for GEC tasks, showing that approximately 80% to 97% of tokens are copied directly from the source sentence. Similar to Attention, this Copy mechanism allows the model to recognize which word should be copied in the decoder when correcting the sentence. In our task of correcting errors in the OCR-ed Tibetan corpus, the OCR system outputs a confidence score for each character. It is unnecessary to incorporate this copy mechanism since we already have a confidence score representing a given character's trustworthiness. Finally, a compression algorithm (Sennrich et al., 2016) was adapted from byte-pair encoding (BPE) to perform word segmentation, which allows for fixed-size vocabularies of variable-length character sequences. Sennrich et al. introduced this subword unit segmentation method. It endows the model the flexibility to change word subunits and is therefore particularly useful for implementing the GEC task model.

### Technical Details
Please check the report for details

### Training and Hyperparameter Selection details
Please check the report for details

### Results Summary
Overall, our Transformer + Confidence Score architecture outperforms the rest of the architectures. Compared to the Transformer architecture, our model improved the BLEU score by 5.242%, the Loss by 23.26% and CER by 30.66%. More importantly, these results suggest that Transformer + Confidence Score can attain both a broad and deep understanding of the Tibetan language. As a corpus-based metric, a BLEU score of 83.72 shows that the model can achieve a wide understanding of the language breadth while a CER of 0.1226 also suggests an in-depth ability to understand and predict individual words and phrases. Compared to LSTM-2-LSTM or GRU-2-GRU, which both suffer from a significantly lower BLEU to CER ratio, the Transformer + Confidence Score not only boosts performance across all three categories of interest but also exhibits a more well-rounded, complete understanding of Tibetan semantics and vocabulary.

### Result Analysis and Discussion
Having demonstrated the efficacy of the Transformer + Confidence Score model, we conduct an in-depth analysis of key sub-modules within the model architecture to better understand its strengths and weaknesses. In evaluating the model, we specifically analyzed erroneous tokens to identify the strengths and weaknesses of the model’s learned representations, visualized Attention and Self-Attention heatmaps within the Transformer, and explored important neurons in our model. 

### Conclusion of this project:
In conclusion, we originally intended to implement a Transformer + Confidence Score model to correct OCR-ed Tibetan manuscript. Our results show that Transformer + Confidence Score outperformed LSTM-2-LSTM, GRU-2-GRU. And compared to the vanilla Transformer architecture, our Transformer + Confidence Score model increased the BLEU score by 5.242% and reduced the Loss and CER by 23.26% and 30.66% respectively. The model is robust in correcting spelling errors in Tibetan OCR-ed texts, but it suffers short-sightedness that it cannot correct words based on word context. Possible solutions include: 1) increase the BPE tokenizer vocab size to 2000 - 3000 like a general English Transformer model and increase training data to allow the model capturing latent semantic relationships, and 2) train a Tibetan BERT model and connect it to the end of this model’s outputs to edit semantically inconsistent and ambiguous words. 
    We accomplished the goal of significantly reducing the number of human laborers and material costs to transcribe ancient Tibetan texts and benefit the scholars in the field. Ultimately, this project paves the way for linguistics research as a promising methodology for building transcribed text corpuses across other ancient languages. 
