# PhishGuard AI — AI-Powered Phishing Email Analyzer

A portfolio-style cybersecurity project built with Python and Streamlit. It combines transparent local text heuristics, a simple illustrative risk score, and an optional AI-generated explanation to help learners investigate possible phishing indicators.

## Deliverables

- **Working email-analysis interface:** paste an email or load a built-in synthetic sample.
- **Sample ingestion and demonstration:** suspicious account alert, routine meeting note, and invoice-pressure samples.
- **Detection results:** local indicators, supporting text evidence, extracted URL strings, and a 0–100 heuristic score with a risk band.
- **Investigation dashboard:** session-only summary of analyses, risk bands, evidence counts, and extracted URLs.
- **Downloadable incident reports:** TXT and JSON exports for each latest investigation.
- **Technical documentation:** project report, architecture diagram, and functional test cases.

## Technology stack

Python · Streamlit · OpenAI Python SDK / Responses API · Regular expressions · python-dotenv

## Run locally (Windows PowerShell)

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
Copy-Item .env.example .env
notepad .env
streamlit run app.py
```

Add your API key to the local .env file:

```env
OPENAI_API_KEY=your_api_key_here
OPENAI_MODEL=gpt-4.1-mini
```

Never commit .env or expose an API key in source code, screenshots, or public issue discussions. Local heuristic detection and report generation work without the AI key; AI explanation requires a configured key.

## Deploy as a public website

This Python/Streamlit app cannot be run by GitHub Pages alone. Deploy with [Streamlit Community Cloud](https://share.streamlit.io/):

1. Sign in using GitHub.
2. Create an app and select this repository and the main branch.
3. Set the main file path to app.py.
4. In app Secrets, add:

   ```toml
   OPENAI_API_KEY = "your_api_key_here"
   OPENAI_MODEL = "gpt-4.1-mini"
   ```

5. Deploy. Streamlit installs requirements.txt and provides a public streamlit.app URL.

## Risk score methodology

| Signal | Points |
|---|---:|
| Urgency or pressure | 20 |
| Credential request | 25 |
| Payment or financial pressure | 20 |
| Threat or reward language | 15 |
| One or more extracted URLs | 10 |

The score is capped at 100. Bands: 0–24 Lower concern; 25–59 Needs caution; 60–100 High concern. This is an illustrative rule-based score, not a calibrated probability or validated detection model.

## Documentation

- [Project report](PROJECT_REPORT.md)
- [Architecture and data flow](docs/ARCHITECTURE.md)
- [Functional test cases](docs/TEST_CASES.md)

Run the tests manually and record actual results before submission. The test-case file intentionally marks outcomes as pending; do not claim tests passed until executed.

## Scope and limitations

This is an educational prototype, not an enterprise email-security product. It does **not** authenticate the sender, validate SPF/DKIM/DMARC, open or reputation-check URLs, inspect attachments, or guarantee that an email is safe or malicious. Keyword rules can produce false positives and false negatives. AI output can also be inaccurate. Dashboard history is held in session memory only and is not a persistent case-management database.

Verify unexpected requests through a trusted contact method obtained independently.

---

**PhishGuard AI · Educational blue-team project**
