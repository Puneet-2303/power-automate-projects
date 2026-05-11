# Flow 2 — Daily Reminder Scheduler

**Type:** Scheduled (time-triggered)
**Status:** Live
**Built:** Independently, without step-by-step guidance

---

## What It Does

Every morning at 8:00 AM, this flow sends a personalised reminder email with today's date automatically inserted into the subject line. No manual action needed — it just runs.

The subject updates itself daily using Power Automate expressions, so every email looks like: "Daily Reminder — Monday, 11 May 2026". The body contains a custom task list written by me.

This was the first flow I built without following a guide. I worked out the recurrence trigger, the expression syntax, and the dynamic subject line through trial and error.

---

## Trigger

Recurrence
- Start: Today's date
- Repeat every: 1 Day
- At: 8:00 AM

---

## Actions

1. Gmail — Send Email
   - To: puneetphalswal33@gmail.com
   - Subject: concat('Daily Reminder — ', formatDateTime(utcNow(), 'dddd dd MMMM yyyy'))
   - Body: Custom daily task list

---

## Connectors Used

- Gmail (personal account)

---

## What I Learned

- Recurrence triggers and how to set start time and repeat interval
- formatDateTime() to convert UTC time into a readable date string
- utcNow() to capture the current timestamp at runtime
- concat() to join static text with dynamic expressions
- Writing dynamic subject lines without hardcoding any dates

---

## Why This One Matters

It looks simple on the surface. But building it without guidance forced me to actually understand how Power Automate expressions work rather than just copying them. The expression language is closer to writing formulas than drag-and-drop, and getting comfortable with it here made Flow 3 much more manageable.

---

## Flow Structure

```
Recurrence Trigger (8:00 AM daily)
  └── Send Email (Gmail)
        Subject: concat() + formatDateTime() + utcNow()
        Body: Custom task list
```
