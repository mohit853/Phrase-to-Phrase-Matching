# Kaggle - USPTO Patent Phrase Matching  

## 📝 Description  
This competition focuses on **semantic similarity** within patent documents.  
The U.S. Patent and Trademark Office (USPTO) provides a large-scale dataset of phrase pairs derived from patents.  
The goal is to build models that determine how closely two phrases match in meaning within their **technical domain (CPC classification)**.  

Accurate similarity matching is critical in patent search and examination, where detecting synonyms, paraphrases, or related terms can help identify prior inventions.  

**Example:**  
- *"television set"* vs. *"TV set"* → Similar (**1.0**)  
- *"strong material"* vs. *"steel"* → Similar in some domains, not others.  

---

## 📂 Dataset  
- **train.csv** – Phrase pairs (anchor, target, CPC context, similarity score)  
- **test.csv** – Phrase pairs without scores (for evaluation)  
- **sample_submission.csv** – Example submission format  

**Columns:**  
- `id`: Unique pair identifier  
- `anchor`: First phrase  
- `target`: Second phrase  
- `context`: CPC code (technical domain)  
- `score`: Similarity score (0.0–1.0, in increments of 0.25)  

**Score interpretation:**  
- **1.0** – Exact or near-exact match (plural/singular, stopwords, etc.)  
- **0.75** – Close synonym/abbreviation  
- **0.5** – Related but not identical (broader/narrower terms)  
- **0.25** – Same domain, weak relation (including antonyms)  
- **0.0** – Unrelated  

---

## ⚙️ Evaluation  
Submissions are evaluated using the **Pearson correlation coefficient** between predicted and true similarity scores.  

**Submission format:**  
```csv
id,score  
4112d61851461f60,0  
09e418c93a776564,0.25  
36baf228038e314b,1  
