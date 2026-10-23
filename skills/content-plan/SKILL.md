---
name: content-plan
description: A weekly content plan: a research brief on what's breaking out for the people someone learns from and what they actually did, then a week of post drafts (LinkedIn and X first) that give readers something useful, in their voice, each labelled so results can be measured later. Modelled on others' breakout posts and filled with what the person built, found and measured; learns their voice from every edit and rejection. Use whenever someone wants a content plan, content calendar, content ideas, LinkedIn or X post ideas, a week of posts, help building in public, "what should I post" or "turn my week into posts", even if they don't name the skill. Never posts or schedules anything itself. Works without Parsly; with Parsly connected it measures what's breaking out and reads their own posts' numbers.
---

# A week of posts

Draft a week of posts the person would be glad to publish, for each platform, in their voice. The goal is consistency without a blank page: they review, edit and post; you do the digging and drafting.

Two inputs, both required:
- **What's working for others.** The posts breaking out right now for the people they learn from (5–20 accounts in their space): which formats, topics and hooks, and what those posts give the reader. This decides the shape and the value of most drafts.
- **What only they have.** What they built, found, measured or got wrong. This fills the shape with substance nobody else can copy.

**Value first.** Most posts should give the reader something to take away (a free tool, a playbook, a teardown, a finding, a clear explanation), the way the founders who grew without ads did. A diary of their week is at most a fifth of the batch. Every draft also carries labels (format, topic, hook, what inspired it) so a later look at the results can say what worked.

## The rules

- **Never post, schedule, like, follow, comment or message for them.** You draft; they publish.
- **Nothing private goes into a draft:** no secrets, keys or internal URLs; no customer or user names, emails or data; no unreleased features, prices or plans unless they say they're happy to share them; no other people named in a less than flattering way. When a note mixes public and private, draft only the public part and say what you left out.
- **"Interesting to follow, not easy to clone":** share the story, the lesson, the result; think twice before publishing exact revenue, architecture details or step-by-step recipes for the product's core. Ask when unsure.
- **Every number comes from a source** (their notes, their analytics, a research page) and stays as precise as the source. Never invent a number, a quote, a customer or a result.
- **Write like them, not like an AI:** no "In today's fast-paced world", no "Here's the thing", no "Let that sink in", no strings of emoji, no hashtags wall, no engagement bait ("Comment YES if you agree": LinkedIn demotes it). Plain words, short sentences.
- **Study, don't copy:** use other people's formats, never their posts.

## 1. Look around, then confirm before you begin

Take a free first look (a minute or two):

1. **Their work since the last batch:** a notes or journal folder (`notes/`, `journal/`, daily notes), changelogs, `git log --since` on the repos they point at (commit subjects, merged pull requests), TODO files, READMEs that changed, a research folder. Ask where to look if nothing obvious is there.
2. **Who they learn from:** `parsly/content/inspiration.md` (the 5–20 accounts they study, per platform). If it doesn't exist, ask for a few names or suggest some from their teardowns and niche, and save the list. Then find each account's recent breakouts:
   - **With Parsly:** `creator_posts` with `sort: "breakouts"` on each (say the credit cost first): posts far above that account's usual, with their numbers.
   - **Without Parsly:** what's public (an X account's recent posts through fxtwitter or a SuperX page, LinkedIn post pages found through search, as the `creator-growth` skill's sources describe), and any audience or funnel reports already in `parsly/`. Say these are a sample, not measured against their usual.
   - Note for each breakout: the format, the hook, what it gives the reader, and the link.
3. **Their playbook:** `parsly/content/playbook.md`, the strategy they've adopted from teardowns of people who grew (written by the `creator-growth` skill): platforms, cadence, formats to use and avoid, giveaways to make. Follow it; it outranks the default mix below. If there's none, suggest running `/reg:creator-growth` on one or two people they'd like to grow like, and carry on with the defaults.
4. **What they've already learned:** `parsly/content/voice.md` (their voice and their dislikes, from earlier batches), `parsly/content/learnings.md` (what's worked for them, from a results check), the last batch's drafts and which were rejected, and any teardowns in `parsly/creators/` and `parsly/funnels/` (other people's engines worth borrowing).
5. **Their past posts, for the voice:** with Parsly connected, `creator_posts` on their own profiles reads them with their numbers (say the credit cost first). Without it, ask them to paste 3–5 posts they liked writing, or a profile link to read what's public.
6. **Is Parsly connected?** (`creator_posts`, `parsly_help` available.)

