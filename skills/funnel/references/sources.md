# Where the evidence is, and how to read it

Read the section you need. Every technique here only reads what the company serves to any visitor.

- [The site and every link](#the-site-and-every-link)
- [Login and sign-up pages](#login-and-sign-up-pages)
- [The code the site serves](#the-code-the-site-serves)
- [Ad libraries](#ad-libraries)
- [Domain, DNS and hosting](#domain-dns-and-hosting)
- [Reviews](#reviews)
- [The people behind it](#the-people-behind-it)
- [Company records, archives and size](#company-records-archives-and-size)
- [Reading what you find](#reading-what-you-find)

## The site and every link

- **Homepage:** title and meta description often state the whole offer in one line ("Meal plans delivered weekly, from £4 a meal"). Note the main call to action and where it points: usually the start of the funnel.
- **Every link, one hop.** List every link on the homepage (in a browser: `[...document.querySelectorAll('a')].map(a => a.innerText.trim() + ' -> ' + a.href)`), then open each one on the same site. Many buttons pointing to one place (e.g. `/apply`) tells you the funnel's front door.
- **`/sitemap.xml` and `/robots.txt`:** pages that aren't linked from the homepage: old landing pages, partner and affiliate programmes, careers (salaries and roles show team size and costs), "welcome back" and "thank you" pages that belong to the funnel. Open each one; some redirect home (note that), most show something.
- **Terms and privacy pages:** terms usually state the plans, prices, billing, trial and cancellation rules exactly; privacy pages list suppliers (payment, email, analytics, hosting).
- **Footer:** company name, registration or VAT number, address, other brands.
- **Pages that come back empty** when fetched are built in the browser: open them in a browser, or find their text in the code (below).

## Login and sign-up pages

Open them; never type into them.

- **Where it points:** a different domain or brand behind "Log in" is often the real company or the platform they're built on (a white-label tool, a parent agency, a sister brand).
- **What loads:** scripts on the login page show affiliate tracking (e.g. Rewardful, FirstPromoter), analytics and payment providers.
- **The app's own code** is served to everyone, logged in or not, just like the site's. Download and search it the same way as the site's (next section): route names describe the onboarding steps, the checkout, the upsells and the cancellation flow in order.

## The code the site serves

Most modern sites ship their pages as JavaScript files. Every visitor downloads them, so they're public, and they often hold every page's text, including pages you'd only see after signing up.

1. **Collect the files.** Fetch the page's HTML and list its `<script src>` files (and `<link rel="modulepreload">`) on the same site. Fetch each one into `<evidence folder>/code-<host>/`, pausing about half a second between requests. The first files usually load the rest in pieces ("chunks"): look inside them for more `.js` paths, or a map of short codes like `{12:"a1b2c3d"}` that become `<same folder>/<code>.js` (Nuxt and webpack sites), or a build manifest listing them (Next.js: `_next/static/…`). Keep following until you have them all, up to a few hundred files. Only files from the company's own domains; skip big shared libraries if they're obvious.
2. **Get an overview first,** so you know where to dig: every outside web address the code mentions (counted: the most-mentioned are their main suppliers and other domains), every money amount with a little text around it, trial mentions, route or page paths (`path:"/…"`), tracking event names, email addresses, and the names of known services (payments, CRM, email, chat, affiliate tracking, analytics, AI). A short throwaway script in the evidence folder does this faster than reading. Minified files are one enormous line, so search with a few hundred characters of context around each match rather than printing whole lines.
3. **Then search for what's still missing.** Useful searches: prices (`£`, `$`, `/mo`, `per month`), `trial`, `cancel`, `refund`, `affiliate`, `commission`, `Lead`, `Purchase`, `StartTrial`, `CompleteRegistration`, `Subscribe`, `fbq(`, `ttq.`, `gtag(`, `dataLayer`, `setTimeout` near words like "accepted", "reviewing", "expires" (staged waits and fake countdowns), `funnel`, `variant`, `experiment` (A/B tests), the names of people in the ads.
4. Things worth noting when you see them:
   - **Tracking events and when they fire.** The event sent at a step (a lead, a trial started, a purchase) is usually what their ads are optimised for. Events sent from their own server (calls to a "conversions" or "events" endpoint) mean serious paid advertising.
   - **Where leads go:** CRM or sales tools (Pipedrive, HubSpot, Close, GoHighLevel), booking tools (Calendly), email tools (Mailchimp, Mandrill, Customer.io).
   - **Timers:** a "spot expires in" countdown that starts from a fixed number on every page load is not real.
   - **Two or more versions of the funnel,** chosen by a URL setting or a split: what they're testing.
   - **Brands and domains:** other names in the code (sister brands, a US version, an older name).
   - **What powers the product:** AI features, builder tools, payment platforms (e.g. Stripe Connect for customers' shops).

Don't run the code, don't call the endpoints you find, and don't copy the code into the report. You're reading it for facts.

## Ad libraries

All public; none needs an account.

- **Meta (Facebook and Instagram):** start with a keyword search to find the advertiser, `https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=<GB|US|ALL>&q=<name or domain>&search_type=keyword_unordered&media_type=all`, then open **each advertiser page's full list**: every ad that page has run, live and stopped, whatever the wording. Its address is `https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=ALL&view_all_page_id=<page id>&search_type=page&media_type=all`; get the page ID from an ad's details ("See ad details" or the advertiser's name on a card links to it). Brands often advertise from several pages (a main brand, a regional page, a founder's page): check each. It's built in the browser, so you need one: a plain fetch returns an empty shell. Scroll to load more (dozens per scroll). Each card shows active or inactive, the run dates, "N ads use this creative", the page name, the text, and the link. To read many at once in a browser, pull the page text after scrolling and split it on "Active"/"Inactive"; pull the links from the cards' `l.facebook.com/l.php?u=` hrefs (the `u` parameter is the destination).
  - **Likely winners:** ads that ran longest and have the most copies. Inactive ads that ran for months count too.
  - **Destination links and their tracking tags** (`utm_source=anna-kitchen-video-h2`): teams often name ads by what they test (presenter, setting, format, hook number, week). Decode the naming: it's their test plan.
  - **Angles over time:** group the ads by hook (founder story, price anchor, "what's the catch", trade-specific, testimonial, urgency) and note which are newest and which ran longest.
  - UK and US ads show no spend or reach. EU ads show reach and audience age and gender in the ad's details.
- **Google:** the Ads Transparency Center, `https://adstransparency.google.com/?region=anywhere&domain=<domain>`: search, YouTube and display ads, with first and last shown dates.
- **TikTok:** `https://library.tiktok.com/ads` (ads shown in Europe) and TikTok's Top Ads in its Creative Center.
- **LinkedIn:** `https://www.linkedin.com/ad-library/search?keyword=<name>`, for business-to-business companies.
- **No browser?** Say the ad libraries couldn't be checked. Use the site's tracking (which ad platforms it reports to) and review wording to infer whether they advertise.

## Domain, DNS and hosting

- **WHOIS** (`whois <domain>`; for `.uk`, `whois -h whois.nic.uk <domain>`): registration date (business age), registrar.
- **DNS** (`dig +short MX/TXT/NS <domain>`): email provider (Google Workspace, Microsoft), verification records for tools they use, DNS host.
- **Headers** (`curl -sI`): server and hosting clues.
- **The same server for several domains** (`dig +short` on each): links brands to one company. Customers' sites that point to the company's server are a customer-count clue (reverse IP lookup services list them; Parsly will add this).

## Reviews

- **Trustpilot, Google, app stores, G2, Capterra:** count, rating and the date the profile was claimed. Review count over the company's age is a rough customer-flow clue.
- **Wording:** customers often say how they found the business ("saw your Facebook ad", "a post in a local group", "he called me", "a friend recommended"). Count these: it's evidence for channels.
- **Names of staff** in reviews show who does the selling.
- If a review site shows a bot check, don't try to get past it; use another source.

## The people behind it

Founders often matter as much as the funnel: their audience can be a channel in its own right, and the company can be a showcase for something else they sell.

- **Who:** names on the about or team page, the terms (who the contract is with), press releases, job ads, the app store publisher, company registers, and the faces in the ads.
- **Their public channels:** YouTube, X, LinkedIn, Instagram, TikTok, podcasts and interviews. Note audience size, what they teach or talk about, and who it's aimed at (customers, or people who want to run the same kind of business?).
- **What else they sell:** courses, paid communities (Skool, Circle), coaching, software, affiliate links in their bios and video descriptions. A founder teaching "how to run an agency like mine" means part of the money and the credibility comes from there.
- **Their claims:** founders' revenue and customer numbers in titles and interviews; collect them with dates, since they often change a lot.
- **Keep it to business:** what they publish and what's on record about their companies. Leave out private life: homes, family, personal accounts unrelated to the business.

## Company records, archives and size

- **Company registers:** UK Companies House (`find-and-update.company-information.service.gov.uk`, free), US state registries or OpenCorporates, and the EU's national registers. Directors, incorporation date, filed accounts (small companies may file only a short balance sheet), registered address. A VAT or company number in the footer finds it.
- **Wayback Machine** (`https://web.archive.org/web/*/<domain>*` or `http://archive.org/wayback/available?url=<url>&timestamp=<YYYYMMDD>`): how the offer, prices and claims changed over time.
- **Careers pages and job ads:** roles and salaries show team size and what they're investing in.
- **Size estimates:** say how you got each one (e.g. "~900 reviews since 2023 and £20/month suggests roughly £X–Y a month if N% of customers review"), give a range, and mark it as your estimate.

## Reading what you find

- **What an affiliate payout says:** a business paying £40–£60 per customer to partners will pay roughly that to win one through ads too.
- **Phone number required on a form** usually means a sales call; no phone and a card at sign-up means self-serve.
- **Card at trial start** vs **pay after you see it**: very different conversion and churn. Check the copy against the checkout code.
- **Changing numbers** (customers, reviews, years in business) across pages or ads: report the range and the sources.
- **Placeholder testimonials:** stock avatars, template names, numbers that look made up.
