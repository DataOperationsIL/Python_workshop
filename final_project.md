# 📦 Final Project: Labeling Pipeline Simulation

Hi and welcome to your final project!  
This assignment is based on a fictional—but realistic—data labeling workflow, designed to give you hands-on experience with the core skills you've learned in this workshop. You’ll use **Python, SQL, and an LLM (Large Language Model)** to simulate a labeling pipeline for an e-commerce dataset.  

This project emphasizes real-world thinking, data operations, and code functionality over "perfect answers."

---

## 🧠 What You'll Practice
By the end of this project, you’ll have experience in:

- 🔌 Connecting to an SQL database using Python  
- 📊 Querying and processing real data  
- 📤 Exporting data for annotation  
- ⚠️ Identifying quality issues in labeled data  
- 📄 Writing simple reports using Python  
- 🤖 Using an LLM to auto-label reviews  

---

## 🧩 Your Tasks
Break your work into 4 main steps. Each step should be a Python script/Jupyter notebook, which you should be able to explain:

1. Select rows for labeling  
2. Create a report  
3. Identify quality issues  
4. Auto-label 2 features  

---

## 🛒 Scenario: Cellphones & Customer Reviews
You are working as part of a data operations team at a fictional e-commerce site that sells cellphones. You have access to a database ([database schema](https://github.com/DataOperationsIL/Python_workshop/blob/main/database_scheme.md)  ):

- `products`: cellphone catalog data 
- `transactions`: purchases of those phones  
- `reviews`: customer-written reviews of those products  

Your team includes offshore labelers in India who label each review based on unknown guidelines... and the quality is all over the place.  

Here’s the current labeling schema (per review):

- Brand mentioned: Yes/No  
- Model mentioned: Yes/No  
- Color mentioned: Yes/No  
- Sentiment: Positive/Negative  
- Sentiment is intense: Yes/No/Unclear  
- Price mentioned: Yes/No  
- Competitor mentioned: Yes/No  
- Battery life mentioned: Yes/No  
- Toxic language present: Yes/No  
- Review sounds fake: Yes/No  
- Dangerous content present: Yes/No  

We won’t go into how each label should be defined—assume the labelers had vague instructions and made mistakes. Your job is to work with what you have.

---

## 🧩 Your Tasks – Detailed Instructions

### 1. Select Reviews for Labeling
Write a Python script that:
- Connects to the provided SQL database  
- Selects 150 reviews that:
  - Have not already been labeled or sent for labeling  
  - Are potentially important to label first (you decide the business logic: e.g., popular products, recent purchases, high value, etc.)  
- Exports the selected reviews to a CSV file in the following format and send to Danielle:

| product_id | review | brand | model | color | brand_mentioned | model_mentioned | color_mentioned | sentiment | sentiment_intensity | price_mentioned | competitor_mentioned | battery_life_mentioned | toxic_language | fake_sounding | dangerous_content | review_id |
|------------|--------|-------|-------|-------|-----------------|-----------------|-----------------|-----------|----------------------|----------------|----------------------|------------------------|----------------|---------------|------------------|-----------|

*(Leave the labeling columns empty.)*  

- Add your selected reviews to the `sent_to_labeling` table via SQL.  

---

### 2. Create a General Data Report
The goal of this task is to explore and describe the data you’re working with.  

Write a Python script or Jupyter notebook that connects to the SQL database, loads the data, and generates a general report which includes:

#### 🧾 Data Overview
- Total number of reviews, products, and transactions  
- Time range of the data (earliest/latest review or transaction date)  
- Number of reviews per product (top 10 products by review count)  
- Number of transactions per product (top 10 products by sales)  
- Anything else that looks interesting  

#### 📊 Visualizations
Include at least 3 of the following (you can do more if you want):  
- Bar chart of review count per brand  
- Bar chart of average transaction amount per product  
- Pie chart of sentiment distribution (if labels exist)  
- Line plot showing review or transaction volume over time  
- Histogram of review lengths (in characters or words)  

#### 💾 Output
- Generate an **HTML report** summarizing your findings.  
- Include tables, graphs, and written observations.  

Libraries you may use:  
`pandas`, `matplotlib`, `seaborn`, `plotly`  
Optional: `pandas-profiling` / `ydata-profiling`

---

### 3. Identify Row-Level Quality Issues in Labeled Data
In this task, you'll investigate the labeled review data for potential quality issues — mistakes or inconsistencies that may have resulted from using an LLM or poor labeling guidelines.  

Your goal is to write a Python script that:
- Loads the labeled reviews table from the SQL database  
- Applies logic to detect issues at the individual row level  
- Outputs a CSV file containing:
  - The original labeled data for problematic rows  
  - One or more new columns describing the specific issue(s) identified  

#### 🧪 Examples of Quality Checks
- **Contradictions**  
  - `sentiment == 'positive' AND toxic_language == 'yes'`  
  - Review is only 3 words long but has 10 detailed labels marked "yes"  

- **Suspicious Uniformity**  
  - All labels marked "yes" or all marked "no"  
  - Label combinations that repeat too frequently  

- **Content/Label Mismatch**  
  - `price_mentioned == 'yes'` but no number or currency symbol appears in the text  
  - `battery_life_mentioned == 'yes'` but no related words (battery, charge, hours) in text  

- **Ambiguous Language**  
  - `sentiment_intensity == 'unclear'` but sentiment is clearly positive or negative  
  - `dangerous_content == 'yes'` but no strong language in the review  

#### 🧾 Output Format
The final CSV should contain:  
- Original data  
- A column for detected quality issues  
- If multiple issues for the same row → either multiple columns or a concatenated string  

---

### 🤖 4. Auto-Label Brand and Sentiment Using Ollama + Full Evaluation
In this task, you’ll:
- Use an **LLM via Ollama** to label two fields in product reviews  
- Compare predictions against ground truth labels (golden set)  
- Evaluate performance using standard classification metrics  

#### 🎯 Labels to Predict
- `brand_mentioned`: yes / no  
- `sentiment`: positive / negative  

#### 📥 Input
Ground Truth File  

#### 🛠 Your Script Should:
- Load the file using `pandas`  
- For each row:
  - Send `review_text` to an LLM via `ollama.chat()`  
  - Use a structured prompt and parse the JSON response  
  - Extract predicted values for `brand_mentioned` and `sentiment`  
- Add two new columns:
  - `brand_mentioned (LLM)`  
  - `sentiment (LLM)`  
- Save the full output to CSV:  
  `llm_label_comparison.csv`

#### 📊 Evaluation Metrics
After collecting predictions:

1. ✅ Normalize labels  
   - Lowercase, trimmed, no punctuation  

2. 📈 For each field (`brand_mentioned`, `sentiment`):  
   - Confusion Matrix  
   - Precision  
   - Recall  
   - F1 Score  
   - Accuracy  

Use `classification_report()` from `sklearn.metrics` for a clean output.  

#### 💾 Final Output
- `llm_label_comparison.csv` – includes original data, LLM predictions, ground truth, and confusion matrix values  
- `evaluation_report.html` *(optional)* – a clear report file with metrics and visualizations  

---
