# Detect duplicate candidates from Gmail to Slack using Google Sheets

This workflow automatically detects duplicate job applicants by checking incoming emails from Gmail against existing records in Google Sheets.  
If a candidate's email is already found in the sheet, it sends an alert to Slack; otherwise, it adds the candidate to the sheet. :contentReference[oaicite:1]{index=1}

---

## Who’s It For

- HR and recruitment teams processing candidate emails manually
- Startups or SMEs handling job applications via Gmail
- Anyone who wants to automate resume collection and deduplication
- Teams using Slack and Google Workspace :contentReference[oaicite:2]{index=2}

---

## How It Works

1. Triggers every few minutes via the **Schedule Trigger** node
2. Fetches recent emails labeled _applicant_ from Gmail
3. Extracts candidate details from the email body using regex
4. Reads all existing rows from the Google Sheet
5. Compares the candidate’s email with existing entries
6. If duplicate → Sends a Slack alert
7. If new → Appends to the Google Sheet :contentReference[oaicite:3]{index=3}

---

## How to Set Up

1. Label candidate emails in Gmail with a label like `applicant`
2. Connect **Gmail**, **Google Sheets**, and **Slack** credentials in n8n
3. Create a **Google Sheet** with these columns:
   - `candidate_name`, `candidate_email`, `candidate_phone`
   - `role_applied`, `years_of_experience`, `recruiter`
   - `resume_url`, `source_email`
4. Import the workflow JSON
5. Update:
   - Gmail label ID
   - Google Sheet ID
   - Slack channel or user
6. Activate the workflow :contentReference[oaicite:4]{index=4}

---

## Requirements

- n8n (self-hosted or cloud)
- Gmail account with access to labeled application emails
- Google Sheet to store candidates
- Slack account with `chat:write` scope
- Basic regex familiarity (optional) :contentReference[oaicite:5]{index=5}

---

## How to Customize

- Change comparison logic to include phone numbers
- Add fallback logic to check for similar names
- Add filters for roles or experience levels
- Forward resumes to Google Drive or Notion
- Trigger an approval flow for screened candidates :contentReference[oaicite:6]{index=6}

---

## Add-Ons

- **Google Drive:** Upload parsed resumes
- **Notion / Airtable:** Store structured candidate records
- **Webhooks:** Forward to ATS or CRM
- **PDF parsers:** Extract data from resume attachments :contentReference[oaicite:7]{index=7}

---

## Use Case Examples

| Use Case                 | Description                                           |
| ------------------------ | ----------------------------------------------------- | ------------------------------------- |
| **Resume deduplication** | Avoid processing the same applicant twice             |
| **Auto Slack alert**     | Instantly notify recruiter of repeat candidates       |
| **Centralized tracking** | Keep candidate records in Sheets for filtering/export |
| **Passive sourcing**     | Run hourly checks on labeled Gmail inboxes            | :contentReference[oaicite:8]{index=8} |

---

## Common Troubleshooting

| Issue                    | Possible Cause                             | Solution                                                       |
| ------------------------ | ------------------------------------------ | -------------------------------------------------------------- | ------------------------------------- |
| Slack message not sent   | Invalid Slack token / channel not selected | Reauthorize Slack connection and select correct user/channel   |
| Google Sheet not updated | Sheet ID or tab name is incorrect          | Double-check the Sheet URL and worksheet tab                   |
| Email data not extracted | Email body format doesn’t match regex      | Adjust regex in the Code node                                  |
| Nothing happens          | Gmail label or date filter is too strict   | Ensure emails exist with the right label in the last X minutes | :contentReference[oaicite:9]{index=9} |

---

## Need Help?

Need help setting it up or tweaking regex for your custom email format? We’re happy to help — just ask!  
Want advanced modifications like phone number duplication checks or auto-resume upload to Google Drive? Our automation team can guide you step-by-step. :contentReference[oaicite:10]{index=10}
