# 🎧 Llama-2 Customer Support Fine-Tuning

## 🎯 Use Case

This model is trained for the following use case prompt:

> **"A model that takes in a raw customer support ticket in English and responds with a concise, empathetic resolution summary categorized by issue type and urgency level."**

The model automatically:
- Reads a raw customer support ticket written in plain English
- Identifies the **issue type** (Billing, Technical, Account, Delivery, General Inquiry)
- Assigns an **urgency level** (Low, Medium, High)
- Generates a **concise, empathetic resolution summary** with clear next steps

---

A full LLM fine-tuning pipeline that trains **Llama-2-7B** using **QLoRA** (4-bit quantization + LoRA adapters) on synthetic customer support data generated with GPT-4.

---

## 📋 Example

**Input (Customer Ticket):**
I was charged twice for my subscription this month and I still can't log
in to my account. This is absolutely unacceptable — I need this fixed
immediately or I'm cancelling.

**Output (Resolution Summary):**
Issue Type: Billing
Urgency Level: High
Resolution Summary: We sincerely apologize for the inconvenience caused
by the duplicate charge and login issue. We will immediately initiate a
refund for the extra charge and escalate your account access issue to
our technical team. You can expect a resolution within 24 hours, and we
will follow up via email once both issues are resolved.


---

## 🏗️ Pipeline Overview

| Step | Description |
|------|-------------|
| Data Generation | Synthetic customer support tickets generated using GPT-4 |
| Preprocessing | Parse and split into train/test sets |
| Training | Fine-tune Llama-2-7B with QLoRA on a T4 GPU |
| Evaluation | Run inference on held-out test tickets |
| Inference | Generate structured resolution summaries |
| Merge & Save | Merge LoRA weights into base model and save to Google Drive |

---

## 📦 Issue Types & Urgency Levels

The model classifies every ticket into one of the following:

**Issue Types:**
- Billing
- Technical
- Account
- Delivery
- General Inquiry

**Urgency Levels:**
- Low
- Medium
- High

---

## ⚙️ How to Run

### 1. Prerequisites
- Google Colab with GPU runtime (T4 or better)
- OpenAI API key (for synthetic data generation)

### 2. Add your API keys
- Replace `"API KEY HERE"` in the data generation cell

### 3. Run all cells in order
The notebook is self-contained and will:
- Generate synthetic training data via GPT-4
- Fine-tune Llama-2-7B with QLoRA
- Save the merged model to your Google Drive
