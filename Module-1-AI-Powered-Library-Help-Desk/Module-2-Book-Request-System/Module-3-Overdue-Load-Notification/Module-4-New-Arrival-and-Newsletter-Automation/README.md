# Module 4 — New Arrival Newsletter Automation

##  What It Does

A weekly automated newsletter system that detects 
new book arrivals, uses OpenAI to write engaging 
descriptions, personalises each newsletter by 
member reading interests, and distributes 
automatically every Friday.

---

##  How It Works

1. Schedule trigger fires every Friday at 10am
2. Google Sheets node reads all new books added that week
3. For each new book OpenAI generates a short engaging description
4. Member database is read — each member has stated reading interests
5. Filter node matches new arrivals to each member's interest category
6. Each member receives only books matching their preferences
7. Personalised newsletter delivered by email automatically

---

##  Google Sheets Structure

### New Arrivals Sheet
| Column | Description |
|--------|-------------|
| DateAdded | When book was logged |
| Title | Book title |
| Author | Author name |
| Category | Subject category |
| Description | AI-generated description |

### Members Sheet
| Column | Description |
|--------|-------------|
| Name | Member name |
| Email | Member email |
| ReadingInterests | Comma-separated categories |
| NewsletterOptIn | Yes / No |

---

##  Tools Used

- **n8n** — Scheduled workflow automation
- **OpenAI GPT-4o** — AI description generation
- **Google Sheets** — Arrivals and member database
- **Gmail** — Newsletter delivery

---

##  Workflow Screenshot

![Module 4 Workflow](../screenshots/module4-workflow.png)

---

##  Key Features

- Fully automated — zero manual content creation
- AI writes professional book descriptions
- Personalised by reading interest — not a generic blast
- Runs every Friday automatically
- Scales to any number of members
