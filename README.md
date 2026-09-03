# 🤖 AI-Powered Personal Assistant & Automation System

An AI-powered personal assistant built using **Streamlit, n8n, Google Gemini, and Google Workspace services**.

The system allows users to interact with an AI assistant through a simple interface and perform useful tasks such as searching the web, managing emails, tracking expenses, creating notes, managing tasks, and handling calendar events.

**Domain:** Personal Productivity / Student Productivity

---

## 📌 Project Overview

The **AI-Powered Personal Assistant & Automation System** is an automation-based AI assistant designed to simplify everyday productivity tasks.

The user communicates with the assistant through a Streamlit interface. The request is sent to an **n8n Webhook**, where an **AI Agent powered by Google Gemini** understands the request and decides which connected tool should be used.

The selected tool performs the required operation, and the result is returned to the user through the frontend.

### Main Architecture

```text
┌─────────────────────┐
│    Streamlit UI     │
│  User sends request │
└──────────┬───────────┘
           │
           ▼
┌─────────────────────┐
│     n8n Webhook      │
└──────────┬───────────┘
           │
           ▼
┌─────────────────────┐
│       AI Agent        │
│    Google Gemini     │
└──────────┬───────────┘
           │
     ┌─────┴─────────────────────────────────┐
     │                                       │
     ▼                                       ▼
┌──────────────┐                       ┌──────────────┐
│ Google Search │                       │     Gmail     │
└──────────────┘                       └──────────────┘
     │                                       │
     ├──────────────┐                        │
     ▼              ▼                        ▼
┌───────────┐  ┌───────────┐          ┌────────────┐
│ Expenses  │  │ Calculator│          │ Google Docs│
│  Sheets   │  │           │          │   Notes    │
└───────────┘  └───────────┘          └────────────┘
     │
     ├───────────────────┐
     ▼                   ▼
┌──────────────┐   ┌────────────────┐
│ Google Tasks │   │ Google Calendar│
└──────────────┘   └────────────────┘
           │
           ▼
┌─────────────────────┐
│ Respond to Webhook   │
└──────────┬───────────┘
           │
           ▼
┌─────────────────────┐
│    Streamlit UI      │
│   Final Response      │
└─────────────────────┘
```

---

## 🎯 Objectives

The main objectives of this project are:

- Build an AI-powered personal productivity assistant.
- Integrate an AI Agent with multiple external tools.
- Automate common personal and productivity tasks.
- Provide a simple and user-friendly interface.
- Store and retrieve relevant user data.
- Demonstrate practical use of AI Agents and workflow automation.
- Integrate multiple Google Workspace services into a single assistant.

---

## ✨ Features

### 🧠 AI Agent

The system uses a Google Gemini-powered AI Agent to understand natural-language requests and determine which tool is required.

The AI Agent is configured to:

- Understand user requests.
- Use tools when required.
- Keep tool usage silent.
- Provide concise responses.
- Display lists and records clearly.
- Return all available records when requested.
- Perform calculations when useful.

### 🌐 Google Search

The assistant can perform web searches using SerpApi.

**Example:**
```
User: What is the latest AI news?
A: [Searches the web and returns relevant results]
```

The search tool is configured for Pakistan-based search results and Google Pakistan localization.

### 📧 Gmail Integration

The assistant can interact with Gmail.

**Supported operations**
- Get a single email
- Get multiple emails
- Send an email

**Example:**
```
User: Send an email to abc@example.com saying that I will attend the meeting.
A: Email sent successfully.
```

### 💰 Expense Management

Expense data is stored using Google Sheets.

**Supported operations**
- Add an expense
- Get expenses
- Update expenses
- Calculate totals

**Example:**
```
User: Add an expense of 500 for transportation.
A: Expense added successfully.
```

```
User: Show me all my expenses.
A: [Returns expense records from Google Sheets]
```

### 📝 Notes Management

Google Docs is used for note management.

**Supported operations**
- Create notes
- Retrieve notes
- Update notes

**Example:**
```
User: Create a note titled "Machine Learning Ideas".
A: Note created successfully.
```

### ✅ Google Tasks

The assistant integrates with Google Tasks.

**Supported operations**
- Create tasks
- Get a single task
- Get multiple tasks

**Example:**
```
User: Create a task called "Complete ML assignment".
A: Task created successfully.
```

### 📅 Google Calendar

The assistant can manage calendar events.

**Supported operations**
- Create events
- Get a single event
- Get multiple events
- Update events
- Delete events

**Example:**
```
User: Create a meeting tomorrow from 10 AM to 11 AM.
A: Calendar event created successfully.
```

### 🧮 Calculator

A calculator tool is connected to the AI Agent for numerical calculations.

**Example:**
```
User: What is 1250 + 350 + 500?
A: 2100
```

### 🧠 Conversation Memory

The workflow includes an n8n Simple Memory component connected to the AI Agent.

This allows the assistant to maintain conversational context during interactions.

---

## 🏗️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Backend/frontend development |
| Streamlit | User interface |
| n8n | Workflow automation |
| Google Gemini | AI language model |
| SerpApi | Web search |
| Gmail API | Email management |
| Google Sheets | Expense storage |
| Google Docs | Notes management |
| Google Tasks | Task management |
| Google Calendar | Calendar management |

---

## 🔄 n8n Workflow

The core n8n workflow consists of three main stages:

**1. Webhook**

The Streamlit frontend sends the user's message to the n8n Webhook.

```
POST /webhook/...
```

The user message is extracted from:

```
$json.body.message
```

**2. AI Agent**

The AI Agent receives the user's request and determines whether one of the connected tools is required.

The Gemini Chat Model provides the language understanding capability.

**3. Respond to Webhook**

After the AI Agent completes the task, the response is returned through the Respond to Webhook node.

---

## 🔌 AI Agent Tools

The AI Agent currently has the following tools connected:

```
Google Search
     │
   Gmail
     │
Add Expense
     │
Get Expenses
     │
Update Expenses
     │
Calculator
     │
Create Notes
     │
Get Notes
     │
Update Notes
     │
Create Google Task
     │
Get Single Task
     │
Get Tasks
     │
Create Calendar Event
     │
Get Calendar Event
     │
Get Many Calendar Events
     │
Update Calendar Event
     │
Delete Calendar Event
```

All of these tools are connected directly to the AI Agent.

---

## 📂 Project Structure

Recommended repository structure:

```
AI-Powered-Personal-Assistant/
│
├── streamlit/
│   └── app.py
│
├── n8n/
│   └── n8n_Personal_Assistant_Workflow_PUBLIC.json
│
├── screenshots/
│   ├── streamlit-ui.png
│   ├── n8n-workflow.png
│   ├── ai-agent.png
│   ├── google-sheets.png
│   ├── gmail.png
│   └── final-output.png
│
├── report/
│   └── Final-Internship-Project-Report.pdf
│
├── .env.example
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 🖥️ User Interface

The frontend is developed using Streamlit.

The interface provides a simple way for users to:

- Enter a request.
- Send the request to n8n.
- Wait for the AI Agent to process it.
- Receive the final response.

**Example requests:**

- Show all my expenses.
- Send an email to my friend.
- Create a task to complete my assignment.
- Create a calendar event tomorrow at 2 PM.
- Create a note about machine learning.
- Search the web for the latest AI news.

---

## ⚙️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/AI-Powered-Personal-Assistant.git
cd AI-Powered-Personal-Assistant
```

### 2. Install Python Dependencies

```bash
pip install -r requirements.txt
```

### 3. Install and Run n8n

If using a local n8n installation:

```bash
n8n
```

Then open:

```
http://localhost:5678
```

---

## 🔐 Configuration

The project requires API credentials for the services used by the workflow.

These credentials should be configured inside n8n.

Required integrations may include:

- Google Gemini
- SerpApi
- Gmail
- Google Sheets
- Google Docs
- Google Tasks
- Google Calendar

---

## ⚠️ Security

Never upload real API keys, OAuth client secrets, access tokens, refresh tokens, passwords, or service-account JSON files to GitHub.

Use placeholders in the public workflow file.

**Example:**

```
YOUR_GOOGLE_SHEET_ID
YOUR_CALENDAR_ID
YOUR_TASK_LIST_ID
```

Credentials should be configured separately in your own n8n instance.

---

## ▶️ Running the Project

**Step 1 — Start n8n**

```bash
n8n
```

**Step 2 — Import the Workflow**

Import:

```
n8n/n8n_Personal_Assistant_Workflow_PUBLIC.json
```

into your n8n instance.

Then configure your own credentials and resource IDs.

**Step 3 — Start Streamlit**

```bash
streamlit run streamlit/app.py
```

The Streamlit application will open in your browser.

---

## 🔁 Example Workflow

**User Request**
```
Show me all my expenses.
```

**Processing**
```
Streamlit
    ↓
n8n Webhook
    ↓
AI Agent
    ↓
Get_Expenses Tool
    ↓
Google Sheets
    ↓
AI Agent
    ↓
Respond to Webhook
    ↓
Streamlit
```

**Result**
```
Here are your expenses:

• Food — 500
• Transport — 300
• Education — 1000
• Shopping — 750
```

---

## 📊 Data Storage

Google Sheets is used as the primary storage mechanism for expense records.

The expense structure includes fields such as:

- ID
- Date
- Expense Category
- Expense
- Remarks

The workflow supports adding, retrieving, and updating expense records.

---

## 🛡️ Security Considerations

The project follows basic security practices:

- API credentials are stored in n8n credentials.
- Sensitive credentials should not be committed to GitHub.
- Public workflow files use placeholders for private resource identifiers.
- `.env` files should be excluded from Git.
- OAuth credentials should be managed through n8n.

---

## 🚀 Future Improvements

Possible future improvements include:

- Multi-user authentication.
- Unique conversation sessions for each user.
- Voice input and voice responses.
- More advanced intent classification.
- Additional productivity tools.
- Database integration.
- File/document processing.
- WhatsApp or Telegram integration.
- User-specific permissions.
- Better error handling and monitoring.
- Deployment to a cloud platform.

---

## 🎓 Internship Project

This project was developed as an internship project at **Quantum Synergy Solutions** to demonstrate practical implementation of:

- Artificial Intelligence
- AI Agents
- Workflow Automation
- API Integration
- Cloud Services
- Data Storage
- Web Application Development

The project combines an interactive frontend with an AI-powered automation backend to create a practical personal productivity assistant.

---

## 👨‍💻 Author

**Zeeshan Ali**
BS Computer Science
AI / Machine Learning & Automation

---

## ⭐ Acknowledgements

Special thanks to Quantum Synergy Solutions and the mentors there for providing the opportunity to work on an AI-powered automation project.

---

## 📄 License

This project is intended for educational and internship purposes.