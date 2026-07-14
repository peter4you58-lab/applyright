# ApplyRight — deploy & setup

## Files

| File | What it's for |
|---|---|
| `index.html` | The whole site. Nothing to build, no dependencies. |
| `CNAME` | Your custom domain. **Edit this** — it currently says `applyright.com`. |
| `robots.txt` | Lets Google index you. Update the sitemap URL to your real domain. |
| `sitemap.xml` | Same — update the domain. |
| `.nojekyll` | Stops GitHub Pages mangling the files. Leave it alone. |

## Deploy (same as petercloud9.online)

```bash
git init
git add .
git commit -m "ApplyRight site"
git branch -M main
git remote add origin https://github.com/peter4you58-lab/applyright.git
git push -u origin main
```

Then: repo → **Settings → Pages → Source: main / root**.
Add the domain under **Custom domain**, tick **Enforce HTTPS** once the cert issues (~15 min).

On Namecheap, Advanced DNS:
- `A` record `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- `CNAME` record `www` → `peter4you58-lab.github.io`

## Two things only you can do

**1. Buy the domain.** I can't purchase one. `applyright.com` is likely taken — check
Namecheap for `applyright.co`, `applyright.io`, `getapplyright.com`, `applyright.uk`.
Whatever you pick, update it in **three places**: `CNAME`, `robots.txt`, `sitemap.xml`.

**2. Create payment links.** These need your ID and bank details, so I can't generate them.
Until you do, the Buy buttons open WhatsApp with the order pre-written — you'll still make
sales from day one.

When you're ready, in `index.html` find `PAY_LINKS` and paste the URLs in:

```js
var PAY_LINKS = {
  single: 'https://paystack.com/pay/xxxx',
  ten:    'https://paystack.com/pay/xxxx',
  twenty: 'https://paystack.com/pay/xxxx'
};
```

The buttons switch to card checkout automatically. Nothing else changes.

**Which processor:** Stripe does not onboard Nigerian entities. Your realistic options for
charging UK/US/CA clients in USD are **Paystack** (Nigerian, takes international cards,
settles to your Naira account) or **Payoneer / Grey / Wise** for a USD receiving account
you invoice against. Paystack Payment Pages are the fastest — no code, made in the dashboard.

## Everything else that's already wired

- All four team contacts, tap-to-call + pre-filled WhatsApp
- Floating WhatsApp button on every screen
- CV intake form → `peter4you58@gmail.com`
- Review form → same inbox, with star rating
- Rating average recalculates from the `REVIEWS` array automatically

## Before you publish any success story

Get the client's **written** permission, and blur out names, emails and reference numbers
in any screenshot. Gwendolin's and Hermann's inboxes must not appear on this site — that's
other people's personal data, and publishing it without consent would be a real problem
for you under UK GDPR, since your clients are UK-based.

## Worth doing in week one

Swap the two forms to **Formspree** (free tier, no backend). Right now they open the
visitor's mail app — on mobile, a chunk of people bail at that step. Formspree keeps
the same HTML and puts submissions in a dashboard *and* your inbox.
