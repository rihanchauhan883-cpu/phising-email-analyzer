# Mini Project Report
## AI-Powered Phishing Email Analyzer

**Project type:** Responsible Generative AI application  
**Technology:** Python, Streamlit, OpenAI API  
**Author:** [Your Name]  
**Institution:** [College / Department]  
**Date:** [Submission Date]

## 1. Abstract
Phishing messages attempt to manipulate recipients into revealing credentials, making payments, or opening unsafe links. This project builds an educational web application that combines simple local text rules with a generative AI explanation. It highlights possible warning signs and offers cautious next steps. The application is designed as a decision-support tool, not an automated security verdict.

## 2. Problem Statement
Beginners may struggle to recognize social-engineering signals in email. A plain binary detector can be hard to understand and can create false confidence. The proposed application explains which text patterns triggered concern and communicates uncertainty.

## 3. Objectives
- Accept a synthetic or sanitized email as input.
- Identify basic indicators using transparent local rules.
- Generate a plain-language explanation using an AI API.
- Recommend safe, human-controlled next steps.
- Demonstrate privacy, transparency, uncertainty, and prompt-injection awareness.

## 4. System Design
1. User enters a sanitized email and confirms it contains no sensitive data.
2. Local Python rules search for urgency, credential requests, financial pressure, threat/reward language, and URLs.
3. The app sends the text and detected indicators to the configured AI model.
4. The model returns an assessment, observed evidence, explanation, safe next steps, and limitations.
5. The user reviews the explanation and independently verifies any suspicious message.

## 5. Tools and Technologies
- Python: application logic and basic indicator rules.
- Streamlit: browser-based user interface.
- OpenAI Python SDK: API integration.
- python-dotenv: local environment variable loading.
- Regular expressions: simple URL extraction.

## 6. Responsible AI Design
- **Privacy:** user warning, sanitized-input confirmation, no intentional local database or app logging of submitted messages. API processing is subject to provider terms and settings.
- **Transparency:** clearly labels the model output as an AI explanation.
- **Human oversight:** no automatic email deletion, blocking, or link opening.
- **Reliability:** does not promise perfect detection; local indicators can have false positives and false negatives.
- **Security:** treats the email body as untrusted content and instructs the model not to follow embedded commands.
- **Safe use:** synthetic test messages use reserved example.test domains.

## 7. Test Plan
| Test | Input / action | Expected result |
|---|---|---|
| T1 | Urgent account suspension and password request | Urgency, credential, and URL indicators appear |
| T2 | Normal meeting message | Few/no indicators; no claim of verified safety |
| T3 | Prompt-injection text in email body | Content is treated as untrusted data |
| T4 | Empty input | Validation error; API not called |
| T5 | Sanitization confirmation unchecked | Request is not sent to API |
| T6 | Missing API key | Helpful configuration error; local indicators remain |
| T7 | API unavailable / invalid key | Error shown without fabricated analysis |
| T8 | Email contains a URL | URL is displayed as text only and is not opened |

**Record actual results before submission:** Pass/Fail, observed behavior, date, and screenshot. Do not claim tests passed until you run them.

## 8. Evaluation
Evaluate the project with synthetic examples. Record the expected category, actual local indicators, whether the explanation cites relevant evidence, whether it states uncertainty, and whether it gives safe next steps. A small student test set demonstrates functionality but is not enough to establish real-world detection accuracy.

## 9. Limitations
The project does not verify sender identity, SPF/DKIM/DMARC, domain reputation, link destinations, attachments, or mail-server logs. Keyword rules are simplistic. AI output can be inaccurate. Provider processing is subject to API terms and settings.

## 10. Future Enhancements
- Add structured, schema-validated model output.
- Evaluate on a larger labeled synthetic dataset and report precision/recall where appropriate.
- Add safe header analysis for SPF/DKIM/DMARC results supplied by the user.
- Add optional domain reputation lookup without visiting suspicious URLs.
- Add accessibility and multilingual testing.
- Add abuse protection and clear data-retention controls before public deployment.

## 11. Conclusion
The project demonstrates a practical use of generative AI for cybersecurity education while emphasizing explainability, privacy, uncertainty, and human oversight. It is a learning aid and should not replace established email security tools or security-team procedures.

## 12. References
- NIST, Artificial Intelligence Risk Management Framework (AI RMF 1.0): https://www.nist.gov/itl/ai-risk-management-framework
- Streamlit documentation: https://docs.streamlit.io/
- OpenAI API documentation: https://platform.openai.com/docs/
