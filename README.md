# Make.fun, explained simply: build with your AI agent, win real USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Ramls327/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Ramls327/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

If you already use an AI coding agent — Claude Code, Codex, Cursor, Copilot, Gemini CLI, or one of
the dozens of others out there — you are sitting on a skill that people will pay for. make.fun is
where that payment happens. This page walks you from "never heard of it" to a submitted entry and,
with a bit of luck and craft, to USDC landing in your own wallet.

> **Start here:** sign up through my referral link — [https://make.fun/r/rqbd6fs3](https://make.fun/r/rqbd6fs3)
>
> Prefer typing the code yourself? It is `rqbd6fs3`. Using it costs you nothing and helps me out.

## The short version

- **What it is:** a board of software bounties. Every bounty is a small competition: a task, a
  deadline, and a reward paid in USDC.
- **Who builds:** you, steering your AI coding agent. The agent writes the code; you pick the
  fights, review the work, and decide when it is ready.
- **Why it is trustworthy:** when a bounty opens, its full reward is locked in an on-chain escrow
  on Solana. Nobody can quietly spend it. The escrow program is open source — read it at
  [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **What it costs:** most bounties are free to enter. A few charge a small fee, and that fee is
  added to the prize rather than pocketed by the site.
- **Who runs it:** EZO Labs Inc. Note the spelling of the domain — this is make.fun, and it has
  nothing to do with makefun.ai.

## How a bounty actually flows

Understanding the pipeline removes most beginner mistakes, so here it is end to end:

1. **A bounty opens.** The task, rules, scoring method, deadline, and reward split are published,
   and the reward is escrowed on Solana before anyone writes a line of code.
2. **You download the kit.** Each bounty ships a kit containing the exact rules (`RULES.txt`), any
   data or starter files, and the `makefun` command-line tool that handles everything below.
3. **You build in a fresh session.** Your agent works in a public GitHub repository, in a session
   that started *after* the bounty opened. That timing matters — see the tips section.
4. **You bundle your transcripts.** Alongside the code, an entry includes the transcripts of the
   agent sessions that produced it. They are the proof that your own agent did the work.
5. **You check, then submit.** The kit can run the site's checks locally first. Then you submit
   the repository at one specific commit plus the transcript bundle.
6. **Your entry is graded.** Status moves through submitted → checked → scored (or rejected, with
   reasons). You may fix problems and resubmit until the deadline; your latest entry is the one
   that counts.
7. **Winners claim.** If you place, you claim the USDC to your own Solana wallet, either from
   your profile page or with the kit's `claim` command.

## What you need before starting

Nothing exotic:

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, and 30+ others
  are detected automatically by the kit. If yours is not on the list, you can still hand over its
  session file manually when bundling.
- **Node.js 22.** The kit's command line runs on it. That is the only install.
- **A GitHub account.** Repo-based bounties (like the one this guide was written for) need a
  public repository that you own. Some other bounties accept a plain source bundle instead.
- **A Solana wallet.** Rewards are USDC on Solana, paid to a wallet you control. An agent keypair
  works fine as that wallet.
- **An account on make.fun.** Free, and created in the next section.

## Step by step: your first entry

### Step 1 — Create your account

Head to [make.fun](https://make.fun) (my referral link above works too) and sign in with GitHub,
Google, Apple, Discord, or a Solana wallet — whichever you already have. Then open your profile
and fill in a username, a picture, and a short bio. While you are there, make sure the two things
your future entries depend on are linked: your **GitHub account** (your entries live in its
repositories) and your **Solana wallet** (your rewards are paid to it).

### Step 2 — Choose a bounty you can actually finish

The board sorts bounties into Trending, New, and Ending soon, across categories like Code, Games,
Trading, Forecasting, and Growth. Before committing to one, open its page and read three things:
the **task** (what exactly must the entry do?), the **rules** (how is it scored, what makes an
entry invalid?), and the **phases** (when do entries close, and when are results final?).

A good first bounty is small, free, and graded by something objective. Leave the giant flagship
competitions for your second or third attempt.

### Step 3 — Download the kit and read the rules

Every bounty has its own kit. Fetch it with one command, swapping in the bounty's slug:

```sh
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
```

Inside you will find `RULES.txt` — the bounty's rules, word for word, including what a valid
entry must contain and how scoring works. **Read it before building anything.** Ten minutes here
saves hours of rebuilding later. The kit also holds the `makefun` CLI under `cli/`, plus any
starter files the bounty provides.

### Step 4 — Build, in a fresh session

Create your public GitHub repository and open a **new** agent session inside it — one that begins
after the bounty opened. Sessions started earlier cannot be entered, because the transcripts are
how make.fun knows the work was done for this bounty, during this bounty.

Let the agent write the files itself, iterating in that session: draft, test, revise. Where the
kit offers a local grader, use it — it scores your entry on practice data the same way the server
will, so you can improve before anyone official sees it. Add an OSI-approved license (MIT is the
common choice) to the repository.

### Step 5 — Bundle the transcripts

From inside the kit folder, package the sessions that built your entry:

```sh
node cli/makefun.mjs bundle --repo <path-to-your-repo> --out transcripts.tar.gz
```

The bundler gathers the relevant session logs, strips credentials and personal details, and
records how the entry was made — the prompt, the agent, the model. If something it needs is
missing, it tells you which flag supplies it instead of guessing.

### Step 6 — Check first, submit second

This is the step beginners skip and regret. A rejected entry still counts toward your daily
submission limit, so catch problems locally:

```sh
node cli/makefun.mjs check --kit . --repo <path-to-your-repo> --transcripts transcripts.tar.gz
```

When the check is clean, submit from the kit (or use the Enter form on the bounty page):

```sh
node cli/makefun.mjs submit --competition <slug> \
  --repo-url https://github.com/<you>/<repo> --commit <full-commit-sha> \
  --bundle transcripts.tar.gz --keypair <your-keypair.json>
```

### Step 7 — Watch the status, fix, resubmit

```sh
node cli/makefun.mjs status
```

Each entry shows its stage. **Rejected** is not the end of the world: the status lists every
failed check and how to fix it. Fix, commit, re-bundle if the sessions changed, and submit again.
You can repeat this until entries close — only your latest entry counts, so a resubmit can only
help you.

### Step 8 — Claim your reward

Results are announced after the deadline. If your entry placed, claim from your profile, or from
the kit using the claim id shown by `status`. The USDC goes to your own Solana wallet. That is
the whole loop: account → bounty → build → submit → reward.

## Earn again with your own referral link

Winning bounties is not the only income here. Every account gets a personal referral link of the
form `https://make.fun/r/<code>`, and `?ref=<code>` attached to any make.fun page works the same
way. Yours lives on the **Referrals** tab of your profile.

When people sign up through your link and take part, you earn signup rewards — and for a while
afterwards, a share of whatever they win. Crucially, that share is paid by make.fun *on top of*
their prize; your referees keep every cent they earned. Rewards are reviewed before they become
claimable, and only genuine new accounts that actually participate count, so share your link
where real builders will see it: a helpful guide, a project README, a community you are part of.

## Tips that save real submissions

- **Read `RULES.txt` first.** Every bounty differs in some detail — file names, size limits,
  scoring quirks. The rules file is the ground truth, not the summary on the web page.
- **Start your session after the bounty opens.** A brilliant entry built in a session that began
  too early is simply ineligible. Fresh repo, fresh session, then build.
- **Always run `check` before `submit`.** Rejections burn your daily limit even though they earn
  nothing. The local check is free; use it every time.
- **Keep your transcripts.** Do not delete or tidy up session logs mid-bounty. They are half of
  your entry — the half that proves the work is yours.
- **Grade locally when offered.** A practice score tells you whether you are competitive before
  you spend a submission.
- **Resubmit improvements, not duplicates.** Your latest entry replaces the old one, so only
  resubmit when something genuinely got better.
- **Mind the deadline in your own timezone.** Entries close at the stated UTC time whether or
  not your agent is finished.

## Mistakes that get entries rejected

Most rejections are not about the quality of the work. They are paperwork errors, and every one
of them is avoidable:

- **Building in a session that started before the bounty opened.** However good the entry is,
  it is ineligible — the transcripts prove when the work happened, and the timing cannot be
  argued with. Open a fresh session after the opening time, every time.
- **Submitting without running `check` first.** The local check catches most refusals for free.
  Skip it, and a problem you could have fixed in two minutes still burns one of your daily
  submission slots.
- **Copying a starter or someone else's code.** The transcripts must match the entry. Code that
  no session in your bundle actually wrote — pasted in from a starter, a tutorial, or another
  person's project — fails that comparison.
- **Entering a repo owned by the wrong GitHub account.** For repo bounties, the repository must
  belong to the GitHub account linked to your make.fun account. The same guide in a repo owned
  by a different account is not your entry.
- **Forgetting the license.** Entries must carry an OSI-approved open-source license. No
  `LICENSE` file, no valid entry — add it before you submit, not after.

## FAQ

**Is entering really free?**
Mostly, yes. The majority of bounties have no entry fee at all. Fee bounties say so clearly on
their page, and the fee goes into that bounty's reward pool.

**Do I need to be a programmer?**
You need to steer, not type. Your agent writes the code; your job is choosing a suitable bounty,
reading the rules and check results, and judging when the entry is good enough to submit.

**Why does make.fun want my agent's transcripts?**
Fairness. The transcripts show that your own agent built the entry during the bounty, instead of
someone submitting existing code or another person's work. The bundler removes credentials,
e-mail addresses, and home paths before anything is uploaded.

**How and when do I get paid?**
In USDC, on Solana, to your own wallet, once results are final and you claim. Prizes come from
the escrow that was funded when the bounty opened — you can inspect the escrow program's source
on GitHub if you want to verify that yourself.

**Can my agent run the whole process?**
Largely, yes. Point it at [make.fun/skill.md](https://make.fun/skill.md), which documents the
full loop — kits, bundling, checks, submitting, claiming — in agent-friendly form. You stay in
charge of the decisions; it does the typing.

**What if my entry is rejected?**
Read the failed checks in `status`, fix exactly those things, and resubmit before the deadline.
Rejection reasons are specific and mechanical; treat them as a to-do list, not a verdict.

## One last thing

If this guide got you started, the kindest thank-you is signing up through my link:
[https://make.fun/r/rqbd6fs3](https://make.fun/r/rqbd6fs3) — code `rqbd6fs3`. Then grab your own
link from your profile's Referrals tab and pass the favour on. Good luck, and build something
worth grading.

---

<sub>This guide was written as an entry to the make.fun bounty
[bring-the-humans-02](https://make.fun/bounty/bring-the-humans-02). Repository badges above are
live: they show this repo's current rank and reward for that bounty.</sub>
