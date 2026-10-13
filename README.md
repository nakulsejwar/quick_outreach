# Quick Outreach v3 — profile fixes + selectable attachments

One local Streamlit app. `.env` holds secrets/settings, `profile.json` holds the candidate profile, and `attachments/` contains optional files to attach.

## Windows setup
```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
Copy-Item .env.example .env
notepad .env
streamlit run app.py
```
If `.env` already exists, keep it instead of overwriting it.

## Profile updates
- Candidate contact email remains blank because no address was supplied. It is optional for sending; sender Gmail is read from `.env`.
- Experience is described as approximately 2.8 years based on the current self-reported summary; verify exact dates before claiming a precise duration.
- Minimum salary expectation remains ₹40,000/month. A ₹26,000–₹38,000/month range is flagged as below expectation; the app must not claim acceptance or flexibility unless you tell it to.

## Attachments
1. Put files such as `resume.pdf` and `cover_letter.pdf` into `attachments/`.
2. Refresh/rerun the app.
3. Select the files in the email review section.
4. Verify recipient, email, and attachments, then confirm Send.

## Logs and security
- `app.log` is automatically created with rotating backups. It avoids logging secrets, email bodies, and profile content.
- Never commit `.env`, `profile.json`, `app.log`, or private attachments.
- OpenRouter receives profile and opportunity content to draft the email.
- Every email requires manual review and confirmation.
- Use a Google App Password, not your normal Gmail password. If App Passwords are unavailable, switch to Gmail API OAuth.
