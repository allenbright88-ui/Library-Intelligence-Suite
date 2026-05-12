# Module 1 — AI-Powered Library Help Desk

##  What It Does

A real-time AI chatbot that answers library user 
enquiries 24/7 from a structured knowledge base, 
executes live handoff to a human librarian when 
requested.

---

##  How It Works

### Path 1 — AI Response
1. User submits a question via the chat interface
2. Webhook receives the data in n8n
3. Data is extracted and logged to Google Sheets
4. IF node checks whether user wants a human
5. If NO → AI Agent queries the FAQ knowledge base
6. AI generates a contextual response
7. Respond to Webhook sends response to chat window instantly
8. Google Sheets updated with the AI response

### Path 2 — Live Librarian Handoff
1. User types a handoff trigger phrase
2. IF node detects the request
3. Librarian notified by email with full conversation details
4. User receives confirmation in the chat window instantly
5. Google Sheets updated with handoff status

### Background — Session Transcript Sender
1. Separate workflow runs every 30 minutes
2. Checks Google Sheets for sessions inactive 30+ minutes
3. Compiles full chat transcript
4. Emails transcript to the user
5. Marks TranscriptSent = Yes to prevent duplicates

---

##  Google Sheets Columns

| Column | Description |
|--------|-------------|
| Timestamp | When the message was received |
| SessionID | Unique ID linking conversation messages |
| Name | User full name |
| Email | User email address |
| Question | The user's message |
| Response | AI response or handoff note |
| HandOff Requested | Yes / No |
| TranscriptSent | Yes / No |
| Channel | Chat / Form |
| SessionStatus | Active / Ended |

---

##  Tools Used

- **n8n** — Workflow automation
- **OpenAI GPT-4o** — AI response generation
- **Lovable** — Chat interface frontend
- **Gmail** — Email notifications and transcripts
- **Google Sheets** — Interaction logging
- **Twilio** — WhatsApp notifications

---

##  Workflow Screenshot

![Module 1 Workflow](../screenshots/module1-workflow.png)

---

##  Live Demo

👉 [Try the AI Help Desk]: https://roper-chat-aide.lovable.app

---

##  Key Features

- Answers user questions 24/7 without human involvement
- Detects handoff requests using keyword matching
- Remembers conversation context across multiple messages
- Auto-sends full chat transcript at session end
- Logs every interaction for librarian review
