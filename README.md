# REG: reverse-engineer growth

**See something that's working? Find out why, and do it yourself.**

Ask your AI how a business wins its customers, and get the whole funnel back: the ads and where they lead, the sign-up, the pricing, the upsells and the people behind it, with the evidence for every finding.

[![You type "How does AG1 get its customers? Go deep." You get AG1's funnel: its ads, landing pages, the code behind its site and its checkout, each marked seen or inferred, and the patterns found.](https://parsly.to/reg/example-ag1.png)](https://parsly.to/guides/how-ag1-gets-its-customers/)

**A real example:** we asked REG how AG1 gets its customers. It found half their US ads running in creators' names, a landing page for every podcast and audience, a visitor classifier in their site's code, and a free gift worth $43 on one page and $72 on another. [Read the full AG1 teardown →](https://parsly.to/guides/how-ag1-gets-its-customers/)

## Install

In Claude Code:

```
/plugin marketplace add itsmattblu/reverse-engineer-growth
/plugin install reg@reg
```

Free, open source, no account. Runs in Claude Code today, with more AI tools on the way.

## Ask

Swap in whoever you want to study:

```
How does [company] get its customers? Go deep.
```
```
Quick look at [company]'s funnel.
```
```
What ads is [company] running, and where do they send people?
```
```
Compare how [company A] and [company B] get their customers.
```
```
I sell [your product] at [your price]. How does [competitor] win customers, and where could I beat them?
```

It asks how deep to go (quick, standard or deep) unless you've said. **Every finding comes with its evidence. Every report ends with what it couldn't see.** No guesses dressed up as facts.

## What's inside

| | |
|---|---|
| **The funnel skill** (`skills/funnel/SKILL.md`) | The method: what to gather, in what order, a ten-stage funnel map with a finish line, a skeptic's pass, and the report |
| **The sources** (`skills/funnel/references/sources.md`) | How to read each one: the site and every link, login pages, the code a site serves, the Meta, Google, TikTok and LinkedIn ad libraries, domain records, reviews, company registers, archived pages |
| **The pattern library** (`skills/funnel/references/patterns.md`) | 27 tricks and tactics that keep turning up, each with how to spot it and what it means: creator partnership ads, a page per traffic source, the quiz intercept, staged acceptance, "free" with the card up front, the decoy price, lock-in, review gating, the white-label underneath… |
| **Example reports** | [How AG1 gets its customers](https://parsly.to/guides/how-ag1-gets-its-customers/), with more on [parsly.to](https://parsly.to/reg/) |

Found something good? Post it and tag [@itsmattblu](https://x.com/itsmattblu). Made by [Parsly](https://parsly.to): [parsly.to/reg](https://parsly.to/reg/).

## What it does for you

1. **Install it** in Claude Code (the two commands above).
2. **Ask in your own words,** or call the skill by name:
   - **Funnel** (`/reg:funnel`): "How does [company] get its customers?" Takes a quick free look, asks how deep to go (quick, standard or deep), then maps how the company wins and keeps customers: its ads and where they lead, the landing page, the sign-up, the follow-up, when the card goes in, how the product gets delivered, the upsells and referrals. Each step comes with its evidence, plus the claims that don't hold up and what couldn't be seen from outside. The report and its evidence are saved in a `parsly/funnels/<date>-<company>/` folder where you run Claude Code.
3. **Give it a browser if you can.** Ad libraries like Meta's only show ads in a browser. Without one, the report says the ads weren't checked.

## Play fair

- **Public evidence only.** The skills read what anyone can see. They never sign up, log in, fill in forms or get past bot checks.
- **Study, don't copy.** Take the patterns and make them your own; don't lift other people's scripts, videos or ads.
- **Claims stay claims.** "10,000 happy customers" on someone's homepage is their number, and the report says so.

## How it does it

- **The pattern library** (`references/patterns.md`) is checked against every company before the report is written, and each pattern found is named with its evidence. It's anonymous: patterns are described in general terms, with only published teardowns of big brands (AG1) linked as worked examples.
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
