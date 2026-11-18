# Test Cases — PhishGuard AI

Run each test in the app and record the actual outcome and screenshot before submission. Expected results are not proof that a test passed.

| ID | Test input / action | Expected result | Actual result |
|---|---|---|---|
| TC-01 | Load “Suspicious account alert” sample | Urgency, credential and URL indicators; elevated heuristic score | Pending manual run |
| TC-02 | Load “Routine meeting note” sample | No configured indicators or low score; app must not call it verified safe | Pending manual run |
| TC-03 | Load “Invoice pressure” sample | Payment and threat indicators; score reflects matched categories | Pending manual run |
| TC-04 | Submit empty input | Validation message; no report generated | Pending manual run |
| TC-05 | Leave sanitization checkbox unchecked | Analysis is blocked | Pending manual run |
| TC-06 | Analyze text containing an http(s) URL | URL string extracted and shown; app does not open it | Pending manual run |
| TC-07 | Run without OPENAI_API_KEY | Local score/evidence still appear; AI configuration error shown | Pending manual run |
| TC-08 | Configure invalid/unavailable API key | AI error shown; no fabricated AI explanation | Pending manual run |
| TC-09 | Include “ignore previous instructions” in sample | Text is treated as untrusted email content; no embedded instruction is followed | Pending manual run |
| TC-10 | Download TXT and JSON reports | Both downloads contain report ID, score, band, evidence and limitations | Pending manual run |

## Test procedure

1. Start locally with `streamlit run app.py`.
2. Use only the built-in synthetic samples or sanitized test content.
3. Run each case and compare the observed result with the expected result.
4. Record Pass/Fail, date, environment, and a screenshot in the submission evidence folder.
5. Do not claim accuracy or detection performance from these functional tests; a labeled dataset and formal evaluation are required for that.
