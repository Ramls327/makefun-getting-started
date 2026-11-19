# Getting started on make.fun — a plain-English guide for first-timers

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Ramls327/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Ramls327/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

New here? Start with my invite: https://make.fun/r/rqbd6fs3
If the site asks for a code instead of a link, type `rqbd6fs3`.
It does not cost you anything extra, and it gives this guide a small boost.

This repository takes someone who has never entered an online coding
bounty and walks them, step by step, to a real submission on make.fun —
and, if the work is good enough, to a payout. You do not need to be a
professional developer: you need an AI agent, patience to read the rules
of the bounty you pick, and willingness to check your work before sending.

## What is make.fun, in one paragraph?

make.fun is a marketplace of small, time-boxed building contests.
Someone posts a task — write a program, build a tiny game, forecast a
number, produce an image, write a guide like this one — attaches a prize
pool, and sets a deadline. You and your AI agent build an entry, submit
it before the deadline, and get graded. Finish in the paid places and
you can withdraw USDC. Think of it less as a job board and more as a
series of sprints where the finish line, the judging method, and the
prize are all written down before the race starts.

## Why people trust the prize will actually be paid

Before a bounty opens, its prize money is deposited into an escrow
account on Solana. The money is visibly locked up front, not promised
afterwards, and winners draw from that escrow once results are final.
Most contests are free; any fee is stated openly and added to the pool.

## The life of a bounty, from open to payout

Every bounty follows the same broad arc:
1. **Open.** The task, rules, deadline, and prize split are published
   and the escrow is funded. Nothing you built before this moment can
   be entered — timing is part of the rules.
2. **Kit.** You download a small bundle for that specific bounty. It
   holds the authoritative rules, any starter files or data, and the
   command-line tool used for the remaining steps.
3. **Fresh-session build.** You start a brand-new agent session after
   the opening time and build the entry inside it. The session is your
   proof of when and how the work happened.
4. **Bundle.** You pack your code together with the transcripts of the
   sessions that produced it. Code alone is not a complete entry.
5. **Check, then submit.** You run the local checker first, fix what it
   flags, and only then submit one exact commit plus the bundle.
6. **Graded.** Your entry moves through checking and scoring. If it is
   refused, the platform lists the failed checks so you know what to fix.
7. **Claim.** Place in the paid ranks, and you claim USDC from the
   Solana escrow to your own wallet, from your profile or via the CLI.

## What you need on your desk before you start

Gather these four things first:
- **An AI agent.** A coding assistant you can direct in plain language
  — the kind that can create files, run commands, and revise its own
  work when you point out a problem. Your job is steering and judging;
  the agent does the typing.
- **Node 22.** The kit's command-line tool runs on Node. Install the
  current long-term release line (version 22) and you are set.
- **GitHub.** Repo-based bounties require a public repository under the
  GitHub account linked to your make.fun profile. Create the account
  early so linking is not a last-minute scramble.
- **A Solana wallet.** Prizes are USDC on Solana. You need a wallet you
  control so winnings have somewhere to land. Keep its keypair file
  safe and never paste its secret into a chat or a repository.

## Step by step: your first entry

### 1. Create your account

Visit make.fun and register using one of the sign-in options offered —
for example GitHub, Google, Discord, or a Solana wallet. Pick a
username, add a photo and a one-line bio, then open your identity or
profile settings and link the two accounts your entries will rely on:
GitHub (where your repos live) and Solana (where you get paid).

### 2. Pick a bounty you can finish

Browse the bounty board and filter for contests that are still open.
For a first attempt, favour a bounty that is free, has a clear and
narrow task, and is judged by an explicit score or checklist rather
than taste alone. Open the bounty page and read the task description,
the entry requirements, and both dates: when entries close and when
results are due. If you cannot describe in one sentence what a finished
entry looks like, pick a different bounty.

### 3. Get the kit — and actually read it

Each bounty distributes its own kit. Download it from the bounty page
or with the command the page gives you, then unpack it somewhere tidy.
Inside, find the rules document and read it completely before building.
Kits typically contain:

- the full rules for that bounty, including validity conditions;
- starter code, data files, or templates, when the bounty provides them;
- the `makefun` command-line tool under a `cli/` folder.

Rules differ between bounties in small but decisive ways — a required
file name here, a size limit there. The kit, not the web summary, wins
every argument.

### 4. Build — inside a fresh session

Create your public GitHub repository first. Many repo bounties expect
the repo to begin with the kit tool's initialisation step, which stamps
it with a freshness anchor proving it was created after the bounty
opened. Follow the kit instructions for that exactly.

Then start a new agent session — one whose first message comes after
the opening time — and build there. Work in stages: a first draft, a
test run, then a visible revision that improves something real. Single-
pass work tends to fail both the graders and the platform's own
originality checks, and staged work is simply better work.

Use any local grader or practice mode the kit provides. A practice
score is free information: it tells you whether to polish or to rethink.

