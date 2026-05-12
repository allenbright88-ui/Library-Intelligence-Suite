# Module 3 — Overdue Book & Fine Reminder Automation

##  What It Does

A scheduled daily automation that monitors all 
active book loans, calculates overdue days and 
fine amounts automatically, and delivers 
multi-stage escalating reminders by email and 
WhatsApp — without any manual intervention.

---

##  How It Works

1. Schedule trigger fires every day at 8am
2. Google Sheets node reads all loan records
3. Date node calculates how many days each loan is overdue
4. JavaScript code node calculates fine amount automatically
5. Condition nodes route each loan to the correct stage

### The 4 Reminder Stages

| Stage | Trigger | Action |
|-------|---------|--------|
| Stage 1 | 1 day before due date | Friendly reminder by email + WhatsApp |
| Stage 2 | On due date | Final return reminder by email + WhatsApp |
| Stage 3 | 1-7 days overdue | Overdue notice with calculated fine amount |
| Stage 4 | 7+ days overdue | Formal demand notice + librarian alert |

6. When a book is marked as returned in Google Sheets
   all reminders stop automatically for that record

---

##  Loan Records Sheet Columns

| Column | Description |
|--------|-------------|
| MemberName | Borrower name |
| Email | Borrower email |
| WhatsApp | Borrower WhatsApp |
| BookTitle | Title borrowed |
| LoanDate | Date borrowed |
| DueDate | Return deadline |
| ReturnStatus | Not Returned / Returned |
| FineAmount | Auto-calculated fine |
| LastReminderSent | Stage of last reminder |
| DaysOverdue | Calculated daily |

---

##  Fine Calculation Logic

```javascript
const daysOverdue = Math.max(0, 
  Math.floor((now - dueDate) / (1000 * 60 * 60 * 24))
);
const finePerDay = 50; // ₦50 per day
const totalFine = daysOverdue * finePerDay;
```

---

##  Tools Used

- **n8n** — Scheduled workflow automation
- **Google Sheets** — Loan records database
- **Gmail** — Email reminders
- **Twilio (WhatsApp)** — WhatsApp reminders
- **JavaScript** — Fine calculation logic

---

##  Workflow Screenshot

![Module 3 Workflow](../screenshots/module3-workflow.png)

---

##  Key Features

- Fully scheduled — fires automatically every day
- Auto-calculates fines using JavaScript
- 4-stage escalation from friendly to formal
- Dual channel delivery (email + WhatsApp)
- Reminders auto-stop when book is returned
