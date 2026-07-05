# Email Builder

**Nautilus Engineering · Full-Stack Engineer Take-Home**

## Getting Started

### Option A: Fork (recommended)

1. Click **Fork** on this repo to create your own copy
2. Clone your fork locally:
   ```bash
   git clone https://github.com/<your-username>/nautilus-email-builder.git
   cd nautilus-email-builder
   ```

### Option B: Clone directly

```bash
git clone https://github.com/xxxoooxoxo/nautilus-email-builder.git
cd nautilus-email-builder
```

> **⚠️ Important:** Do **not** push to this repository. Work on your own fork or a local copy only. If you cloned directly, remove the remote before starting:
> ```bash
> git remote remove origin
> ```

---

## The Problem

Build a visual email builder. Users compose emails by dragging and dropping components, preview the result, send it, or schedule it for later.

The scaffold includes the tech stack and dependencies — no UI or features are implemented. That's your job.

**Time:** plan for 4–6 focused hours. Submit within **72 hours** of receiving access.

## Tech Stack

Already installed in the scaffold. Use them.

| Technology | Purpose |
|---|---|
| Next.js 15+ (App Router) | Application framework |
| TypeScript (strict) | Type safety |
| React Email | Email-safe components |
| Resend | Email delivery |
| Puck Editor | Drag & drop builder |
| Temporal | Durable scheduling |

## Running Locally

```bash
npm install
cp .env.example .env.local   # then fill in your values
```

| Variable | Description | Required |
|---|---|---|
| `RESEND_API_KEY` | API key from [resend.com](https://resend.com) | Yes |
| `RESEND_FROM_EMAIL` | Sender address (default: `onboarding@resend.dev`) | No |
| `TEMPORAL_ADDRESS` | Temporal server address (default: `localhost:7233`) | No |

Install the Temporal CLI ([macOS](https://docs.temporal.io/cli#install): `brew install temporal` · Windows: `winget install Temporal.TemporalCLI` · Linux: `curl -sSf https://temporal.download/cli.sh | sh`), then:

```bash
temporal server start-dev   # terminal 1
npm run dev                 # terminal 2
```

The scaffold has no worker process — writing one (and a script to run it, e.g. `npm run worker`) is part of the scheduling work.

## Requirements

Your email builder must:

- **Drag-and-drop composition** — Users build emails by dragging components onto a canvas. Which components you support and how you expose their properties is up to you.
- **Truthful preview** — Users see what their email will look like before sending. The preview must be the same HTML that Resend receives. How your architecture makes drift between them impossible is the most interesting decision in this assignment — we'll ask you to explain it.
- **Send** — Emails are delivered via Resend. The user provides a recipient and subject, and sees clear success/failure feedback.
- **Durable scheduling** — Users can schedule an email for a future date/time via Temporal, see their scheduled emails, and cancel them. Cancellation must actually work, end to end.
- **At least one meaningful test** — covering your editor-state → email-HTML serialization. More are welcome; one is required.

Beyond these, **add at least two features that aren't listed here** — things you believe should exist in a product like this. What you choose to add, and how well you choose it, matters as much as how you build it.

## How We Verify

We'd rather tell you exactly how we review than have you guess:

1. **We diff your write-up against your code.** A missing feature costs you little. A claimed feature that doesn't exist ends the review.
2. **We run the kill test.** We schedule an email, stop every process, restart them, and expect the email to still arrive. `setTimeout`, in-memory queues, and flat files won't survive this.
3. **We read your git history.** Incremental commits with real messages, timestamps consistent with your write-up. Ten rough commits beat one 10,000-line drop.
4. **We use the app** the way a customer would. Sensible defaults, empty states, error states, and small details count.
5. **In the follow-up interview, you'll extend your own code live** — for example, adding a new component end to end. Build something you can navigate without a map.

## Using AI

We expect you to use Claude Code — it's how we work at Nautilus, and using it well is a skill we're hiring for. Using it well means reading what it produces: pruning dead code and unused dependencies, catching its mistakes, and shipping only what you understand. Your AI Debrief (below) and the live follow-up are where that shows.

## Write-Up

Replace this README's content with your write-up. Use exactly these sections:

1. **Setup** — how to run it, including the worker.
2. **Environment variables** — every variable your code reads, and no others.
3. **Architecture** — how editor state becomes sent email, and what guarantees preview and delivery can't drift.
4. **Decisions & tradeoffs** — what you chose, what you rejected, and why. Including your two added features and why they earn their place.
5. **Known limitations** — what's cut, broken, or fragile. Being straight here is worth more than you think; see How We Verify #1.
6. **AI Debrief** — what the AI got wrong and what you changed. "Nothing" is not a credible answer.
7. **Time** — hours spent, roughly broken down.

## Submission

- **Private GitHub repo** shared with `alihsareini@live.com`, within 72 hours.
- **Proof it works** (required): a deployed demo (Vercel preferred — scheduling may be excluded there, since Temporal is hard to host serverless) **or** a short screen recording showing the full loop: compose → preview → send → schedule → cancel.

## Resources

- [Next.js Docs](https://nextjs.org/docs)
- [Puck Editor](https://puckeditor.com)
- [React Email](https://react.email)
- [Resend](https://resend.com)
- [Temporal](https://temporal.io)

Questions? Reach out — we'd rather you ask than guess.