### 5. Bundle your transcripts

When the entry looks ready, return to the kit folder and run its bundle
command, pointing it at your repository. The bundler collects the
session transcripts that wrote the entry, attaches run metadata (the
prompt, the harness, the model), applies redactions you specify, and
writes a single archive. If it refuses because something required is
missing — a session file, a system prompt, a usage record — read the
error, supply that exact piece, and run it again. Do not hand-edit the
archive to make an error go away.

### 6. Check before you submit

Run the kit's check command against your repo and bundle. Treat any
failure as a gift: it is the same family of checks the server will run,
discovered while fixing them still costs you nothing. A failed server
submission, by contrast, can consume part of your daily quota.

### 7. Submit one exact commit

Submit from the kit, naming the competition, your repository (by URL
for repo bounties, or by local source where the kit says so), the full
40-character commit hash you intend to enter, and your bundle file.
Double-check the hash: the commit you name is the commit that gets
graded, not whatever your repo happens to point at later.

### 8. Fix and resubmit if needed

Watch your entry's status. A rejection is a list of concrete problems,
not a final judgement on you. Fix exactly what failed, commit the fix,
re-bundle if your sessions changed, check again, and resubmit before
entries close. Your newest submission replaces the previous one, so a
resubmit should carry a genuine improvement or a real fix — not a
duplicate sent out of nerves.

### 9. Claim your USDC

After results are final, check whether you placed. If you did, claim
from your profile page or with the kit's claim flow, using the claim
code shown in your submission status. The USDC moves from the Solana
escrow to the wallet you linked. Confirm it arrived in your wallet
before you consider the bounty truly finished.

## Quick checklist to run through before you press submit

Copy this list into your notes and tick each item off, in order:

- [ ] My build session started after this bounty opened.
- [ ] My repository is public and owned by my linked GitHub account.
- [ ] An OSI-approved licence file (for example MIT) is committed.
- [ ] The commit I am entering is the one I actually tested.
- [ ] I re-ran the kit's local grader or check and it passes cleanly.
- [ ] My bundle was rebuilt after my most recent code change.
- [ ] No keypair, API key, or password appears anywhere in the repo.
- [ ] I have enough time left to fix one rejection and resubmit.

If any box stays unticked, fix that item first. Five quiet minutes with
this list have saved more entries than any clever last-minute rewrite.

## Referrals: the second way this site rewards you

Every account receives a personal referral link. Mine, used throughout
this guide, is https://make.fun/r/rqbd6fs3 with code `rqbd6fs3`. Yours
will be on the Referrals tab of your own profile once you sign up.

When a real person joins through your link and genuinely takes part,
you can earn a signup reward, and some bounties — including the one
this guide was written for — are scored directly on verified referral
signups. Referral rewards are reviewed before they become claimable,
and only authentic new participants count, so share your link where it
is actually useful: in a guide, a project README, or a community of
builders. Spam earns nothing and helps no one.

## Tips I wish someone had given me on day one

- Start the session after the bounty opens, every single time. An
  excellent entry from an early session is still ineligible.
- Read the kit's rules before writing a single file.
- Run check before every submit, not just the first one.
- Keep session files untouched while a bounty is live; they are half
  your entry.
- Commit in stages and write commit messages that say what changed.
- Convert deadlines to your own timezone and set an alarm well before.
- Spend resubmissions on measured improvements, not hope.
- Never commit secrets — keypairs, API keys, and passwords stay out of
  git, always.

## FAQ

**Do I have to pay to enter?**
Usually not. Most bounties are free. Any fee is stated on the bounty
page before you commit to anything.

**I am not a programmer. Can I still enter?**
Yes, if you can direct an agent clearly, read rules carefully, and
judge whether output matches the task. That steering role is the job.

**Why does the platform want my transcripts at all?**
To verify that your agent built the entry, during the bounty window,
in the sessions you bundled. It is an anti-copying measure, and the
bundler strips credentials and private details before upload.

**When and how am I paid?**
After grading is final and you claim: in USDC, on Solana, from the
bounty's escrow, to your own linked wallet.

**What happens if my entry is rejected?**
Open the status, read each failed check, fix those items, and resubmit
before the deadline. Rejection reasons are mechanical and specific.

**Can one entry be submitted to two bounties?**
Build and bundle per bounty — each contest has its own kit and opening
time, so treat each as its own project.

**How much time should a first entry take?**
Budget an afternoon: an hour to read and set up, a couple of hours of
staged building and local grading, and a final half hour for bundling,
checking, and submitting with time to spare before the deadline.

## Closing note

You now know the whole loop: account, bounty, kit, fresh-session build,
bundle, check, submit, fix if needed, and claim from escrow. The only
remaining step is doing it once, on a small bounty, end to end.

If this page helped you, consider starting through my link —
https://make.fun/r/rqbd6fs3 — code `rqbd6fs3` — and then pass your own
link onward in whatever you build. Good luck with your first entry.
