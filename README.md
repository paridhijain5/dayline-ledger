# Dayline

**Every day counted. Every rupee on record.**

Dayline is a small web app for domestic and daily-wage workers and the people who employ them. It keeps a day-by-day record of attendance and advances, works out what is owed, and produces one clear statement that can be shared.

- Built for EvoHacks 2 (theme: Projects for Social Good)

## The problem
Many domestic workers are paid in cash, with no written record. At the end of the month, what is owed often depends on memory: how many days were missed, how much was taken in advance. That leads to arguments, and the worker usually has less power in them.

## What Dayline does
- Enter the worker's name, the agreed monthly pay and how many paid leave days are allowed.
- Tap a day on the calendar to mark it as worked, leave or paid off.
- Record advances with a note.
- Dayline calculates the daily rate, deducts only the leave beyond the allowance, subtracts advances and shows the amount due.
- If advances are larger than the pay, the amount due stops at ₹0. It never goes negative.
- It writes a plain statement of every number, which can be copied, shared on WhatsApp or read aloud.
- A "Sample month" button fills in an example so you can try it in seconds.
- Hindi language support *(keep only if it works)*.
- Light and dark mode *(keep only if it works)*.
- Data stays in the browser and nothing is uploaded *(keep only if saving after refresh works)*.

## How the calculation works
```
daily rate   = monthly pay / days in the month
extra leave  = max(0, leave days - paid leave allowed)
deduction    = extra leave x daily rate
amount due   = max(0, monthly pay - deduction - advances)
```
Unmarked days are treated as paid. Only recorded leave beyond the allowance is deducted.

Example (October 2026, 31 days): pay ₹12,000, daily rate ₹387, 3 leave days with 2 allowed, so 1 extra day is deducted (₹387). With a ₹1,500 advance the amount due is **₹10,113**.

## Accessibility
- Large tap targets and visible focus states
- Day status shown with colour and a symbol, so colour is never the only signal
- Statement can be read aloud with the Web Speech API
- Works on phones, which is how most workers and employers will use it

## Tech stack
- Next.js (React) with TypeScript
- Tailwind CSS and shadcn/ui components
- Web Speech API for read-aloud
- No backend and no database. All calculations run in the browser.
- Deployed on Vercel

## Run it locally
You need Node.js and pnpm.
```bash
pnpm install
pnpm dev
```
Then open http://localhost:3000

## Project structure
```
app/          pages and layout
components/   UI components
lib/          helper functions (calculation and formatting)
public/       static assets
```

## Built during the event
Everything was designed and built during EvoHacks 2. No existing code was reused. I used AI tools (Claude and v0) to help with code and design iterations, and I tested the maths and chose the final version myself.

## Limitations and next steps
- It is a personal record and not a legal document.
- There is no cloud sync or backup yet.
- Next: shared statements for worker and employer, more regional languages, and PDF export.

## Author
Paridhi Jain
