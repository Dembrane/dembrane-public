# dembrane email brand tokens

Source of truth for the `styled-email` skill. The authoritative palette is the
2026 brand guidelines (down-to-earth, human, approachable). Never invent values;
read them from here.

## Palette
- Page background (body): charcoal / graphite `#2D2D2C`
- Content card: parchment `#F6F4F1`
- Text: graphite `#2D2D2C` (not pure black)
- Primary, links, button fill: royal blue `#4169E1`
- Footer text on the charcoal frame: parchment `#F6F4F1`
- Card sub-block (featured card): white `#FFFFFF`; hairline divider `#E6E3DF`

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
- Body weight 300. 500 for headlines and emphasis, 600 for labels and the wordmark.
- Web fonts render in Apple Mail, iOS, and the Gmail app. Outlook on Windows
  falls back to the Arial / Helvetica stack. That is expected and fine.

## Shape
- Sharp corners (border-radius 0) everywhere.
- Pill (`border-radius:9999px`) only on the primary button.

## Wordmark
- Text wordmark "dembrane" (lowercase), DM Sans 600, graphite. No logo image needed.

## Hosted assets (MailerLite file manager)
- Default hero illustration, real people in dialogue, brand colours:
  `https://storage.mlcdn.com/account_image/2452303/lPdZN8T1Gz68G4yCbHsfadLpgvNtDfDhaWvLjGbz.png`
- To add assets: upload in MailerLite → File manager, then paste the hosted URL here.

## Footer facts
- Org line: `dembrane · 's-Hertogenbosch, the Netherlands`
  (full registered address: Sint Janssingel 88, 's-Hertogenbosch)
- Social: LinkedIn.
- MailerLite merge tags, keep them exactly:
  - `{$email}` — the recipient's address
  - `{$url_unsubscribe}` — the unsubscribe link (MailerLite will not send without a working one)

## Sending domain
- Send marketing from a subdomain (e.g. `mail.dembrane.com`) with SPF, DKIM, and
  DMARC, so marketing volume never touches dembrane.com's core email reputation.
