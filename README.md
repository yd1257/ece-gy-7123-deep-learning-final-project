# **ECE GY 7123 Deep Learning**

## Final Project
## **COMPORT**: a Confidence-score Mechanism for Post-processing OCR-ed Tibetan-manuscripts


### Student Name:


*   Xiaoyu Wang
*   Yiren Dai

### Institute: 
*   ECE Department, Tandon School of Engineering, NYU

### Directory Summary:

- **best_model**: we saved the best test accuracy model file in this folder
- **project_codebase**:
  - Jupyter_Notebook_Version: Jupyter Notebook Version execution code
  - Python_Version: Python Version execution code
- **visualization**: we saved the best test accuracy model's:
  - Heat Map
  - Word Cloud

### Abstract of this project:

Scholars in the humanities rely heavily on ancient manuscripts to study history, religion, and socio-political structures in the past. Many efforts have been devoted to digitizing these precious manuscripts using OCR technology, but most manuscripts were blemished over the centuries so that an Optical Character Recognition (OCR) program cannot be expected to capture faded graphs and stains on pages. We present a neural spelling correction model built on Google OCR-ed Tibetan Manuscripts to auto-correct OCR-ed noisy output. Our project is divided into four sections: dataset, model architecture, training and analysis. First, we feature-engineered our raw Tibetan etext corpus into two sets of structured data frames -- a set of paired toy data and a set of paired real data. Then, we implemented a Confidence Score mechanism into the Transformer architecture to perform spelling correction tasks. According to the Loss, BLEU score and Character Error Rate, our Transformer + Confidence Score model proves to be superior to Transformer, LSTM-2-LSTM and GRU-2-GRU architectures. Finally, to examine the robustness of our model, we analyzed erroneous tokens, visualized Attention and Self-Attention heatmaps, and explored important neurons in our model.

### Conclusion of this project:

In conclusion, we originally intended to implement a Transformer + Confidence Score model to correct OCR-ed Tibetan manuscript. Our results show that Transformer + Confidence Score outperformed LSTM-2-LSTM, GRU-2-GRU. And compared to the vanilla Transformer architecture, our Transformer + Confidence Score model increased the BLEU score by 5.242% and reduced the Loss and CER by 23.26% and 30.66% respectively. The model is robust in correcting spelling errors in Tibetan OCR-ed texts, but it suffers short-sightedness that it cannot correct words based on word context. Possible solutions include: 1) increase the BPE tokenizer vocab size to 2000 - 3000 like a general English Transformer model and increase training data to allow the model capturing latent semantic relationships, and 2) train a Tibetan BERT model and connect it to the end of this model’s outputs to edit semantically inconsistent and ambiguous words. 
    We accomplished the goal of significantly reducing the number of human laborers and material costs to transcribe ancient Tibetan texts and benefit the scholars in the field. Ultimately, this project paves the way for linguistics research as a promising methodology for building transcribed text corpuses across other ancient languages. 
