# example-support

An example [Tico](https://tico.team) bot that triages a support queue. It reads new tickets or
support mail, works out what each one is, drafts the reply, and routes what needs a person to the
person who owns it. It never answers a customer itself. Good looks like a draft a person sends with
one edit, and a queue where nothing sits unread.

The examples in this repository use a fictional company, Acme Co (`acme.example`). Replace them.

## What it needs

- Read access to the support queue (a helpdesk or a shared support mailbox). Read and draft only.
- Nothing else. It does not need send rights, refund rights, or write access to the helpdesk.

## What it must never do

- Reply to a customer, or change anything in the helpdesk.
- Promise a refund, credit, discount, or date.
- Copy a customer's personal details into a file.

## Add it to a Tico install

1. Create your own copy of this repository as `<your-org>/emp-support` (use the template button or
   `gh repo create --template ticoteam/example-support`).
2. Replace Acme details in `knowledge/company.md` and `knowledge/escalation.md`.
3. Tell BotOps: "set up a support bot from `<your-org>/emp-support`". It registers the bot, seeds
   routines, and runs `hub bot check support`. The bot stays `planned` until you activate it.
4. Put the credential for your helpdesk or mailbox on the machine that runs the bot, under the
   variable name declared in `employee.yaml`. Declaring access does not create it.

## Customize

- `knowledge/answers.md`: the standing answer to each recurring question. This is where the bot gets
  better; keep each answer dated and confirmed by a person.
- `knowledge/escalation.md`: what must reach a person immediately, and who.
- `knowledge/known-issues.md`: what is broken often enough that the answer is always the same.
- `employee.yaml`: runtime and model (left to your install), access, and an optional schedule once
  you have read a week of hand-run passes.

## Contributing

Pull requests welcome: better playbooks, sharper sorting rules, generic answers that apply to any
company. Keep contributions generic: no real company names, customers, domains or credentials; use
Acme. See `AGENT.md` for the rules a change must not break.

## License

Apache-2.0. See `LICENSE`.
