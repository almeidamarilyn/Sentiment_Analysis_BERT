# Sentiment_Analysis_BERT

A lightweight repo for fine-tuning a BERT model for sentiment analysis and running quick inferences. Built around a single Python script: `sentiment_analysis_using_bert_model.py`.

---

## 📖 Project Overview  

This project demonstrates how to build a **sentiment analysis model** using **BERT (Bidirectional Encoder Representations from Transformers)**.  

- The script fine-tunes a pre-trained BERT model on a labeled dataset (text + sentiment labels).  
- It supports **training, evaluation, and inference** from the command line.  
- Training data typically consists of sentences/reviews labeled as **positive** or **negative**, but the pipeline can be adapted to multi-class sentiment tasks.  
- Once trained, the model can predict the sentiment of any given text input.  

**Why BERT?**  
Unlike traditional models, BERT is pre-trained on massive amounts of text and understands language context bidirectionally (both left and right). This makes it highly effective for NLP tasks like sentiment analysis, where nuance and context matter.  

**Use cases include:**  
- Classifying customer reviews as positive/negative.  
- Monitoring social media for brand sentiment.  
- Automating support ticket prioritization based on tone.  

---

## 🚀 Quick Start

### 1) Clone & set up
```bash
# replace <your-repo> with your GitHub repo URL after you create it
git clone <your-repo>
cd <repo-folder>

# (optional) create a virtual environment
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

pip install --upgrade pip
pip install -r requirements.txt
```
### 2) Add your data
- **Training data format (example CSV):**
  - Column `text`: the sentence or review
  - Column `label`: integer class (e.g., 0=negative, 1=positive)
- Put files in a `data/` folder, e.g.:
  - `data/train.csv`
  - `data/valid.csv`
  - `data/test.csv`


### 3) Train (example)
```bash
python sentiment_analysis_using_bert_model.py \
  --mode train \
  --train_path data/train.csv \
  --valid_path data/valid.csv \
  --model_name bert-base-uncased \
  --epochs 3 \
  --batch_size 16 \
  --lr 2e-5 \
  --output_dir outputs/
```
### 4) Evaluate (example)
```bash
python sentiment_analysis_using_bert_model.py \
  --mode eval \
  --test_path data/test.csv \
  --model_dir outputs/
```

### 5) Inference (example)
```bash
python sentiment_analysis_using_bert_model.py \
  --mode predict \
  --text "I absolutely loved this product!" \
  --model_dir outputs/
```
