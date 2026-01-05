
# Detect Duplicate Candidates from Gmail to Slack Using Google Sheets

This workflow automatically detects duplicate job applicants by checking incoming emails from Gmail against existing records in Google Sheets.
If a candidate’s email already exists, it sends an alert to Slack; otherwise, it adds the candidate to the sheet.

---

## Who’s It For

* HR and recruitment teams processing candidate emails manually
* Startups or SMEs handling job applications via Gmail
* Anyone looking to automate resume collection and deduplication
* Teams using Slack and Google Workspace

---

## How It Works

1. Triggers at a fixed interval using the **Schedule Trigger** node
2. Fetches recent emails labeled `applicant` from Gmail
3. Extracts candidate details from the email body using regex
4. Reads existing candidate records from Google Sheets
5. Compares the incoming candidate email with existing entries
6. If duplicate → Sends a Slack alert
7. If new → Appends the candidate to Google Sheets

---

## How to Set Up

1. Label candidate emails in Gmail with a label such as `applicant`
2. Connect **Gmail**, **Google Sheets**, and **Slack** credentials in n8n
3. Create a **Google Sheet** with the following columns:

   * `candidate_name`
   * `candidate_email`
   * `candidate_phone`
   * `role_applied`
   * `years_of_experience`
   * `recruiter`
   * `resume_url`
   * `source_email`
4. Import the workflow JSON into n8n
5. Update:

   * Gmail label ID
   * Google Sheet ID and tab name
   * Slack channel or user
6. Activate the workflow

---

## Requirements

* n8n (cloud or self-hosted)
* Gmail account with labeled application emails
* Google Sheet for candidate storage
* Slack account with `chat:write` permission
* Basic regex knowledge (optional)

---

## How to Customize

* Extend comparison logic to include phone numbers
* Add fuzzy matching for similar candidate names
* Filter candidates by role or experience level
* Upload resume attachments to Google Drive or Notion
* Add approval or screening flows for shortlisted candidates

---

## Add-Ons

* **Google Drive** – Upload and store parsed resumes
* **Notion / Airtable** – Maintain structured candidate databases
* **Webhooks** – Forward candidates to ATS or CRM systems
* **PDF Parsers** – Extract structured data from resume attachments

---

## Use Case Examples

| Use Case             | Description                                        |
| -------------------- | -------------------------------------------------- |
| Resume deduplication | Avoid processing the same applicant multiple times |
| Auto Slack alert     | Instantly notify recruiters of repeat candidates   |
| Centralized tracking | Maintain candidate records in Google Sheets        |
| Passive sourcing     | Run scheduled checks on labeled Gmail inboxes      |

---

## Common Troubleshooting

| Issue                    | Possible Cause                              | Solution                                                   |
| ------------------------ | ------------------------------------------- | ---------------------------------------------------------- |
| Slack message not sent   | Invalid Slack token or channel not selected | Reauthorize Slack and select the correct channel or user   |
| Google Sheet not updated | Incorrect Sheet ID or tab name              | Verify the Google Sheet URL and worksheet tab              |
| Email data not extracted | Regex does not match email body             | Update regex logic in the Code node                        |
| Workflow not running     | Gmail label or time filter too strict       | Ensure labeled emails exist within the trigger time window |

---

## Need Help?

Need help setting this up or adjusting regex for your custom email format? We’re happy to help.

Looking for advanced enhancements like:

* Phone number duplication checks
* Auto-upload resumes to Google Drive
* ATS or CRM integrations

Our automation experts can guide you step by step 👍
