---
name: styled-email
description: Use when creating, drafting, or sending a styled marketing email or newsletter for dembrane — event invitations, feature or article updates, product announcements, privacy/policy notices. Produces on-brand, Outlook-safe HTML from a plain-language brief, ready to paste into MailerLite's Custom HTML editor. Fires on email, newsletter, campaign, invite, invitation, announce, mailerlite, send-out, or blast references.
---

## When to Use This

- "send an invite to ...", "draft a newsletter about ...", "announce ...", "email the list about ..."
- Any dembrane broadcast email that should look on-brand.

## When NOT to Use This

- One-to-one replies or transactional / product emails (those are app-side, not marketing).
- Internal updates that belong in Notion or tasks → use `task-management` / `resource-navigation`.

## What You Produce

A single self-contained HTML file, filled from `templates/master.html`, that the
user pastes into a MailerLite **Custom HTML** campaign. When the MailerLite MCP is
available in the session you may instead create the campaign as a draft (see Delivery).

## Workflow

1. **Read the source of truth first:** `templates/master.html` and `templates/brand-tokens.md`. Never invent brand colours, fonts, or footer facts; take them from there.
2. **Take the brief.** What is the email, the headline idea, the key facts, the call to action and its link. Ask only for what is genuinely missing (a working link; for an event, the date and place).
3. **Pick the type and accent.** Choose from the categorical accent map in brand-tokens. Set the accent bar AND the category tag to that colour together.
4. **Fill the template.** Headline, intro, optional BLOCKs (event details / featured article — delete the ones you do not need), CTA text and href, preheader, subject. Use the hosted hero illustration from brand-tokens or a real photo of people in dialogue.
5. **Apply voice and spell-check** everything, subject and preheader included.
6. **Render to verify.** Write the filled HTML to a working file and open it in a browser preview, then screenshot it. Check the top and the footer. Show the user before anything is sent.
7. **Deliver** (below).

## Voice

- dembrane is always lowercase, even at the start of a sentence or in a title.
- No em dashes. Aim for zero; one per email maximum.
- No violent or martial language ("arm", "weapon", "fight", "battle", "trojan horse"). The brand is hope, empowerment, care.
- Warm, grounded, human. Anchor in something real. Short sentences.

## Filling Rules

- Write **both** a subject line and a preheader. Preheader ~90 chars, warm, not a copy of the subject.
- The CTA button URL appears **twice** in the raw HTML: once in the Outlook `v:roundrect` and once in the normal `<a>`. Change **both**, or Outlook users get the old link. The article link appears once.
- Keep the footer merge tags `{$url_unsubscribe}` and `{$email}` exactly, and keep the address line.
- Never put a `--` run or a literal close-comment marker inside an HTML comment — it closes the comment early and leaks text into the email body. (Watch for this if you hand-edit comments.)
- Use straight characters, no em dash, to avoid both the brand rule and mojibake.

## Delivery

- **Default, works today:** output the final HTML and tell the user to create a campaign in MailerLite → Regular → Custom HTML → paste → set the subject → send a test to themselves → send. Click tracking is automatic; add UTM params if the link points to dembrane.com so PostHog attributes the clicks.
- **If MailerLite MCP tools are available in the session:** offer to create the campaign as a **draft** (never send) with this HTML, the subject, and the chosen group or segment. Always leave the final send to the user.

## Reference

`templates/master.html` — the canonical scaffold (table-based, Outlook-safe, mobile-responsive).
`templates/brand-tokens.md` — palette, type, shape, accent map, hosted assets, footer facts, merge tags.
