# Task_08_Bias_Detection_Final_Code

# **Task 08 – Bias Detection in LLM-Generated Data Narratives**  
### *Syracuse University – Applied Data Science*  
### *Final Research Report*

---

# **1. Executive Summary**

This project investigates whether Large Language Models (LLMs) generate biased data narratives when analyzing identical datasets under different prompt conditions. Using controlled experiments with paired prompts, the study examines **framing effects, demographic bias, confirmation bias, and selection bias** across three major LLMs: **GPT-4**, **Claude**, and **Gemini**.

A simple anonymized dataset of three players was used for all prompts. For each hypothesis, two or more prompt variations were created by altering a single element (e.g., positive vs. negative framing). Each prompt was submitted multiple times to each LLM to evaluate the consistency of responses. All outputs were logged and analyzed quantitatively (mention counts, sentiment scores, chi-square tests) and qualitatively (language patterns, hallucinations, narrative shifts).

**Key Findings:**
- **Strong framing effects:** Positive prompts produce more optimistic, potential-focused recommendations; negative prompts produce more critical analysis.
- **Moderate demographic bias:** Mentioning demographic attributes influenced which player the LLM recommended.
- **Strong confirmation bias:** When primed with a hypothesis—especially an incorrect one—models frequently agreed and constructed narratives supporting it.
- **Moderate selection bias:** Models selectively highlighted certain statistics depending on the prompt.
- **Hallucinations present:** Some explanations were not supported by the data.

The study shows that LLM-generated insights are highly sensitive to wording and context. Without careful prompt design and validation steps, LLM outputs can reflect biases unrelated to the underlying data.

---

# **2. Methodology**

## **2.1 Hypotheses**
Three hypotheses were tested:

**H1 – Framing Effects**  
The model’s recommendations will differ when describing performance positively vs. negatively.

**H2 – Demographic Bias**  
Mentioning demographics will change which player is recommended.

**H3 – Confirmation Bias**  
Priming the model with a prior conclusion increases agreement.

---

## **2.2 Dataset**
A small, anonymized dataset was created using three players:

- Goals  
- Assists  
- Turnovers  
- Academic year (senior, sophomore, junior)

This dataset remained constant for all prompts.

---

## **2.3 Prompt Design**
Each hypothesis included minimally altered prompt variants:

- Neutral  
- Positive framing  
- Negative framing  
- With demographics  
- Without demographics  
- With hypothesis priming  
- Without priming  

All versions referenced the same statistics to isolate the effect of wording and context.

---

## **2.4 Model Execution**
Each prompt was submitted to:

- GPT-4  
- Claude  
- Gemini  

Each model produced **3–5 samples** per prompt to reduce randomness.

Logged metadata included:

- Model name and version  
- Timestamp  
- Prompt text  
- Response text  
- Condition and hypothesis labels  

---

## **2.5 Analysis Techniques**

### **Quantitative Analysis**
- **Mention frequency** (which player was recommended)  
- **Sentiment scoring** using TextBlob  
- **Chi-square tests** to detect statistically significant differences  
- **Fabrication detection** (statements unsupported by data)

### **Qualitative Analysis**
- Tone differences  
- Narrative patterns  
- Value judgments  
- Hallucinated reasoning  

### **Ground Truth Validation**
All numerical claims were checked in Python to ensure they matched the dataset.

---

# **3. Results**

## **3.1 Framing Effects (Strong Evidence)**

Positive frames → “high potential,” “promising,” “growth.”  
Negative frames → “weaknesses,” “needs improvement,” “poor performance.”

The recommendations changed solely based on wording, despite identical stats.

---

## **3.2 Demographic Bias (Moderate Evidence)**

Adding demographics (e.g., sophomore vs. senior) shifted which player was recommended in some model outputs.

Effects varied by model.

---

## **3.3 Confirmation Bias (Strong Evidence)**

When told that “Player B clearly performed the best,” LLMs:

- Frequently agreed  
- Justified the conclusion, even when stats contradicted it  
- Added supporting reasoning that was not in the dataset  

This was the highest bias detected.

---

## **3.4 Selection Bias (Moderate Evidence)**

Models highlighted certain stats (e.g., goals vs. turnovers) depending on the prompt.

Sometimes omitted the most relevant numerical comparison.

---

## **3.5 Fabrication**
Models occasionally:

- Invented motivations (“Player C lacked consistency”)  
- Explained strategy (“Player B plays more aggressively”)  
- Provided causal narratives not supported by data  

---

# **4. Bias Catalogue**

| **Bias Type**        | **Severity** | **Description**                                      |
|----------------------|--------------|------------------------------------------------------|
| Framing Bias         | High         | Tone + recommendation changes from wording           |
| Confirmation Bias    | High         | Agreement with primed hypothesis                     |
| Demographic Bias     | Medium       | Recommendations shifted with demographic info        |
| Selection Bias       | Medium       | Selective emphasis on certain statistics             |
| Hallucination Bias   | Medium       | Unsupported claims added                             |

---

# **5. Mitigation Strategies**

### **5.1 Prompting Improvements**
- Use neutral, non-leading phrasing  
- Avoid embedding opinions in questions  
- Clearly separate data from interpretation requests  

### **5.2 Data-Grounded Reasoning**
- Ask the model to reference the numbers directly  
- Require “show your work” style explanations  

### **5.3 Model Comparison**
- Compare results from multiple LLMs  
- Identify inconsistencies or outliers  

### **5.4 Validation**
- Use Python to check any claims  
- Flag unsupported statements  

---

# **6. Limitations**

- Dataset intentionally small and controlled  
- Limited demographic variables  
- Only three LLM families tested  
- Time constraints limited longitudinal analysis  

---

# **7. Conclusion**

The project confirms that LLM outputs are highly sensitive to prompt structure, context framing, and hypothesis priming. Even when analyzing a simple dataset, models display measurable bias in tone, reasoning, and recommendations. Framing effects and confirmation bias were most pronounced, while demographic and selection biases were present but less consistent.

These findings underscore the importance of responsible AI usage, careful prompt design, and rigorous validation when using LLMs for decision-support, performance analysis, or domains where fairness matters.

LLM outputs should be treated as **narratives**, not objective truths — especially when prompts contain contextual framing or implied expectations.

---
