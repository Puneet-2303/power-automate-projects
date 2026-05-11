# Flow 3 — Leave Request Approval Workflow

**Type:** Event-triggered with human-in-the-loop approval
**Status:** Live
**Complexity:** Highest of the three flows
**Run time (tested):** 5 minutes 33 seconds (includes approval wait)

---

## What It Does

An employee sends an email with "LEAVE REQUEST" in the subject. The flow picks it up, creates an approval task assigned to a manager in Microsoft Approvals, waits for a response, then automatically replies to the original email with the outcome.

The reply is either "Your leave has been approved!" or "Your leave request was not approved" — depending on what the manager decided. Nobody writes the reply manually. The whole thing runs on its own once the manager clicks Approve or Reject.

---

## Why This One Is Different

Flows 1 and 2 follow a straight line — trigger, action, done. This one branches. The outcome of the approval changes what happens next, which meant learning how to wire up conditions, handle two separate reply paths, and reference the original email dynamically so the reply goes to the right person.

It also introduced Dataverse, which Power Automate provisions automatically for the Approvals connector. Getting that set up without breaking the flow took a few attempts.

---

## Trigger

Gmail — new email arrives
Subject filter: LEAVE REQUEST
From: puneetphalswal@gmail.com
Label: Inbox

---

## Actions

1. Start and wait for an approval
   - Approval Type: Approve/Reject (first to respond)
   - Title: Leave Approval
   - Assigned to: Puneet_fabric_user (Microsoft account)
   - Details: Email subject (dynamic)

2. Condition — IF Outcome = Approve

3. TRUE branch — Reply to email (V2)
   - Message ID: dynamic
   - Body: "Your leave has been approved!"

4. FALSE branch — Reply to email (V2)
   - Message ID: dynamic
   - Body: "Your leave request was not approved"

---

## Connectors Used

- Gmail (personal account)
- Microsoft Approvals
- Microsoft Dataverse (auto-provisioned)

---

## Test Result

Sent a LEAVE REQUEST email from test account. Approval notification arrived in the Microsoft Approvals portal within seconds. Clicked Approve. Reply email landed in the original inbox within the 5 minute 33 second window (approval wait included). Both the approve and reject paths were tested and confirmed working.

---

## What I Learned

- How the Approvals connector works and how to configure approval types
- Start and wait for approval — pausing the flow until a human responds
- Condition (IF/THEN/ELSE) branching based on dynamic output values
- Reply to email (V2) using dynamic Message ID to thread replies correctly
- Subject filter triggers on Gmail
- Dataverse provisioning and what it does behind the scenes
- Human-in-the-loop automation as a pattern for real business workflows

---

## Flow Structure

```
Gmail Trigger (subject: LEAVE REQUEST, inbox)
  └── Start and Wait for Approval (Microsoft Approvals)
        └── Condition: Outcome = Approve?
              ├── TRUE:  Reply to Email "Your leave has been approved!"
              └── FALSE: Reply to Email "Your leave request was not approved"
```
