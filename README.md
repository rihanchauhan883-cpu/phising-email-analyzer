# PhishGuard AI — AI-Powered Phishing Email Analyzer

A portfolio-style, interactive cybersecurity project built with Python and Streamlit. It combines transparent local keyword heuristics with an optional OpenAI-powered explanation to help learners review possible phishing indicators.

## Project highlights

- **Portfolio-style interface:** project overview, capabilities, workflow, technology stack, and limitations.
- **Interactive email analyzer:** paste a synthetic or sanitized email and review matched local indicators.
- **Local heuristic checks:** urgency, credential requests, payment pressure, threat/reward wording, and URL extraction.
- **AI-assisted explanation:** summarizes evidence and suggests safe next steps when an API key is configured.
- **Safety-first behavior:** email content is treated as untrusted input; URLs are not opened or verified.

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

Never commit .env or expose an API key in source code, screenshots, or public issue discussions.

## Deploy as a public website

This is a Python/Streamlit app, so GitHub Pages alone cannot run it. Deploy it with [Streamlit Community Cloud](https://share.streamlit.io/):

1. Sign in using GitHub.
2. Create an app and select this repository and the main branch.
3. Set the main file path to app.py.
4. In the app's Advanced settings / Secrets, add:

   ```toml
   OPENAI_API_KEY = "your_api_key_here"
   OPENAI_MODEL = "gpt-4.1-mini"
   ```

5. Deploy. Streamlit installs packages from requirements.txt and provides a public streamlit.app URL.

## Analysis workflow

1. User pastes a synthetic or sanitized email and confirms it contains no sensitive information.
2. Local Python rules search for selected suspicious phrases and extract URL strings.
3. If configured, the app sends the sanitized email and local indicators to the selected OpenAI model for an explanation.
4. The interface displays local indicators and the AI-generated explanation.

## Scope and limitations

This is an educational prototype, not an enterprise email-security product. It does **not** authenticate the sender, validate SPF/DKIM/DMARC, open or reputation-check URLs, inspect attachments, or guarantee that an email is safe or malicious.

Keyword rules can produce false positives and false negatives. AI output can also be inaccurate. Verify unexpected requests through a trusted contact method obtained independently.

## Future improvements

- Parse and explain email headers.
- Add SPF/DKIM/DMARC result ingestion from trusted analysis sources.
- Add safe URL reputation lookups without visiting links directly.
- Add attachment metadata analysis in an isolated workflow.
- Build a test dataset and measure precision, recall, and false-positive rate.

---

**PhishGuard AI · Educational blue-team project**
