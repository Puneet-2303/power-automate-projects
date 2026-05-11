# Power Automate — Cloud Flow Portfolio

Three live, tested automation flows built independently using Microsoft Power Automate. Each one solves a real problem — no tutorials followed end-to-end, no hand-holding. Just a trigger, a goal, and figuring it out.

The flows cover three different automation patterns: event-triggered, scheduled, and human-in-the-loop approval. All are currently live.

---

## Flows

### [Flow 1 — Email Attachment Saver](./flow-1-email-attachment-automation)
Watches Gmail for incoming emails with attachments and saves them automatically to a OneDrive folder. No manual downloads needed.

**Tools:** Gmail, OneDrive (Personal), Apply to Each loop, dynamic content

---

### [Flow 2 — Daily Reminder Scheduler](./flow-2-daily-reminder-scheduler)
Sends a personalised daily email every morning at 8:00 AM with today's date dynamically inserted. Built without any step-by-step guide — the first flow I built completely on my own.

**Tools:** Gmail, Recurrence trigger, formatDateTime(), concat(), utcNow()

---

### [Flow 3 — Leave Request Approval Workflow](./flow-3-leave-approval-workflow)
The most complex of the three. An employee emails a leave request, it gets routed to a manager via Microsoft Approvals, and the employee receives an automated reply with the outcome — approved or rejected — without anyone manually writing a response.

**Tools:** Gmail, Microsoft Approvals, Dataverse, Condition (IF/THEN/ELSE), dynamic content

---

## Skills Covered

| Concept | Learned In |
|---|---|
| Event-triggered flows | Flow 1 |
| Apply to Each loops | Flow 1 |
| Scheduled recurrence | Flow 2 |
| Date/time expressions | Flow 2 |
| Approval connectors | Flow 3 |
| Conditional branching | Flow 3 |
| Dataverse provisioning | Flow 3 |
| Human-in-the-loop automation | Flow 3 |

---

## Why I Built These

I am preparing for a Systems Analyst role that requires hands-on Power Automate experience. Rather than just reading documentation, I built real flows that actually run. Flow 3 in particular — the approval workflow — taught me how conditional logic, dynamic content, and multi-step connectors fit together in practice, which is hard to get from theory alone.