Then send one short message and wait for the answer. Never spend Parsly credits before a yes.

```markdown
**Before I start:** <what you found: e.g. "6 days of notes, 23 merged changes; 9 breakouts from the 12 accounts you follow, mostly free tools behind a comment and teardowns; last week's 5 drafts (2 rejected: too salesy)">.

I'll write this week's brief (what's breaking out, what you did, where they meet), then draft <5> posts for <LinkedIn and X>, one a day, each written for both platforms:
- <format>, modelled on <breakout>: <one-line idea filled from their own work>
- …
- One experiment: <a format they haven't tried>.

<Without Parsly:> **Parsly isn't connected,** so I can't read your past posts with their numbers. I'll learn your voice from <what they pasted / the voice file / your notes> and won't know yet which formats work for you.
<With Parsly:> **With Parsly:** reading your last <N> posts on <platforms> costs about <N> credits; you have <balance>.

Swap any idea, or go?
```

- Default: **5 posts** (one per weekday), for the platforms they name; LinkedIn and X if they don't say.
- If they've already said what they want ("a week for LinkedIn"), send the same message ending "Starting now unless you'd like to change anything" and go ahead, unless credits would be spent.

## 2. Write the week's brief

Before any draft, write a short research brief: an informed view of what people in their space are posting about this week, what the person did, and where the two meet. Save it as `parsly/content/<YYYY>-W<week>/brief.md` and show it first.

```markdown
# Week <week> brief

## What's breaking out
<The 3–5 themes and formats doing best this week among the accounts they learn from (and the wider niche, from a few searches): each with 1–2 linked example posts, how far above their author's usual (if measured), and what the reader got from it. Name a conversation everyone is having, if there is one.>

## What you did
<The 3–6 most postable things from their week: built, decided, found, measured, got wrong. Each with its source.>

## Where they meet
<The opportunities: each of their things matched to a theme or format that's working, as a one-line post idea. Flag anything they could give away. Flag what everyone's posting about that they have nothing real to add to: skip it.>

## What's still unknown
<Without Parsly: the breakouts are a sample, not measured against their authors' usual. Any accounts that couldn't be read.>
```

The drafts come from "Where they meet". The brief is useful on its own: if they only read one thing each week, it should be this.

## 3. Choose the week

If there's a fresh growth report in `parsly/creators/` (from `creator-growth`) that the person hasn't posted about yet, make it this week's output post: "I reverse-engineered how @<name> grew", the turning points and the one thing to copy, facts only, with the report's link (or page) in the first comment or reply.

Start from the brief's "Where they meet", not the notes alone: for each slot, take a format and angle that's working for the people they learn from, then fill it with something real of theirs. "Their giveaway of 60 agents did 12× their usual" becomes "a free pack of the person's own skills behind a keyword". Never their text, only the shape and the kind of value.

Balance the mix (formats are in [formats.md](references/formats.md)):

