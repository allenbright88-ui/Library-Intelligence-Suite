# Module 2 — Automated Book Request & Availability System

##  What It Does

A three-path intelligent system that handles every 
possible book request scenario automatically — 
available, unavailable, and not in catalogue — 
with instant email and WhatsApp notifications.

---

##  How It Works

### Workflow 1 — Book Request (Member Facing)

**Path A — Book Available**
1. Member submits book request form
2. Data extracted and formatted
3. Request logged to Google Sheets
4. System searches entire book catalogue
5. Code node matches requested title intelligently
6. IF node checks availability
7. Book catalogue updated (copies reduced by 1)
8. Request status updated to Confirmed
9. Member notified by email and WhatsApp instantly

**Path B — Book Unavailable (Waitlist)**
1. Steps 1-6 same as above
2. System reads all waitlist rows
3. Code node calculates waitlist position
4. Request status updated to Waitlist
5. Member notified of position by email and WhatsApp

**Path C — Book Not in Catalogue**
1. Code node returns bookFound = false
2. Request logged with status Not in Catalogue
3. Member notified by email and WhatsApp
4. Librarian alerted to review for potential acquisition

### Workflow 2 — Book Return (Librarian Facing)
1. Librarian fills return form (title, condition, date)
2. System reads full catalogue to find returned book
3. Code node matches book and calculates new availability
4. Catalogue updated (copies increased by 1)
5. Waitlist sheet checked for next person
6. If someone is waiting → notified by email and WhatsApp
7. Their status updated from Waitlist to Confirmed

---

##  Google Sheets Structure

### Book Catalogue Sheet
| Column | Description |
|--------|-------------|
| BookID | Unique book identifier |
| Title | Book title |
| Author | Author name |
| Category | Subject category |
| TotalCopies | Total copies owned |
| AvailableCopies | Copies currently available |
| Status | Available / Unavailable |

### Book Requests & Waitlist Sheet
| Column | Description |
|--------|-------------|
| Timestamp | Request submission time |
| RequestID | Unique request identifier |
| Name | Member name |
| Email | Member email |
| WhatsApp | Member WhatsApp number |
| BookTitle | Requested book title |
| Author | Requested author |
| RequestStatus | Confirmed / Waitlist / Not in Catalogue |
| NotificationSent | Yes / No |
| WaitlistPosition | Position in queue |
| ReservationExpiry | 7 days from confirmation |

---

##  Tools Used

- **n8n** — Workflow automation
- **Google Sheets** — Catalogue and request management
- **Gmail** — Email notifications
- **Twilio (WhatsApp)** — WhatsApp notifications
- **Lovable** — Request form frontend
- **JavaScript** — Intelligent book matching and formatting

---

##  Workflow Screenshots

![Book Request Workflow](../screenshots/module2-request-workflow.png)
![Book Return Workflow](../screenshots/module2-return-workflow.png)

---

##  Key Features

- Handles 3 complete scenarios with no manual work
- Intelligent book title matching (case insensitive, partial match)
- Auto waitlist position assignment and tracking
- Instant dual-channel notification (email + WhatsApp)
- Librarian form for logging returns triggers full cascade
