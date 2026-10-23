# Funnel patterns

Tricks and tactics that keep turning up when you take businesses apart, each with how to spot it and what it tells you. Check every company against this list, and name the patterns you find in the report ("Pattern: staged acceptance"), with the evidence. Describe what you saw neutrally: a pattern is a finding, not an accusation.

Grouped by where they sit in the funnel:

- [Ads](#ads)
- [Landing pages](#landing-pages)
- [Sign-up and capture](#sign-up-and-capture)
- [Offer and checkout](#offer-and-checkout)
- [Keeping customers](#keeping-customers)
- [Proof and claims](#proof-and-claims)
- [Behind the scenes](#behind-the-scenes)

## Ads

### Creator partnership ads
Ads run in a creator's name ("[creator] with [brand]") rather than the brand's, often many creators at once.
- **Spot it:** in the Meta Ad Library, cards headed "[name] with [brand]"; links carrying a creator-ads tool's tag (e.g. `?trybe=`); ads linking to creators' profiles.
- **Means:** they've found that faces and voices outperform brand ads, and they're paying creators to rent their audience's trust. Count the share of live ads that run this way.
- **Worked example:** half of AG1's live US ads ([teardown](https://parsly.to/guides/how-ag1-gets-its-customers/)).

### Founder-voice ads
Ads written as a personal post from the founder or a named person ("Hi all, my friend and I recently started…"), often with the same story rerun for months.
- **Spot it:** first-person copy, named people, a story about starting out; check whether "recently started" copy has run for a year.
- **Means:** native-looking posts beat polished ads for small-business buyers. A long-running one is probably their best performer.

### Waves of variants, left running
Dozens of ads launched on the same day, each with one copy, then left running; new waves every few weeks.
- **Spot it:** many ads sharing a start date; "1 ad uses this creative" on most; tracking tags that name what's being tested (presenter, setting, format, hook number, week).
- **Means:** they test by volume rather than scaling one winner. Decode the naming in the tags: it's their test plan.

### Evergreen scarcity
"Limited spots", "only for July", "sold out, back for now" on ads that run for months.
- **Spot it:** compare the scarcity claim with the ad's start date and the number of copies.
- **Means:** scarcity is a standing hook, not a real limit. Report the claim and the dates side by side.

## Landing pages

### A page per traffic source
Separate landing pages for each podcast, partner, audience or ad angle, often unlinked from the site.
- **Spot it:** the sitemap (pages per podcast host, per partner, per campaign); ad links pointing to different pages; a separate subdomain for new audiences.
- **Means:** they match the page to where the visitor came from, which usually lifts conversion. Their list of pages is a list of their channels.
- **Worked example:** AG1's per-podcast pages and its audience pages on a separate subdomain ([teardown](https://parsly.to/guides/how-ag1-gets-its-customers/)).

### A visitor classifier
Code that sorts each visitor into groups by where they arrived from (paid search, social, a competitor's site, returning).
- **Spot it:** in the site's code, words like `classify`, `creator-growth`, `segment` next to a list of referrers or competitor names.
- **Means:** the page changes with the visitor. Which groups exist tells you which channels and competitors they care about.

### Two funnels behind one page
The same site serves different funnels chosen by a URL setting or a split test (`?funnel=`, `variant`, `experiment`).
- **Spot it:** in the code, a parameter that switches the call to action's destination; pages named `-old`, `-v2`, `original-two`.
- **Means:** they're testing a structural change (quiz vs self-serve, call vs checkout). Report both routes.

## Sign-up and capture

### The quiz intercept
"Book a demo" or "Get started" buttons quietly opening a multi-step quiz that asks for revenue or budget before anything else.
- **Spot it:** buttons whose code opens a modal instead of linking; quiz steps asking revenue, team size, urgency; phone required.
- **Means:** they qualify leads before a human spends time on them, and steer bigger ones to a higher offer. A required phone number means a sales call.

### Partial-form capture
Each answer in a form saved as soon as it's entered, so half-finished forms still become leads.
- **Spot it:** in the code, a request sent on each step's change, not only on submit.
- **Means:** they follow up people who never finished. Expect calls or emails after a half-filled form.

### Lead routing by size
Answers decide what happens next: small leads get "we'll call you", bigger ones book a call or see a sales video, existing customers go to their account manager.
- **Spot it:** in the code, branches on revenue or company name after the form.
- **Means:** sales time goes to the biggest leads. The thresholds tell you who their ideal customer is.

### Staged acceptance
After a form, a "Reviewing your request… Request accepted!" sequence, sometimes with "we only accept 20% of applicants".
- **Spot it:** in the code, messages on fixed timers (e.g. 20 seconds) with no request to a server in between.
- **Means:** the review is theatre, used to make a free offer feel earned. Report the fixed timings.

## Offer and checkout

### "Free" with the card up front
A free build, trial or gift that needs card details before anything is delivered, then becomes a subscription.
- **Spot it:** compare the ad's "free" with the checkout code (a trial on the subscription) and the terms.
- **Means:** the free thing is a trial of a paid plan. Note when the first charge lands and how cancelling works.

### The decoy price
A plan or service priced just above the bundle they want you to buy (e.g. a single service at $400 next to a bundle at $389).
- **Spot it:** on the pricing page, an option that's clearly worse value than the one beside it.
- **Means:** it's there to make the main offer look cheap.

### Inflated "value"
Discounts measured against a total that includes the free gifts, or a gift whose stated value changes from page to page.
- **Spot it:** compare the "was" price with the one-off price; note every stated value of the same gift on the same day.
- **Means:** the discount is smaller than it looks. Report each figure with its page.
- **Worked example:** AG1's welcome kit valued differently on two pages ([teardown](https://parsly.to/guides/how-ag1-gets-its-customers/)).

### Countdown that resets
"Your spot expires in 1h 20m", restarting from the same number every time the page loads.
- **Spot it:** reload the page; or find the fixed number of seconds in the code.
- **Means:** fake urgency, usually on a page for people who started and didn't finish.

### Prepay to waive the setup fee
A setup fee that disappears if you pay several months up front.
- **Spot it:** pricing or terms offering quarterly or yearly prepayment with the fee waived.
- **Means:** cash up front, and customers held past the money-back window.

## Keeping customers

### Lock-in
Things you lose when you leave: a website you rent rather than own, a domain they control (and lock for 60 days), loyalty credits that vanish on cancelling.
- **Spot it:** the terms (ownership, transfers), the loyalty page, the account app's code.
- **Means:** churn is managed by making leaving costly. Their weak spot for a competitor to attack.

### The cancellation save
Cancelling triggers reasons, then an offer (50% off for life, a free month), then a warning.
- **Spot it:** the account app's code (cancel flow screens), help pages.
- **Means:** churn matters to them; the size of the offer hints at how much a customer is worth.

### The upsell ladder
A cheap entry product that leads to done-for-you packages, add-ons and yearly plans, often pitched inside the app or on a call.
- **Spot it:** upgrade pages in the app's code, payment links for higher tiers, FAQ written for existing customers.
- **Means:** the entry product isn't where the money is. Map every rung with its price.

## Proof and claims

### Numbers that don't agree
Customer counts, review counts or years in business that differ between pages or ads on the same day.
- **Spot it:** collect every figure with its page and date.
- **Means:** at least some are out of date or rounded up. Report the range and sources; don't pick one.

### Placeholder testimonials
Quotes with stock avatars, template slot names in the code (`QUOTE_1`) or figures that look made up.
- **Spot it:** avatar image hosts like stock-photo or placeholder services; slot names next to the quotes.
- **Means:** the social proof may not be real customers. Say what you saw, not that it's fake.

### Prompted reviews
A review profile that jumped from a handful to hundreds in months, with many reviews naming staff.
- **Spot it:** review dates and counts by month; staff names in five-star reviews.
- **Means:** reviews are requested at a set moment (often onboarding). It's a size and process clue, not proof of anything wrong.

### Review gating
Customers asked to rate first, with high ratings sent to Google and low ones kept private.
- **Spot it:** a rating step before a review link; code branching on the score; the offer described in the product's own features.
- **Means:** Google's rules don't allow it. Report it as a risk for them and for their customers.

## Behind the scenes

### The white-label underneath
A product that's really an off-the-shelf platform with their brand on it.
- **Spot it:** the login page's domain and code (e.g. GoHighLevel's LeadConnector), DNS records pointing at a platform, the terms naming it.
- **Means:** what they add is setup, niche templates and sales, not the software. Copying the product is easier than it looks.

### What the ads are optimised for
The event their site reports to the ad platforms at a given step (a lead, a trial started, a purchase), often sent from their own server.
- **Spot it:** in the code, the event names sent to Meta, TikTok and Google at each step; calls to a "conversions" endpoint.
- **Means:** that event is what the ad platforms are told to find more of. It shows which step they treat as the win.

### What a customer is worth
An affiliate or referral payout per customer.
- **Spot it:** partner and affiliate pages, referral terms.
- **Means:** a business paying £50 per customer to partners will pay roughly that to win one through ads too.

### The competitor typo page
A page made for people who mistype a rival's name.
- **Spot it:** a page titled "[rival-like name]: maybe you meant [us]?", often unlinked, found in the sitemap or the code's route list, sometimes tagged as such.
- **Means:** they're harvesting a competitor's brand searches cheaply, without ads.

### The free extension as a feeder
A free browser extension or small app for the same users, promoting the paid product.
- **Spot it:** a "by the makers of" page, a store listing from the same developer, a link or embed inside the free tool carrying its own source tag.
- **Means:** a cheap, lasting channel; its user count is a size clue for the audience.

### Source tags on every free surface
Each tool, page, shared link and profile carries its own campaign tag (`?src=`, `typ_source=`, `ref=`).
- **Spot it:** a list of source values in the site's code; call-to-action links tagged per button.
- **Means:** the tag list is their map of channels, and the business grows on owned surfaces rather than ads.

### The founder's audience
A founder with a channel, course or paid community teaching others to run the same kind of business.
- **Spot it:** the founder's YouTube, X and LinkedIn; a course or community linked from their bio; affiliate links to the tools they use.
- **Means:** the audience is a channel in its own right, and the company may also be a showcase for what they teach. Part of the money may come from there.
