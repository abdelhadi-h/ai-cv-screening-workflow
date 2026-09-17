# 🤖 AI CV Screening Workflow

> AI-powered CV screening and candidate evaluation workflow built with n8n, Google Gemini, Gmail, and Google Sheets.

This workflow automates the initial CV screening process for a Software Engineer position.

It collects candidate information through an application form, extracts text from the uploaded PDF CV, analyzes the candidate using Google Gemini, generates a compatibility rating and recommendation, stores the candidate information in Google Sheets, and notifies HR by email.

The workflow also sends an automatic confirmation email to the candidate after the application is processed.

---

# 🚀 Overview

Manual CV screening can require HR teams to review large numbers of applications individually.

This workflow demonstrates how AI and workflow automation can be used to automate the first stage of candidate screening.

The current workflow follows this process:

```text
Candidate Application
        ↓
PDF CV Upload
        ↓
Extract CV Text
        ↓
AI Analysis with Gemini
        ↓
Compatibility Rating
        ↓
Save Candidate to Google Sheets
        ↓
Notify HR
        ↓
Send Confirmation Email
✨ Features
📝 Candidate Application Form

The workflow starts with an n8n application form for a:

Software Engineer Position

The form collects:

Full Name
E-mail
Salary Expectation
LinkedIn
Resume / CV in PDF format

The CV upload is required and accepts .pdf files.

📄 CV Extraction

The uploaded CV is processed using n8n's file extraction functionality.

The workflow extracts text from the uploaded PDF before sending it to the AI analysis step.

This converts the uploaded resume into text that can be analyzed by the AI model.

🧠 AI CV Analysis

The workflow uses:

Google Gemini Chat Model

The AI analysis compares the candidate's resume against the job description:

Software Engineer

The AI is instructed to evaluate:

Candidate skills
Experience
Qualifications
Job compatibility
Overall suitability

The AI also produces a compatibility rating from:

1 = Not Compatible
10 = Perfect Fit

The analysis includes:

Compatibility Rating
Recommendation
Reasoning for the recommendation

The workflow limits the AI response to a maximum of 75 words and supports configurable output language through the workflow prompt.

📊 Candidate Database

After AI analysis, the candidate information is stored in Google Sheets.

The spreadsheet stores:

Field	Description
CV	Uploaded CV filename
Full Name	Candidate name
E-mail	Candidate email
Expectation	Candidate salary expectation
Linkedin	Candidate LinkedIn profile
AI Rating	AI-generated screening result

The workflow uses a Google Sheet named:

CV of Software Engineers
📧 HR Notification

After the candidate is added to the candidate list, the workflow sends an email notification to HR.

The HR notification includes:

Candidate Name
Candidate Email
Candidate LinkedIn
Candidate Salary Expectation
AI Rating

Example subject:

New Candidate CV Awaiting Review

The purpose is to notify HR that a new CV has been processed and is ready for review.

✅ Candidate Confirmation

After the HR notification step, the workflow sends a confirmation email to the candidate.

Example subject:

We Have Received Your CV

The email confirms that:

Your CV has been received and will be reviewed shortly.

This creates an automated candidate communication step without requiring HR to send the email manually.

⚙️ Workflow Architecture
┌──────────────────────────────┐
│      Candidate Application   │
│          n8n Form            │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│        PDF CV Upload         │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       CV Text Extraction     │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│     Google Gemini AI         │
│      CV Screening            │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       Candidate List         │
│       Google Sheets          │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       HR Notification        │
│            Gmail             │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│    Candidate Confirmation    │
│            Gmail             │
└──────────────────────────────┘
🔄 Workflow Sequence

The workflow consists of the following major steps:

1. Application Form

The candidate submits:

Full Name
E-mail
Expectation
LinkedIn
Resume/CV
2. Convert Binary to JSON

The PDF CV is extracted into text.

3. AI Analysis & Rating

The extracted resume text is sent to the Google Gemini model.

4. Candidate Lists

The candidate data and AI screening result are stored in Google Sheets.

5. Inform HR

HR receives a notification about the new candidate.

6. Confirmation of CV Submission

The candidate receives a confirmation email.

🛠️ Technology Stack
Technology	Purpose
n8n	Workflow automation
Google Gemini	AI CV analysis
Gmail	Candidate and HR email notifications
Google Sheets	Candidate database
PDF Extraction	Resume text extraction
📋 Example Candidate Data

Example:

Full Name:
John Doe

E-mail:
john@example.com

Expectation:
2000-3000$

LinkedIn:
https://linkedin.com/in/johndoe

Resume:
john-doe-cv.pdf

The workflow processes the candidate information automatically.

🧠 Example AI Screening Result

The workflow is designed to produce a concise result containing:

Compatibility Rating: 8/10

Recommendation:
Consider the candidate for an interview.

Reason:
The candidate demonstrates relevant software engineering
experience and skills aligned with the position requirements.

The exact result depends on the submitted CV and AI analysis.

🎯 Use Case

This workflow is suitable for companies that want to automate the first stage of recruitment.

Potential applications include:

Software engineering recruitment
Developer hiring
Technical recruitment
HR automation
Candidate pre-screening
Recruitment agencies
Internal hiring systems
🏢 Business Process

Traditional workflow:

Candidate
   ↓
Application
   ↓
HR manually opens CV
   ↓
HR reads CV
   ↓
HR evaluates candidate
   ↓
HR updates spreadsheet
   ↓
HR sends email

Automated workflow:

Candidate
   ↓
Application Form
   ↓
AI CV Screening
   ↓
Google Sheets
   ↓
HR Notification
   ↓
Candidate Confirmation
📁 Project Structure
ai-cv-screening-workflow/
│
├── README.md
│
├── .gitignore
│
└── workflows/
    └── AI-CV-Screening-Workflow.json
🔧 Installation
1. Install n8n

Install n8n locally or use a hosted n8n deployment.

Official documentation:

https://docs.n8n.io/

2. Import the Workflow

Import the workflow JSON file into n8n.

Example:

workflows/AI-CV-Screening-Workflow.json
3. Configure Google Gemini

Connect the Google Gemini credentials used by the AI model.

The Gemini model is used by the CV analysis step.

4. Configure Gmail

Connect the Gmail credentials required for:

HR notification
Candidate confirmation email
5. Configure Google Sheets

Connect the Google Sheets account and configure the candidate spreadsheet.

The current workflow stores candidate information in a spreadsheet named:

CV of Software Engineers
6. Configure the Application Form

Make sure the candidate form contains the required fields:

Full Name
E-mail
Expectation
Linkedin
Your Resume/CV

The CV field should accept PDF files.

🔐 Security

Before publishing this workflow publicly, review all credentials, IDs, email addresses, spreadsheet references, and other configuration values.

Never commit:

API keys
OAuth credentials
Passwords
Private access tokens
Private candidate information
Private recruitment data
Internal HR email addresses
Private Google Sheet identifiers

Use n8n credentials and secure configuration instead.

⚠️ Public GitHub Preparation

Before uploading this workflow to a public repository, replace organization-specific information with placeholders.

For example:

YOUR_HR_EMAIL
YOUR_GOOGLE_SHEET_ID
YOUR_GOOGLE_SHEET_NAME
YOUR_COMPANY_NAME

This makes the workflow safer to share publicly and easier for other users to configure.

🧪 Testing

A basic test can be performed by submitting a sample candidate application.

Example:

Name:
Test Candidate

Email:
test@example.com

Expectation:
2000-3000$

LinkedIn:
https://linkedin.com/in/test

CV:
sample-cv.pdf

Then verify that:

✓ CV is uploaded
✓ PDF text is extracted
✓ Gemini analyzes the resume
✓ Candidate is added to Google Sheets
✓ HR receives an email
✓ Candidate receives confirmation
📌 Current Scope

The current workflow focuses on:

Application collection
PDF CV extraction
AI screening
Compatibility rating
Candidate storage
HR notification
Candidate confirmation

It is primarily a first-stage recruitment automation workflow.

🔮 Roadmap
Phase 1 — Current
 Candidate application form
 PDF CV upload
 CV text extraction
 AI screening
 Compatibility rating
 Google Sheets storage
 HR notification
 Candidate confirmation
Phase 2 — Recruitment Intelligence
 Multiple job descriptions
 Job-specific screening
 Candidate ranking dashboard
 Candidate filtering
 Experience extraction
 Skills extraction
 Education extraction
Phase 3 — Advanced AI
 AI interview generation
 Automated interview invitations
 Candidate question generation
 Candidate scoring dashboard
 Multi-language screening
 Candidate summary generation
Phase 4 — Recruitment Platform
 Recruitment dashboard
 Candidate pipeline
 Interview management
 Recruiter workspace
 Candidate search
 Recruitment analytics
 Automated follow-ups
🌍 Future Improvements

Future versions can extend the workflow to support:

Multiple Jobs
      ↓
Job-Specific AI Analysis
      ↓
Candidate Matching
      ↓
Candidate Ranking
      ↓
Recruiter Dashboard
      ↓
Interview Automation
📚 What This Project Demonstrates

This project demonstrates practical use of:

AI-powered recruitment
Workflow automation
n8n
Google Gemini
Gmail automation
Google Sheets
PDF processing
Candidate data management
Automated HR communication
🎓 Learning Objectives

The project demonstrates how AI can be integrated into a real business process rather than being used only as a standalone chatbot.

The core concept is:

Form
+
Document Processing
+
AI
+
Database
+
Email Automation
📊 Automation Value

The workflow can reduce repetitive work during the initial recruitment stage by connecting application collection, CV processing, AI evaluation, candidate storage, and automated communication into one workflow.

The workflow does not replace the final hiring decision.

It automates an initial screening step and provides HR with structured information for review.

👨‍💻 Author
Abdelhadi Habibi

Computer Science student and builder focused on:

Artificial Intelligence
Automation
SaaS
Business Systems
HR Automation
Workflow Automation
📄 License

This project is currently provided for:

Educational purposes
Demonstration
Development
Experimentation

A formal open-source license can be added in a future release.

⭐ Project Vision

The vision is to build practical AI automation systems that connect business processes from beginning to end.

For recruitment:

Candidate
    ↓
Application
    ↓
CV Processing
    ↓
AI Screening
    ↓
Candidate Database
    ↓
HR Notification
    ↓
Interview

AI + Automation + Business Process
