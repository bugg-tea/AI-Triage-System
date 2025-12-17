# 🏥 AI Medical Triage System

A lightweight, **medical triage assistant** designed to process patient symptoms from **text, audio, or video** inputs.  
It performs **symptom extraction, urgency scoring, guideline retrieval, escalation decision-making**, and supports **feedback-driven dynamic learning**.  

This system is suitable for research, demonstration, or prototype medical triage workflows in resource-constrained environments.
(NOTE :- given app.py code file is actually a google collab file downloaded in .py form)

---

**Example:-**

Input:

Text: "Patient reports dyspnea and severe chest pain"

Age: Adult

Gender: M

Output:

CLEAN TEXT: patient reports dyspnea and severe chest pain
SYMPTOMS: ['breath', 'pain']
URGENCY: High
GUIDELINES: ['WHO – IITT: Respiratory distress guidance', 'Ensure airway patency and oxygen monitoring', 'WHO – Pain Management Guidelines', 'Consider analgesics based on severity']
ESCALATION: Immediate Doctor Referral

Feedback Summary:
{'Correct': 1}

Current Symptom Weights:
{'breath': 3, 'pain': 3, 'fever': 2, 'vomit': 2, 'cough': 2, 'headache': 1}


---

## 🚀 Features

1. **Multi-modal Input**  
   - Accepts **text**, **audio**, and **video** inputs.  
   - Supports **any single input, combination of two, or all three** simultaneously.

2. **Speech-to-Text**  
   - Uses **OpenAI Whisper (small model)** for accurate audio/video transcription.  
   - CPU-optimized for local execution.

3. **Text Cleaning & Preprocessing**  
   - Removes special characters, excessive whitespace, and normalizes text.  

4. **Symptom Extraction (Rule + NER)**  
   - Rule-based + biomedical NER using `d4data/biomedical-ner-all`.  
   - Extracts **canonical medical symptoms** (breath, pain, fever, vomit, cough, headache).  

5. **Urgency Scoring**  
   - Assigns **Low, Medium, High** urgency based on symptoms, age group, and dynamic weights.  
   - High-risk symptoms (e.g., breathing difficulty, severe pain) automatically escalate urgency.  

6. **Guideline Retrieval**  
   - Retrieves relevant **WHO medical guidelines** for detected symptoms.  
   - Context-aware: adjusts for **age, urgency, and patient condition**.  

7. **Escalation Agent**  
   - Provides **escalation recommendations**: Immediate Doctor Referral, Doctor Soon, Regular Monitoring.  
   - Critical symptoms trigger automatic escalation.

8. **Feedback-Driven Learning**  
   - Users can provide **Correct, Incorrect, or Needs Review** feedback.  
   - Feedback updates **symptom weights and urgency rules dynamically**.  
   - Live feedback summary is displayed in the interface.

9. **Explainable Output**  
   - Outputs include detected symptoms, urgency label, guidelines, escalation, and symptom weight adjustments.

10. **CPU-only & Lightweight**  
    - No GPU required; optimized for **fast, stable execution** on laptops and CPUs.

---

---

## 🎛️ Gradio Interface

The project includes a **fully interactive Gradio UI** for real-time testing and feedback.

### 📥 Supported Inputs
- Text input (manual symptom description)
- Audio upload (`.wav`, `.mp3`)
- Video upload (`.mp4`, `.avi`)
- Any **one**, **two**, or **all three** inputs can be provided together

### 📤 Outputs Displayed
- Cleaned & normalized text
- Extracted canonical symptoms
- Urgency score and label
- Relevant WHO guideline snippets
- Escalation recommendation
- Live feedback summary
- Current dynamic symptom weights

### 📝 Feedback & Learning
After reviewing the output, users can select:
- **Correct**
- **Incorrect**
- **Needs Review**

This feedback is:
- Logged to `feedback_log.csv`
- Used to dynamically adjust symptom weights
- Reflected immediately in the **Feedback Summary** panel

---



