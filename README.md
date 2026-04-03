# 🚗 AutoSLA

LLM‑powered **Car Contract Analysis & VIN Verification System** built using **Streamlit, OCR, Gemini AI, and NHTSA VIN API**.

AutoSLA extracts text from vehicle lease/loan contracts, analyzes financial & risk details using AI, and verifies VIN data with official government records.

---

## 🌐 Live Demo

**[https://autosla.streamlit.app](https://autosla.streamlit.app)**

---

# ✨ Features

* 📄 **OCR Extraction** from PDF and image contracts
* 🤖 **AI Contract Analysis** using Gemini 2.5 Flash
* 🚗 **VIN Decoding & Verification** via NHTSA API
* ⚠️ **Red‑Flag Detection** for hidden fees & risks
* 📊 **Clean Streamlit Dashboard UI**

---

# 🛠 Tech Stack

* **Frontend/UI:** Streamlit
* **OCR:** pdfplumber, pytesseract, Pillow
* **LLM:** Google Gemini API 
* **VIN Validation:** NHTSA VPIC API
* **Language:** Python 

---

# 📂 Project Structure

```
AutoSLA/
├── app.py                
├── requirements.txt     
├── .env                  
├── README.md             
└── modules/
    ├── ai_analyzer.py
    ├── chatbot.py
    ├── ocr_engine.py
    ├── price_engine.py
    └── vin_lookup.py

```

---

# ⚙️ Installation & Setup

## Install dependencies

If **requirements.txt** already exists:

```
pip install -r requirements.txt
```

## Install Tesseract OCR (IMPORTANT)

Download from:

👉 [https://github.com/tesseract-ocr/tesseract](https://github.com/tesseract-ocr/tesseract)

After installation, update the path inside **app.py** if needed:

```python
pytesseract.pytesseract.tesseract_cmd = r"C:\Program Files\Tesseract-OCR\tesseract.exe"
```

## Add Gemini API Key

Create a **.env** file in the project root:

```
GEMINI_API_KEY=your_api_key_here
```

Get API key from:

👉 [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)

---

# ▶️ Run the Application

```
streamlit run app.py
```

Then open the browser link shown in terminal (usually **http://localhost:8501**).

---

# How It Works

### Step 1 — Upload Contract

User uploads **PDF or image** containing vehicle lease/loan details.

### Step 2 — OCR Processing

* PDFs → extracted using **pdfplumber**
* Images → extracted using **pytesseract OCR**

### Step 3 — AI Contract Analysis

Gemini extracts:

* Brand, model, year, VIN
* Monthly payment, APR, lease term, upfront cost
* Mileage limits
* Hidden risks / red flags

### Step 4 — VIN Verification

VIN is validated using:

**NHTSA VPIC API** → returns official manufacturer data, vehicle specifications, and recall information.

### Step 5 — Price & Fairness Evaluation

The **price_engine.py** module estimates whether the deal is fair by:

* Calculating **estimated market value** based on brand, model year, and depreciation
* Computing **total contract cost** from monthly payment, lease term, and upfront amount
* Applying penalties for:

  * High price compared to market value
  * High or missing APR
  * Detected legal or financial red flags

This produces a **Fairness Score (0–100)** shown in the dashboard to help users quickly judge if the contract is:

* ✅ Competitive
* ⚠️ Average
* 🚨 High‑risk or overpriced

## N/A values in output

**Possible reasons:**

* OCR text not readable
* Wrong/invalid VIN
* Gemini API key missing
* JSON parsing failure

**Fix:**

* Use clear contract PDF
* Check `.env` API key
* Ensure internet connection

# 🚀 Future Improvements

* Multi‑language contract support
* Risk scoring system
* PDF report generation
* Blockchain‑based contract verification
* Mobile app version

---
# Screenshots

<img width="1919" height="659" alt="Screenshot 2026-02-21 220144" src="https://github.com/user-attachments/assets/d26ffd8b-2fbe-4f7d-9918-2703c7722922" />
<img width="1916" height="684" alt="Screenshot 2026-02-21 220307" src="https://github.com/user-attachments/assets/965b3283-7c5b-45b3-948e-dca3bdfcb92a" />
<img width="1919" height="671" alt="Screenshot 2026-02-21 220434" src="https://github.com/user-attachments/assets/15c0108b-2d7a-4c9e-b0b6-c683f81ebd01" />
<img width="1919" height="661" alt="Screenshot 2026-02-21 220500" src="https://github.com/user-attachments/assets/8f76cf36-d1c7-4604-8b55-e0e9130dbcab" />
<img width="1919" height="704" alt="Screenshot 2026-02-21 220709" src="https://github.com/user-attachments/assets/20b74e62-55c2-4342-a31c-923983cd0fbe" />

---

**AutoSLA — Making car contracts transparent using AI.** 🚗✨
