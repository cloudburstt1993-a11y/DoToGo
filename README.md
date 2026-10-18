# DoToGo

Vietnamese home catering in Grand Junction, Colorado. One static `index.html`,
no build step, served by GitHub Pages.

## Going live: the settings block

Everything that needs a real account is collected in one place — `const DOTOGO`
near the top of the script at the bottom of `index.html`. Fill in a value and
that part of the site switches on. Leave it empty and the page hides it rather
than showing a dead link or a phone number nobody answers.

| Setting | What it turns on | Where to get it |
|---|---|---|
| `phone` / `phoneDisplay` | Call-and-text links in the booking panel | — |
| `email` | Email links, and the fallback route for order requests | — |
| `orderFormEndpoint` | The order form actually delivers | formspree.io — make a form, paste its URL |
| `bookingEmbedUrl` | A real scheduler replaces the built-in calendar | Calendly, Acuity, Google Appointments or Square |
| `stripeDepositUrl` | "Pay the 50% deposit by card" button | Stripe → Payment Links |
| `paypalUrl` / `venmoUrl` | The peer-to-peer payment buttons | paypal.me / venmo.com |
| `social.Facebook` etc. | The footer social buttons | his profile URLs |

Two rules for the Stripe link:

1. It must be **DoToGo's own Stripe account** — his EIN, his bank. Payments for
   his food landing in someone else's merchant account is a mess at tax time and
   worse at chargeback time.
2. Use a **test-mode** link (`buy.stripe.com/test_…`) until his account is
   verified, so nothing takes real money before it is meant to.

## The built-in calendar is a stopgap

The calendar in the booking section keeps its reservations in `localStorage` —
the visitor's own browser. It cannot know which dates DoToGo has actually taken,
two customers can pick the same slot without either being told, and clearing
browser history erases it.

The wording on it says only what it can honestly claim: dates are "open to
request", and every booking is confirmed by phone or email before it is final.
Confirming a date also posts to the Google Apps Script in `confirmBooking()`,
which writes the event to a Google Calendar; if that call fails the customer is
now told to ring, instead of the failure being swallowed.

Setting `bookingEmbedUrl` removes this calendar entirely and embeds the real
scheduler in its place. That is the fix — the stopgap just avoids promising
availability nobody has checked.

## This is a pitch demo, and search engines are told so

`index.html` carries `<meta name="robots" content="noindex, nofollow">`. A demo
with placeholder prices and a test payment button has no business ranking for
"Vietnamese catering Grand Junction", and later it would compete with his real
site for the same searches. Flip that one tag to `index, follow` on launch day.

Crawling is deliberately left open in `robots.txt`. A `Disallow: /` would be
counterproductive here: a crawler that is blocked never reads the noindex tag,
and the URL can still end up listed from an external link.

Every URL — canonical, `og:url`, the two JSON-LD urls, `sitemap.xml` and
`robots.txt` — points at the GitHub Pages origin this actually lives on. When a
domain is registered, those are the five places to change.

## Still to fill in

Nothing in the markup. What is left needs accounts only DoToGo can open:
a Formspree form, a scheduling tool, a Stripe account, a domain, and his real
phone, email and social profiles. Each is one line in the settings block.
- Menu prices and the 10-guest minimum are in both the visible page and the
  `CateringBusiness` JSON-LD near the top of `<head>`. Change them in both.

## Artwork

All icons are inline SVG, stroked in `currentColor` so the `--gold` tokens drive
them. The hero is a goat — 2027 is the Year of the Goat (Năm Mùi), and Tết falls
on 6 February 2027. It is deliberately the opening-year campaign rather than the
identity: the artwork carries it, the wordmark stays neutral, so nothing has to
be unpicked in 2028.
