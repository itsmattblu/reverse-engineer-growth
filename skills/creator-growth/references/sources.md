# Where the evidence is, and how to read it

Read the section you need. Everything here reads only what any logged-out visitor can see. Platforms change what they show often: if a method stops working, note it under "couldn't see" and move on rather than trying to get round a block.

- [The product's site and legal pages](#the-products-site-and-legal-pages)
- [Domains and age](#domains-and-age)
- [Company records](#company-records)
- [App and extension stores](#app-and-extension-stores)
- [X](#x)
- [LinkedIn](#linkedin)
- [YouTube, TikTok and Instagram](#youtube-tiktok-and-instagram)
- [Reddit, Bluesky and Threads](#reddit-bluesky-and-threads)
- [Communities, directories and press](#communities-directories-and-press)
- [Archives](#archives)
- [Revenue and user claims](#revenue-and-user-claims)
- [Measuring posts](#measuring-posts)
- [Commenters, pods and copies](#commenters-pods-and-copies)

## The product's site and legal pages

- **Legal notice, privacy policy, terms of sale:** often the richest source. They name the company (or say it's "being incorporated"), the director or publisher, a contact email (which can reveal a co-founder), earlier product names, what data sign-up collects and what it's used for, and whether the paid plan is actually on sale.
- **Sign-up fields:** a required phone number usually means they call or message to sell; read the field and its wording, never submit it.
- **Built in the browser:** many product sites come back as an empty shell to `curl` or a fetch tool. Open each page directly in a browser (navigating within the app may not render), or read the text from the site's script files.
- **Links out:** the footer and about page link the founders' profiles; tracking-link services on outbound links show which clicks they measure.

## Domains and age

- **RDAP** (`https://rdap.org/domain/<domain>`, JSON, no key): registration date and registrar. The product's domains and any sister sites found in links or code. A domain registered a few months before launch dates when the product began.
- **WHOIS** (`whois <domain>`) works too where RDAP doesn't.

## Company records

- **The founders' country decides the register:**
  - UK: Companies House (`find-and-update.company-information.service.gov.uk`, free).
  - France: `https://recherche-entreprises.api.gouv.fr/search?q=<name or number>` (free, no key): companies, directors, dates, closures and liquidations.
  - Elsewhere: the national register or OpenCorporates.
- **What to look for:** earlier companies by the same people, when they opened and closed, and the founders' roles. An earlier product that closed is part of the story (what they learned, the audience they built with it).
- Registers list dates of birth for directors; use them only to tell same-named people apart, not in the report.

## App and extension stores

- **Chrome Web Store:** the listing shows a rounded user count ("1,000+"), rating and review count. Some built-in browsers can't open it ("only works in a full browser"); `curl` on the listing address and on `<listing>/reviews` usually works, and the reviews page shows who reviewed and when.
- **Dated snapshots:** extension trackers (extscope.org, chrome-stats.com) keep user counts over time, which shows a launch's real effect. They sometimes block fetches; take the newest dated figure you can get and say its date.
- **Reviews:** fetch `<listing>/reviews` and check whether early reviews come from the founders themselves or appear in a burst on one day, before the public launch.
- **App Store / Play:** release date, rating count, "what's new" history.

## X

- **Profile without logging in:** `https://api.fxtwitter.com/<handle>` (JSON; send a browser-like `User-Agent` header, or every handle comes back as a false 404): followers, following, post count, join date, bio, links. A single post: `https://api.fxtwitter.com/<handle>/status/<id>` (views, likes, reposts, replies, date).
- **Posting rate:** post count ÷ days since joining gives a lifetime average (replies included; heavy repliers show 20–40 a day).
- **Creator pages:** SuperX publishes public creator pages (`https://superx.so/creators/<handle>`) with a follower snapshot, tone summary and top posts by views. Undated: use the newest post on the page to date it.
- **Finding their handle:** web search often doesn't link a founder to their X account. Try likely handles on fxtwitter: their name, first name plus surname initial, first name plus the first letters of the surname, `<product>`, `<product>now`, `<product>app`. fxtwitter answers a wrong 404 without a `User-Agent` header, and sometimes even with one: retry once.
- **Recent posts, newest first:** `https://api.fxtwitter.com/2/profile/<handle>/statuses?with_replies=false` returns the account's own recent posts with views, likes, replies, reposts, quotes and bookmarks (about 2–3 weeks for a busy account; same `User-Agent` and retry rules). Best for "what's breaking out now".
- **Top posts:** a SuperX creator page carries their all-time top posts (and about 14 recent ones) with views as JSON inside the page (HTML-escaped); search the page source for it.
- **Search:** web search for `site:x.com <handle> <topic>` finds individual posts; the X timeline itself needs a login beyond the first few posts.
- **Bio as scoreboard:** many founders list each product's monthly revenue in their bio; record it with the date.

## LinkedIn

- **Profiles are closed** to logged-out visitors (HTTP 999 or a login wall). Don't try to get past it.
- **Single post pages often load in a browser:** the full post, reactions, comments, the commenters (name, headline, country subdomain such as `ng.linkedin.com`), and the author's follower and post counts. Find posts by searching the product name or a topic with "linkedin".
- **Exact post dates:** the number in a post's address (`activity-<id>` or `urn:li:activity:<id>`) holds its timestamp: `id >> 22` is milliseconds since 1970. For example in Python, `datetime.fromtimestamp((id >> 22) / 1000, tz=timezone.utc)`.
- **Finding their posts without Parsly:** fetch tools and most search APIs return only one or two LinkedIn posts. What works:
  1. A search engine query `site:linkedin.com/posts "<Full Name>"` (and the profile slug, e.g. `"firstname-lastname-a1b2c3"`) lists their public post addresses; run it a few times with a topic or the product name. Mind the search limit in the rules: a handful of queries, seconds apart.
  2. Fetch each `https://www.linkedin.com/posts/...` page logged out with `curl`. The HTML holds `data-num-reactions`, `data-num-comments`, the post text (in the JSON-LD `articleBody`), about 10 comments, and the author's follower and post counts. Country pages (`fr.linkedin.com/posts/...`) leave out follower counts: fetch the same path on `www`.
  3. **Keep only posts whose address slug is the person's own.** Search also returns other people's posts where they only commented.
- **Who boosted them:** reposters aren't shown logged out. Search the product name across `site:linkedin.com/posts` to find other people's posts about it.
- **Without either** you'll see a handful of posts at best, so say the post history wasn't visible. **With Parsly**, `creator_posts` returns about 100 posts a page with reactions by type, comments, reposts and each post's `xUsual`.

## YouTube, TikTok and Instagram

- **YouTube:** the channel's About page (subscribers, join date, total views); the Videos tab sorted by popular. Social Blade has subscriber history. With Parsly, `youtube_channel_videos` with `sort: "breakouts"` measures each video against its neighbours.
- **TikTok:** profile pages often load with follower and like counts and recent videos; Social Blade has history for larger accounts.
- **Instagram:** often only the page title (name, follower count) for logged-out visitors; with Parsly, `creator_posts` reads the posts.
- Search engine snippets of these profiles often carry a follower count with a rough date.

## Reddit, Bluesky and Threads

- **Reddit:** the person's posts and comments (`/user/<name>/submitted`), the subreddits they post in, and how their product posts were received. Reddit often blocks automated fetches; search results for `site:reddit.com <product>` are the fallback.
- **Bluesky:** fully public. `https://public.api.bsky.app/xrpc/app.bsky.actor.getProfile?actor=<handle>` (followers, posts) and `app.bsky.feed.getAuthorFeed?actor=<handle>` (their posts with likes, reposts, replies).
- **Threads:** profiles show follower counts; post history is limited when logged out.

## When the product hosts its users' content

Many creator tools publish users' work on their own domain (public profiles, threads, pages, reports). These are often the richest source:
- **The founders' own pages** on their product (their profile or saved posts there) can list their posts with links, which fxtwitter or a post page then measures. They're a self-selected sample (what the founders chose to keep), so say so and don't treat the ratios as their full history.
- **Users' pages** show the product's growth loop: a "made with" link, the author's referral tag (`via=`, `ref=`) on links back, pages that reached Hacker News or search. Search `site:<product domain>` and Hacker News (`hn.algolia.com/?q=<product>`).

## Communities, directories and press

- **Indie Hackers** (product page, milestone posts), **Product Hunt** (launch day, maker, votes), **Peerlist, Uneed, BetaList**: launch dates and how they told the story.
- **Podcasts and interviews:** founders explain their method in their own words; search "<name> podcast", "<product> interview". Note the date and what they credit.
- **Newsletters:** their own (subscriber claims) and ones that featured them.
- **Communities:** X Communities, Discords, Skool groups and subreddits they run or post in.

## Archives

- **Wayback Machine:** `https://web.archive.org/web/*/<url>*` lists snapshots; `http://archive.org/wayback/available?url=<url>&timestamp=<YYYYMMDD>` gets the nearest one. Old snapshots of a profile give follower counts at past dates; old snapshots of the site show earlier names and offers. The archive is sometimes offline or answers 429 (too many requests): wait a minute and retry once, or try the CDX endpoint (`https://web.archive.org/cdx/search/cdx?url=<url>&output=json&limit=20`); otherwise note it and don't guess.

## Revenue and user claims

- **Verified revenue:** TrustMRR (`https://trustmrr.com/startup/<slug>`, `https://trustmrr.com/founder/<handle>`) shows revenue read from the payment provider, and some founders' follower counts and growth.
- **Claims:** "+300 users in 24h", "$10K MRR" in posts and bios are claims. Record each with its date and whose it is; compare with a store's count or a verified page where one exists.

## Measuring posts

- **Engagement** = likes (or reactions) + comments + reposts/shares. Views where the platform gives them.
- **Their usual** = the median engagement across the posts you have. A breakout is a post far above their usual: 5× or more stands out; 3× is worth a look. Raw numbers mislead: 400 reactions is a breakout on a 2K account and ordinary on a 100K one.
- **Find the format:** group the posts by what they do (giveaway, launch, milestone, personal story, opinion, how-to) and compare each group's median. The engine is the group that sits well above the rest, not the single biggest post.
- **Over time:** the monthly median shows what changed things (a new format, a language or platform switch, a launch).

## Commenters, pods and copies

- **Who comments:** read 10–20 commenters on the biggest posts. Their roles show whether the audience is the buyers. A run of polished, generic comments from accounts far from the product's market (for example many from one or two countries the product doesn't serve) suggests engagement pods or bought comments; report it as a likely sign, with what you saw.
- **"Comment KEYWORD" posts** inflate comment counts by design: each comment is a request for the giveaway. Count them separately from conversation.
- **Copies:** put a breakout post's opening line in quotes into a web search. If someone else posted it days earlier, note who was first and the dates.
