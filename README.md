# 🤖 AI-Powered Customer Review Insights Pipeline

An automated N8N-based no-code Generative AI workflow that analyzes customer product reviews using LLMs (GPT-4 / Mistral), generates structured insights, logs results to Google Sheets, and sends alerts for negative feedback.
---

## 📌 Project Overview

This project automates the analysis of customer reviews for products such as **XSound Pro Headphones** (or any product).

Instead of manually reviewing hundreds of customer reviews, this workflow:

- Generates concise AI-powered summaries
- Performs sentiment analysis (Positive / Negative / Neutral)
- Classifies summary tone (Informative / Persuasive / Friendly)
- Calculates confidence scores
- Logs structured insights into Google Sheets
- Sends email alerts for negative reviews

---

## 🎯 Problem Statement

Manual review analysis is:
- Time-consuming  
- Inconsistent  
- Prone to bias  
- Difficult to scale  

This workflow solves the problem by:

✅ Reducing processing time from hours to minutes  
✅ Ensuring consistent AI-based sentiment detection  
✅ Providing structured insights for Sales, Marketing, and Product teams  
✅ Triggering instant alerts for negative customer feedback  

---

## 🛠️ Tech Stack

- N8N Cloud – Workflow Automation
- OpenAI GPT-4 / GPT-4o-mini or Mistral Small
- Google Sheets API
- Gmail Integration
- LLM Basic Chain Nodes

---

## 🔄 Workflow Architecture

On Form Submission  
        ↓  
Summarization (LLM)  
        ↓  
Sentiment Analysis (LLM)  
        ↓  
Summary Tone Classification (LLM)  
        ↓  
Google Sheets Logging  
        ↓  
IF (Negative Sentiment?)  
        ↓  
Gmail Notification (if TRUE)

---

## ⚙️ Step-by-Step Workflow Implementation

### 1️⃣ On Form Submission Node

Fields:
- Product Name (Text)
- Product Review (Text Area)

---

### 2️⃣ Summarization Node (LLM Chain)

**Prompt Objective:**  
Generate a concise summary of the customer review.

**Output Format:**
```
<Summary text only>
```

---

### 3️⃣ Sentiment Analysis Node (LLM Chain)

**Prompt Objective:**  
Analyze sentiment of the original review.

**Output Format:**
```
Sentiment: <Positive/Negative/Neutral> | Score: <0 to 1>
```

Example:
```
Sentiment: Negative | Score: 0.87
```

---

### 4️⃣ Summary Tone Classification Node (LLM Chain)

**Prompt Objective:**  
Classify tone of the generated summary.

**Output Format:**
```
Tone: <Informative/Persuasive/Friendly> | Score: <0 to 1>
```

Example:
```
Tone: Informative | Score: 0.91
```

---

### 5️⃣ Google Sheets Node

Create a Google Sheet with columns:

| Product Name | Product Review | Product Review Summary | Sentiment and Score | Tone and Score |

Map outputs from previous nodes into respective columns.

---

### 6️⃣ IF Node – Negative Check

Condition:
```
If Sentiment = Negative
```

If TRUE → Trigger Gmail node  
If FALSE → End workflow  

---

### 7️⃣ Gmail Node – Alert System

**Subject:**
```
Negative Customer Review Received – <Product Name>
```

**Message:**
```
Dear Team Lead,

We have received a negative customer review for the product - <Product Name>.

Please find the feedback summary below:
<Product Review Summary>

Best Regards,
Workflow Automation Team
```

---

## 🚀 How to Run the Project

1. Sign up at https://n8n.io  
2. Create a new workflow  
3. Configure:
   - OpenAI / Mistral credentials  
   - Google Sheets credentials  
   - Gmail credentials  
4. Activate the workflow  
5. Use Production URL to submit test reviews  
6. Verify:
   - Data added in Google Sheet  
   - Email triggered for negative sentiment  

---

## 📊 Example

**Input Review:**
> The sound quality is average and the battery drains quickly. Not worth the price.

**Generated Output:**

Summary:
```
Customer found the sound quality average and expressed dissatisfaction with poor battery life.
```

Sentiment:
```
Negative | Score: 0.89
```

Tone:
```
Informative | Score: 0.93
```

Email Alert: Triggered

---

## 📂 Repository Structure

```
/workflow-export.json
/README.md
/screenshots/
/sample-output/
```

---

## 🔮 Future Enhancements

- Dashboard integration (Power BI / Looker Studio)
- Slack / Teams notifications
- Trend visualization charts
- Topic modeling
- Multilingual support

---

## 📜 License

Developed as part of Module 2 Mini Project – GenAI Automation Workflow (Educational Purpose).
Workflow Screenshot:
