WorkFlow
An AI-powered, role-based employee task & accountability platform.
Most small and mid-sized teams run on spreadsheets, chat messages, and verbal instructions — so no one really knows who is doing what, whether it was actually done, or who changed what and when. WorkFlow replaces that mess with a single, structured, transparent system where every task, update, and outcome is tracked and verifiable, with an AI layer that verifies work and keeps managers informed automatically.

What It Does
For managers

Assign tasks with clear deadlines and priority levels
Track real-time progress across the whole team from one dashboard
See overdue tasks flagged automatically
Review the daily work logs each employee submits

For employees

See exactly what's assigned, with unambiguous priorities and deadlines
Log daily work against each task — no room for bluffing
One clear view of all their responsibilities

Built-in accountability

Every status change, log, and update is recorded with a timestamp and the name of who made it — a complete, tamper-resistant audit trail. Nothing can be quietly undone or hidden.

AI Features (the differentiators)

AI Work-Log Verification — When an employee submits a daily log, an LLM compares it against the assigned task and returns a verdict (genuine / vague / mismatch) with a confidence signal and a one-line reason. This directly attacks the bluffing problem: managers can instantly tell real progress from filler.
"Where's My Team?" Summary — With one click, the LLM turns the entire task table into a plain-English briefing: who's behind, what's at risk, which deadlines are slipping, and who's quietly overperforming. This replaces the time managers normally lose to manual follow-ups.

Every AI output is advisory and visible to a human — it informs decisions, it doesn't silently change records.

Why Not Trello / Jira?
WorkFlow is built specifically for non-technical teams in small businesses — usable on day one, focused on accountability rather than just task tracking. Daily work logs plus a full timestamped audit trail mean there's always proof of work done, and the AI verifies that proof automatically — something generic tools don't do.

Tech Stack
LayerTechnologyFrameworkNext.js (App Router)LanguageTypeScriptStylingTailwind CSSAIAnthropic Claude via @anthropic-ai/sdk, called from a server-side API routeStateReact Context + reducer, persisted to localStorage

What's mocked vs. real: This is a hackathon prototype. Authentication and the database are mocked — users, tasks, and logs are seeded in-memory and persisted to the browser's localStorage (no backend DB). The AI features are fully live and call the Anthropic API in real time. The architecture is intentionally structured so a real database and auth layer can be swapped in without rewriting the UI.


Running Locally
Prerequisites

Node.js 18+ and npm
An Anthropic API key — get one at console.anthropic.com

Setup
bash# 1. Clone the repo
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>/workflow

# 2. Install dependencies
npm install

# 3. Add your API key
#    Copy the example env file and paste your key into it
cp .env.example .env.local
#    then open .env.local and set:
#    ANTHROPIC_API_KEY=sk-ant-your-key-here

# 4. Start the dev server
npm run dev
Open http://localhost:3000 in your browser.

The app reads the API key only at startup, so if you add or change the key while the server is running, stop it (Ctrl+C) and run npm run dev again.

Trying It Out

Use the role switcher at the top to move between the Manager and Employee views.
As an employee, update a task's status and submit a daily work log — watch the AI return a verdict.
As the manager, click "Where's My Team?" to get an instant AI briefing on the whole team.


Project Structure
workflow/
├─ src/
│  ├─ app/
│  │  ├─ page.tsx              # main app shell + role switch
│  │  └─ api/ai/route.ts       # server-side LLM route (verify + summary)
│  ├─ components/              # dashboard, task table, work-log form, audit trail, etc.
│  └─ lib/
│     ├─ store.tsx             # Context + reducer + localStorage persistence
│     ├─ seed.ts               # mock users, tasks, logs
│     └─ types.ts              # shared TypeScript types
└─ README.md

Target Users
Small to mid-sized businesses across any industry — manufacturing, retail, real estate, logistics, finance — where teams of 5 to 200 people are managed manually today.
