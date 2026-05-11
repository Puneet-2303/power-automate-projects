# Flow 1 — Email Attachment Saver

**Type:** Event-triggered (automated)
**Status:** Live
**Built with:** Step-by-step guidance (first flow)

---

## What It Does

Every time a new email arrives in Gmail with one or more attachments, this flow saves each attachment directly to a folder called "Email Attachments" in personal OneDrive. No manual downloading, no missed files.

The filter is specific — it only fires when the email has attachments AND lands in the inbox. Everything else gets ignored.

---

## Trigger

Gmail — new email arrives
Conditions: Has Attachments = Yes, Label = Inbox

---

## Actions

1. Apply to Each (loops through every attachment on the email)
2. Create file in OneDrive
   - Folder: /Email Attachments
   - File Name: Attachment Name (dynamic)
   - File Content: Attachment Content (dynamic)

---

## Connectors Used

- Gmail (personal account)
- OneDrive (personal)

---

## Test Result

Sent a test email with Overview.pdf attached. Flow ran in under 3 seconds. File appeared in the OneDrive Email Attachments folder immediately.

---

## What I Learned

- How to configure the Gmail trigger with attachment filtering
- Apply to Each loops for handling multiple files in a single email
- Mapping dynamic content (file name, file content) from trigger outputs
- Flow testing and debugging in the Power Automate designer

---

## Flow Structure

```
Gmail Trigger (new email, has attachments, inbox)
  └── Apply to Each (attachments)
        └── Create File (OneDrive)
```
