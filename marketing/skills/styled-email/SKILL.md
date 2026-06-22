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

1. **Read the source of truth first:** `templates/master.html` and `templates/brand-tokens.md`. Never invent brand colours, fonts, the logo URL, or footer facts; take them from there.
2. **Take the brief.** What is the email, the headline idea, the key facts, the call to action and its link. Ask only for what is genuinely missing (a working link; for an event, the date and place).
3. **Pick the type and accent.** Choose from the categorical accent map in brand-tokens. Set the accent bar AND the category tag to that colour together.
4. **Fill the template.** Logo stays. Headline, intro, optional BLOCKs (event details / featured article — delete the ones you do not need), CTA text and href, preheader, subject. Use the hosted hero illustration from brand-tokens or a real photo of people in dialogue. Do NOT add a footer.
5. **Apply voice and spell-check** everything, subject and preheader included.
6. **Render to verify.** Write the filled HTML to a working file and open it in a browser preview, then screenshot it. Check the top (logo, headline). The MailerLite footer is appended at send and is NOT in your local file, so when using the MCP also open the campaign's `preview_url` and check the footer renders dark-on-light and legible. Show the user before anything is sent.
7. **Deliver** (below).

## Voice

- dembrane is always lowercase, even at the start of a sentence or in a title.
- No em dashes. Aim for zero; one per email maximum.
- No violent or martial language ("arm", "weapon", "fight", "battle", "trojan horse"). The brand is hope, empowerment, care.
- Warm, grounded, human. Anchor in something real. Short sentences.

## Filling Rules

- Write **both** a subject line and a preheader. Preheader ~90 chars, warm, not a copy of the subject.
- **Keep the page background light** (parchment, white card). Do not switch to a dark/charcoal frame — it breaks the appended footer (see brand-tokens).
- **Do NOT add a footer or an unsubscribe link.** MailerLite appends the required footer (company info, permission line, Unsubscribe, Sent-by badge). Adding your own duplicates it.
- The CTA button URL appears **twice** in the raw HTML: once in the Outlook `v:roundrect` and once in the normal `<a>`. Change **both**, or Outlook users get the old link. The article link appears once.
- Never put a `--` run or a literal close-comment marker inside an HTML comment — it closes the comment early and leaks text into the email body.
- Use straight characters, no em dash, to avoid both the brand rule and mojibake.

## Delivery

- **Default, works today:** output the final HTML and tell the user to create a campaign in MailerLite → Regular → Custom HTML → paste → set the subject → send a test to themselves → send. Click tracking is automatic; add UTM params if the link points to dembrane.com so PostHog attributes the clicks.
- **If MailerLite MCP tools are available in the session**, create the campaign as a draft and always leave the final send to the user. Notes:
  - Send `from` an `@dembrane.com` address (the domain is authenticated).
  - To test, target a one-person group, never "all subscribers". Flow: `create_group` → `add_subscriber(groups:[id])` → `create_campaign(type:regular, groups:[id], content, from, subject)` → `schedule_campaign(delivery:"instant")`.
  - **`update_campaign` wipes the audience** — it has no `groups` param and silently resets recipients to ALL active subscribers. To change content while keeping a group, **delete and recreate** with `create_campaign`. Always re-check `recipients_count` before any send.

## Common Mistakes

- **Dark page background** → the appended footer + Unsubscribe link go dark-on-dark (illegible, non-compliant) and dark-mode clients mangle CSS recolor attempts. Keep it light.
- **Adding your own footer/unsubscribe** → duplicates MailerLite's appended one.
- **Editing a live campaign with `update_campaign`** → blows the audience up to everyone. Delete + recreate instead.
- **Trusting the local render for the footer** → the footer only exists in MailerLite's render; check `preview_url`.

## Reference

`templates/master.html` — the canonical scaffold (light layout, table-based, Outlook-safe, mobile-responsive).
`templates/brand-tokens.md` — palette, type, shape, logo, hosted assets, footer facts, sending domain, merge tags.
