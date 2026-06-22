# dembrane styled email — how to send

You describe the email in plain language. Claude builds it on-brand and hands you
HTML to paste into MailerLite. No design tools, no editing code, nothing to break.

## One-time setup

1. Install the dembrane plugin in Claude Code (same as our other dembrane skills).
2. Make sure you have access to the dembrane MailerLite account.

## Sending an email (about five minutes)

1. Open Claude Code.
2. Describe what you want in plain language. The skill fires on its own; there is
   no command to remember. Include the topic, the key facts, and the link the
   button should go to. For example:

   > draft an invitation to our listening evening on 3 July at 18:00 in
   > 's-Hertogenbosch, the button should go to https://lu.ma/our-event

3. Claude builds it and shows you a preview screenshot. Read it. Ask for changes
   in plain language: "make the intro warmer", "swap the accent to amber",
   "drop the featured article block".
4. When you are happy, Claude gives you the final HTML and a subject line.
5. In MailerLite: **Create campaign → Regular → Custom HTML → paste**. Set the
   subject. **Send a test to yourself first.** Then send.

## What you do NOT touch

Colours, fonts, layout, the footer. They are locked to the brand. You only ever
describe content.

## The four email types

event invitation · featured article · product update · privacy/policy notice.
Claude picks the right accent colour for each one automatically.

## Rules of thumb

- Always send yourself a test before sending to the list.
- MailerLite adds the footer (your address + the unsubscribe link) automatically, so the email itself has none. Keep your MailerLite Company profile accurate so that footer is right.
- dembrane is always lowercase. No em dashes. Warm and human.

## Where this lives

The skill and the master template live in this repo under
`marketing/skills/styled-email/` (in the dembrane-public repo). The template is the single source of truth; if the
brand changes, we update `templates/master.html` and `templates/brand-tokens.md`
once and everyone gets it on the next pull.
