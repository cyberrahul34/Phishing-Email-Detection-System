
# Phishing Email Detection System (AI-Based)

A beginner-friendly cybersecurity project that detects phishing emails with a **Regex + Machine Learning hybrid** and gives a **0-100 risk score** with reasons.

## Features
- Detects urgency / "verify account" wording
- Flags IP-based links, risky domains (.ru .cn .tk .xyz .top), fake brand domains and URL shorteners
- TF-IDF + Logistic Regression classifier (trains automatically)
- Weighted regex rules work as a fallback
- Report with reasons, scores and verdict: SAFE / SUSPICIOUS / PHISHING

## Install
```bash
pip install -r requirements.txt
```

## Run
```bash
python phishing_hybrid.py
```
It runs sample tests, then asks you to paste an email text (type `q` to quit).

## Use your own dataset (optional)
Put `dataset.csv` in the same folder with columns `text` and `label` (1 = phishing, 0 = safe).

## Example output
```
Email   : Click here to verify your PayPal account http://abc.tk
  ⚠ Link uses a suspicious domain (+30)
  ⚠ Asks to verify/update account details (+30)
  ⚠ Pushy call-to-action (+20)
Regex score: 80/100 | ML score: 62/100
Result  : PHISHING (High Risk) - risk score 73/100
```

## Limitations
The built-in training set is tiny (24 demo emails), so the ML score is rough. Only email text is analysed (no headers, attachments or live blacklists). Use for learning and defence only.

## Roadmap
Train on a real dataset, parse `.eml` headers (SPF/DKIM/DMARC), URL blacklist checks, Streamlit dashboard, Gmail/Outlook integration.

## Docs
Full report and slides are in `docs/`.