- **Giveaway** (a free tool, template, skill pack or checklist behind "comment WORD") — about one a week, only if they have something real to give.
- **Output or teardown** (something their product or research produced that's useful on its own: how a known brand gets customers, a finding from data, a before and after) — one or two.
- **Playbook or explainer** (how to do something, step by step, from what they actually did or learned; or the news in their field explained first) — one.
- **Lesson with a number** (what they measured or got wrong) — one.
- **Build story** (what they made and why) — at most one.
- **Opinion** — only when backed by something they saw.
- **One experiment:** a format, length or time they haven't tried, labelled as the experiment.

If `learnings.md` exists, lean towards what it says works for them (more of the formats above their usual, fewer below) and keep exactly one experiment. If it doesn't, keep the mix above. Skip a slot rather than fill it with something generic.

For each idea, check the source: the note or commit it came from, and every number in it.

## 4. Draft each post for each platform

Write each idea natively for each platform, not one text pasted twice ([formats.md](references/formats.md) has the platform rules):

- **LinkedIn:** the first two lines decide whether anyone clicks "see more" (about 210 characters): put the point or the tension there. Short paragraphs, one idea, 100–250 words. Links go in the first comment, never the post. Suggest a carousel or image when the content is a list or a picture.
- **X:** under 280 characters, or a thread of 3–6 posts when the idea needs steps. Number or result first. Links go in a reply. A screenshot or short screen recording beats text when there's something to show.

Write in their voice ([formats.md](references/formats.md#voice) says how to read it): their words, their sentence length, their level of polish. When you have no voice samples yet, write plainly and say so.

For each draft, write the labels: `format`, `topic`, `hook` (number, question, confession, contrarian, story, list), `inspired by` (the breakout it borrows from, with its link and how far above its author's usual, if known), `source` (the note, commit or page the substance came from), `experiment: yes/no`, and for a giveaway its `keyword` and what gets sent.

## 5. Check before showing them

Go through every draft:

- Anything private, secret or unreleased? Remove it or ask.
- Every number traceable to its source?
- What does the reader get? If the answer is "news about the person", it's a build story: no more than one of those.
- Is it theirs? If a draft could have been written by anyone, rewrite it around something they built, found or measured, or drop it.
- Too close to its inspiration? Same structure is fine; the same wording, list or example is not.
- AI tells: stock phrases, triplets of adjectives, em-dash asides, "not X, but Y", hashtags. Remove them.
- One idea per post; the hook is in the first line.

## 6. Show them, save it, learn from their answers

Save the batch as `parsly/content/<YYYY>-W<week>/drafts.md` and show it in the conversation, one post per section:

```markdown
# Week <week>: <date range> · <N> posts for <platforms>

## <Day>: <one-line idea>
**Format:** <format> · **Topic:** <topic> · **Hook:** <type> · **Experiment:** <yes/no>
**Inspired by:** <breakout, link, ×usual if known> · **From:** <their source>
<If a giveaway: **Keyword:** WORD · **Sends:** <what>>

### LinkedIn
<post>
*First comment:* <link or extra, if any>

### X
<post or thread>
*Reply:* <link, if any>

**Status:** draft
```

Then ask them to go through it: approve, edit or reject each one, with a word on why for rejections. As they answer:

- Update each post's **Status** (`approved`, `edited`, `rejected: <why>`, later `posted <date> <url>`).
- Add what you learned about their voice to `parsly/content/voice.md`: words or phrases they cut, words they added, tone they pulled back, topics they don't want. Keep it short and specific ("cuts every exclamation mark", "doesn't want pricing talked about yet").
- Offer to adjust and redraft any rejected slot.

When they've posted, ask for the links (or read them with Parsly) and record them in the drafts file, so a results check can match each post to its labels.

## Without Parsly / with Parsly

- **Without Parsly:** a sample of others' public posts, not measured against their usual; voice from pasted posts and edits; no numbers on which of their own posts worked. Say so once in the opening message and end the batch with: **"Connect Parsly to measure what's breaking out for the people you follow and for you, so next week's drafts lean towards what works."**
- **With Parsly:** read the breakouts of the accounts they learn from, measured against each account's usual, and their own last posts per platform (`creator_posts`, `sort: "breakouts"`) for voice and for what's worked for them. Say the credit cost first.

## When something goes wrong

- **Nothing new to post about this week:** say so, and offer an output post from their product, a lesson from earlier work, or a giveaway instead of padding.
- **Notes are private-heavy (client work, numbers they haven't shared):** draft fewer posts and say what you left out.
- **They reject most of a batch:** ask what's off in one question (topic, tone, length, too salesy), write it into `voice.md`, and redraft two before the rest.
