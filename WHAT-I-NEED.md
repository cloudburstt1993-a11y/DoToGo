# What I need to finish DoToGo

Everything below is something I can't get myself — it's his, or it's a decision,
or it needs an account in his name. Each item says the format I need it in, so a
one-line answer is enough.

Site as it stands: https://cloudburstt1993-a11y.github.io/DoToGo/
Settings block that consumes most of this: `const DOTOGO` near the bottom of `index.html`.

---

## 1. Blocking — answer before anything else

### Can he legally cater this menu from a home kitchen in Mesa County?

This decides whether the words "home kitchen" stay on the page, and it may
change his pricing. **He needs to ring Mesa County Public Health and ask**, not
guess, and not take my word for it.

The specific question to ask them:

> "I want to cater Vietnamese food for private events — 10+ guests, pickup and
> local delivery. The menu includes phở with beef, bánh mì with seasoned meat,
> and cơm tấm with pork chop. I'd be cooking at home. What licence do I need,
> and can I do this from a home kitchen or do I need a commissary?"

Why it matters, from the research:

- Colorado's **Cottage Foods Act** historically covered only shelf-stable food.
  Phở is not shelf-stable.
- **HB26-1033 (the "Tamale Act")**, signed 4 June 2026, extends it to
  refrigerated time/temperature-controlled foods — but requires registration
  with CDPHE and a registration number *before selling*, food-handling
  training, and transport **no more than once, under two hours**. Crucially,
  **meat must still meet federal inspection requirements**; state law can't
  override that.
- Sources disagree on the effective date (1 January vs. certain meat/TCS foods
  not until **2027**), and the Act **sunsets 1 September 2028**.
- Separately, cottage food is a *home point-of-sale* permission. **Catering an
  event is a different activity** that usually needs a retail food
  establishment licence and a commissary kitchen.

**What I need back:** what the county says, in their words. If the answer is
"commissary required", tell me — "home kitchen" comes off every page, the
About section gets rewritten, and the prices probably need to go up.

---

## 2. Contact details

Without these the phone and email rows stay hidden, which is the honest
default but not a finished site.

| I need | Format | Goes to |
|---|---|---|
| Phone | `+19705550123` and `(970) 555-0123` | `phone`, `phoneDisplay` |
| Email | `orders@…` | `email` |
| Does he want calls, texts, or both? | one line | the copy next to the number |

---

## 3. Accounts he has to create

I can't open these — they need his name, his bank, his verification.

| Account | What I need back | Turns on |
|---|---|---|
| **Formspree** (free tier fine) | the form URL `https://formspree.io/f/xxxxxxxx` | orders actually deliver |
| **Scheduler** — Calendly, Acuity, Google Appointments or Square | the booking URL | replaces the placeholder calendar |
| **Stripe** — **his own account**, his EIN, his bank | a **test-mode** Payment Link `https://buy.stripe.com/test_…` | the 50% deposit button |
| PayPal / Venmo (optional) | the profile URLs | those buttons |
| Facebook / Instagram / TikTok / Snapchat | the profile URLs | the footer row |

Two Stripe rules: it must be **his** account, not Bookcliff Web's — payments
for his food landing in your merchant account is a mess at tax time and worse
at chargeback time. And keep it **test mode** until the site is real, because
the page is public and a stranger could otherwise pay a real deposit for food
nobody is cooking.

---

## 4. Business facts the site currently can't answer

Every one of these is a question a customer will ask. The page scores zero on
all of them right now, and every catering site I looked at carries them.

- **Service radius** — how many miles from Grand Junction, and is there a
  delivery fee or a minimum beyond that?
- **Lead time** — the page says "48-hr advance notice preferred". Preferred is
  not a policy. What's the real minimum, and is it longer for big orders?
  (Comparable caterers run 3–7 working days.)
- **Cancellation and refund** — if someone cancels a week out, what happens to
  the 50% deposit? Three days out? Day of?
- **Allergens and dietary** — can he do vegetarian or gluten-free? Is the
  kitchen shared with shellfish, peanuts, fish sauce? The safe pattern is to
  state what he can accommodate and route the rest to a conversation, never to
  promise "safe for".
- **Delivery vs. pickup** — does he deliver and set up, or drop and go?
- **Payment on the balance** — due when, paid how?

---

## 5. Domain

Nothing is registered. Right now every URL points at the GitHub Pages address,
which is correct but temporary.

- Does he want `dotogo.com`? Is it available? Who buys it — him or you?
- Until it exists, the demo stays on the Pages URL and stays `noindex`.

---

## 6. Content I won't invent

- **A paragraph about him** — who's cooking, why Vietnamese, how long. The
  About section is currently generic and it's the second thing people read.
- **Real photos of real food.** This is the single biggest upgrade left. The
  line-art icons are good placeholders; they are not photographs of his phở.
  Even phone photos in daylight beat icons.
- **Reviews** — only real ones, with permission. I will not write testimonials.

---

## Order I'd work in

1. Licensing answer (may rewrite the page)
2. Phone + email (makes the site usable today)
3. Formspree (orders stop vanishing)
4. The six business facts (section 4) — I can write these into the page in one pass
5. Scheduler + Stripe test link
6. Photos
7. Domain, then flip `noindex` and go live

Send me any item and I'll wire it in and redeploy. Items 2–5 are each one line
in the settings block.
