# 💸 AI Expense Splitter — Splitwise Clone

An AI-powered full-stack expense splitting app built with **Next.js 15**, **Convex**, **Gemini AI**, **Clerk**, and **Inngest**. Split bills with friends, track group balances in real-time, and receive personalized monthly spending insights delivered straight to your inbox.

---

## ✨ Features

- 🔐 **Authentication** — Email, password & social login via Clerk
- 👥 **Group Management** — Create groups, add contacts, and manage members
- 💰 **Expense Tracking** — Add, split, and categorize expenses in real-time
- ⚖️ **Balance Summary** — Live balance tracking across all groups and contacts
- ✅ **Settlements** — Mark debts as settled and keep records updated
- 🤖 **AI Spending Insights** — Gemini AI analyzes monthly expenses and generates personalized financial reports
- 📧 **Automated Email Reports** — Inngest background jobs deliver AI-generated insights to users every month
- 📱 **Fully Responsive** — Works seamlessly across all screen sizes

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Next.js 15, React 19, Tailwind CSS, Shadcn UI |
| Backend / Database | Convex (real-time reactive DB) |
| Authentication | Clerk |
| AI | Google Gemini AI |
| Background Jobs | Inngest |
| Email | Resend |
| Deployment | Vercel |

---

## 📁 Project Structure

```
├── app/
│   ├── (auth)/          # Sign in / Sign up pages
│   └── (main)/
│       ├── dashboard/   # Balance summary & overview
│       ├── contacts/    # Friends & group management
│       └── expenses/    # Expense tracking & settlements
├── convex/              # Backend functions & DB schema
├── lib/
│   └── inngest/         # Background job pipeline (AI insights)
├── components/          # Reusable UI components
└── public/              # Static assets
```

---

## ⚙️ Getting Started

### Prerequisites

- Node.js 18+
- Accounts on: [Convex](https://convex.dev), [Clerk](https://clerk.com), [Inngest](https://inngest.com), [Resend](https://resend.com), [Google AI Studio](https://aistudio.google.com)

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/ai-splitwise-clone.git
cd ai-splitwise-clone

# Install dependencies
npm install
```

### Environment Variables

Create a `.env.local` file in the root directory:

```env
# Clerk
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_...
CLERK_SECRET_KEY=sk_test_...

# Convex
NEXT_PUBLIC_CONVEX_URL=https://...convex.cloud
CONVEX_DEPLOYMENT=dev

# Gemini AI
GEMINI_API_KEY=AIza...

# Inngest
INNGEST_EVENT_KEY=...
INNGEST_SIGNING_KEY=...

# Resend
RESEND_API_KEY=re_...

# App
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

### Running Locally

```bash
# Start Next.js dev server
npm run dev

# Start Convex backend (in a new terminal)
npx convex dev

# Start Inngest dev server (in a new terminal)
npx inngest-cli@latest dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 🤖 How the AI Pipeline Works

1. **Inngest cron job** triggers at the start of each month
2. Fetches all users who had expenses in the previous month via **Convex**
3. Sends each user's spending data (category breakdowns, totals) to **Gemini AI**
4. Gemini returns a personalized financial analysis with actionable suggestions
5. **Resend** delivers the formatted HTML report to the user's email

---
