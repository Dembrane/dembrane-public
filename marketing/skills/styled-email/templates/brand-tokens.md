# dembrane email brand tokens

Source of truth for the `styled-email` skill. The authoritative palette is the
2026 brand guidelines (down-to-earth, human, approachable). Never invent values;
read them from here.

## Palette
- Page background (body): parchment `#F6F4F1`
- Content card: white `#FFFFFF`
- Text: graphite `#2D2D2C` (not pure black)
- Primary, links, button fill: royal blue `#4169E1`
- Featured sub-block: parchment `#F6F4F1` fill with a `#E6E3DF` hairline border (so it reads on the white card); hairline dividers `#E6E3DF`

**Light page on purpose.** Do not use a dark/charcoal page background. MailerLite
force-appends a required footer in its own dark text (see Footer facts); on a dark
page that footer and its Unsubscribe link go illegible, and dark-mode clients
mangle any `<style>` recolor (they recolor the link underline but not the text).
A light page keeps the appended footer legible in every client, Outlook included.

## Categorical accents (decorative, NEVER semantic)
Set the accent bar AND the category tag to the same colour per email type.
Green is not "success", amber is not "warning". They only signal the type.

| Email type        | Accent      | Hex       |
|-------------------|-------------|-----------|
| event invitation  | cyan        | `#00FFFF` |
| featured article  | green       | `#1EFFA1` |
| product update    | royal blue  | `#4169E1` |
| privacy / policy  | amber       | `#FFD166` |

Extended palette (use sparingly): pink `#FFC2FF`, yellow `#F4FF81`, coral `#FF9AA2`.

## Type
- DM Sans (Google Fonts, loaded via the `<link>` in master.html).
- Body weight 400 (300 reads too thin in the inbox). 500 for headlines and emphasis, 600 for labels and the category tag.
- Web fonts render in Apple Mail, iOS, and the Gmail app. Outlook on Windows
  falls back to the Arial / Helvetica stack. That is expected and fine.

## Shape
- Sharp corners (border-radius 0) everywhere.
- Pill (`border-radius:9999px`) only on the primary button.

## Logo
- Use the hosted logo image in the header (mark + wordmark), not a text wordmark:
  `https://storage.mlcdn.com/account_image/2452303/2Y8IRvNBEydCjAdDlQ8wpnSTkEVo7Fa2kEgJ3wkj.png`
  (native 293x60; display at width 146 / height 30). Sits top-left, category tag top-right.

## Hosted assets (MailerLite file manager)
- Logo (see above).
- Default hero illustration, real people in dialogue, brand colours:
  `https://storage.mlcdn.com/account_image/2452303/lPdZN8T1Gz68G4yCbHsfadLpgvNtDfDhaWvLjGbz.png`
- To add assets: MailerLite left sidebar > File manager (not a `/account/*` URL), upload, then paste the hosted `storage.mlcdn.com/account_image/2452303/...` URL here.

## Footer facts
- **Do not build your own footer.** MailerLite appends a required footer to every
  Custom HTML campaign: company name + address (from Account settings > Company
  profile), a permission line, the Unsubscribe link, and on free/trial a "Sent by
  MailerLite" badge. Adding your own duplicates it and reintroduces the dark-text
  problem. The merge tags `{$email}` / `{$url_unsubscribe}` are handled by that
  appended footer, you do not place them yourself.
- Registered address shown there: dembrane, Sint Janssingel 88, 's-Hertogenbosch, the Netherlands. Keep MailerLite's Company profile accurate so the footer is correct.
- Social: LinkedIn.

## Sending domain
- The sending domain is the root **`dembrane.com`**, authenticated in MailerLite
  (status "Authenticated", done June 2026 via MailerLite's Entri auto-config into
  Cloudflare). NOT a `mail.` subdomain (that host is taken by Google). Send `from`
  any `@dembrane.com` address. DKIM currently signs on `mlsend.com`; full
  `d=dembrane.com` alignment would need MailerLite's paid custom-domain option.
