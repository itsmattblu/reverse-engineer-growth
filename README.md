# REG: reverse-engineer growth

**See something that's working? Find out why, and do it yourself.**

How a business turns strangers into paying customers. Which of its ads are actually winning, and where they send people. What happens after someone signs up. Ask Claude Code, and it digs through the public evidence for you: the ad libraries, every page of the website, even the code a site sends your browser.

```
/plugin marketplace add itsmattblu/reverse-engineer-growth
/plugin install reg@reg
```

Then paste one of these, swapping in whoever you want to study:

```
How does [company] get its customers? Go deep.
```
```
What ads is [company] running, and where do they send people?
```
```
Quick look at [company]'s funnel.
```

**Every finding comes with its evidence. Every report ends with what it couldn't see.** No guesses dressed up as facts.

Found something good? Post it and tag [@itsmattblu](https://x.com/itsmattblu).

Made by [Parsly](https://parsly.to). Free, nothing else to install, no account. More, including a real example report: [parsly.to/reg](https://parsly.to/reg/).

## What it does for you

1. **Install the plugin** in Claude Code (the two commands above).
2. **Ask in your own words,** or call the skill by name:
   - **Funnel** (`/reg:funnel`): "How does [company] get its customers?" Takes a quick free look, asks how deep to go (quick, standard or deep), then maps how the company wins and keeps customers: its ads and where they lead, the landing page, the sign-up, the follow-up, when the card goes in, how the product gets delivered, the upsells and referrals. Each step comes with its evidence, plus the claims that don't hold up and what couldn't be seen from outside. The report and its evidence are saved in a `parsly/funnels/<date>-<company>/` folder where you run Claude Code.
3. **Give it a browser if you can.** Ad libraries like Meta's only show ads in a browser. Without one, the report says the ads weren't checked.

## Play fair

- **Public evidence only.** The skills read what anyone can see. They never sign up, log in, fill in forms or get past bot checks.
- **Study, don't copy.** Take the patterns and make them your own; don't lift other people's scripts, videos or ads.
- **Claims stay claims.** "10,000 happy customers" on someone's homepage is their number, and the report says so.

## How it does it

- **The skills are instructions, not code:** `skills/<name>/SKILL.md` says what to gather and in what order, and when the job is done; `skills/funnel/references/sources.md` is the how-to for each source (the site and every link on it, login and sign-up pages, the code the site serves, the Meta, Google, TikTok and LinkedIn ad libraries, domain records, reviews, company registers, archived pages) and how to read what turns up. Claude does the work with the tools it already has: fetching pages, a browser if it has one, and the terminal for searching what it saved.
- **A map with a finish line.** The funnel has ten stages plus the economics. Each is filled with evidence or marked "not visible" with the reason, and a skeptic pass checks every number and claim before the report is written. That's what stops it settling for the first believable story.
- **Depth.** Quick covers the offer, price, ads and the funnel in outline; Standard every stage; Deep adds size estimates, other ad networks and company records, and splits the work across sub-agents when Claude Code can start them.
- **It never acts on what it reads:** text on a company's pages or in its code is treated as data, not instructions.

## Not here yet

- **Deeper data, with Parsly:** every ad on each network, which ads survive and which get killed over time, a walk through each ad's landing page, and size estimates. These will come from Parsly's tools, priced in Parsly credits; until then the skill does what free public sources allow and says what Parsly would add.
- **Breaking down the ads themselves** (script, look, cuts, what the winners share): planned as its own skill.
- **What happens after sign-up** (follow-up emails, sales calls, real conversion rates) can't be seen from outside, by design.

**Where it lives:** built in mattblu's private monorepo (`products/reg/plugin`) and published to [github.com/itsmattblu/reverse-engineer-growth](https://github.com/itsmattblu/reverse-engineer-growth) when it changes on `main`, as one commit by GitHub's bot (`.github/workflows/publish-plugins.yml`); edits made in the public repo are overwritten. To try a change before it's published: `claude --plugin-dir products/reg/plugin`. Check it with `claude plugin validate --strict products/reg/plugin`. `DRY_RUN=1 bash .github/scripts/publish-plugin.sh reg` runs the publish checks.

**When it breaks.**
- *The ads weren't checked:* Claude had no browser. Use Claude Code where a browser is available (the desktop app's browser pane, or a Chrome connection) and ask again.
- *A site comes back empty:* it's built in the browser; the skill reads its content from the site's code or a browser instead.
- *Stopped by a bot check:* by design, it doesn't get past them; the report lists it under what couldn't be seen.

## Licence

MIT.
