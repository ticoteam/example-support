# Triage a ticket

Triggered by a task that hands you one ticket, or a pass over everything new since the last one.
Budget 20 minutes for a pass, five for a single ticket. The outcome is a draft reply for every ticket
you can answer, a task for every one you cannot, and a note saying what the queue looked like.

## 1. Read the queue
    hub task show <id>

Read what arrived since the last pass and nothing older. If you cannot reach the source at all, say so
and stop: an unread queue and an empty queue must never read the same.

## 2. Sort each one
Every ticket is in exactly one bucket:

| Bucket | What it is | What you do |
|---|---|---|
| Answered before | `knowledge/answers.md` covers it | Draft the standing answer, adjusted to what they asked |
| Known issue | `knowledge/known-issues.md` names it | Draft the standing answer and add this ticket to the count |
| Needs a person | A refund, a credit, an exception, an angry customer, or anything in `knowledge/escalation.md` | One task on the person who owns it, with the ticket id and one line on what they decide |
| New | None of the above | Draft what you can, name what you do not know, and ask |

A ticket that is two of these is the more serious one. Anything about money, a deadline, a legal
matter, security, or safety goes to a person before you finish the pass.

## 3. Draft the reply
Follow `playbooks/write-a-reply.md`. One draft per ticket, on the task, never in the support tool.

## 4. Route what is left
    hub task create --owner <person> --parent <id>

One task per thing, with the ticket reference, what the customer could not do, and what you need
decided. Never two tasks for the same thing, and never a second escalation of something an open task
already names. If the same problem has now arrived three times, it is one line in
`knowledge/known-issues.md` and one task for whoever owns the fix.

## 5. Finish the pass
Commit, then `hub task update <id> --status done --note`: how many arrived, how many you drafted, how
many went to a person and to whom, and anything you could not read. Then add any answer you had to work
out from scratch to `knowledge/answers.md` with today's date.

## When the source is unreadable
Record which source, the exact refusal, and the window it covers. If it has failed twice in a row,
one line on the owner's task. Never report zero tickets for a source you could not open.
