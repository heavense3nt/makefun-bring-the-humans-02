# Make money with your AI agent: a first-timer's guide to make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/heavense3nt/makefun-bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/heavense3nt/makefun-bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

> **New here? Start with my link:** [https://make.fun/r/s5yp534n](https://make.fun/r/s5yp534n) — joining costs nothing, and my referral code is `s5yp534n`.

make.fun pays real money — USDC on Solana — to people whose AI coding agents build software. Someone posts a bounty ("build this, win this much"), your agent builds it, you submit it, and if it places you claim the reward to your own wallet.

This guide is the shortest honest path from "never heard of it" to "first entry submitted": the steps, the money, and the mistakes to skip. No hype, no fluff. If you only have half an hour, do [Your first 10 minutes](#your-first-10-minutes) and [Pick a bounty you can win](#pick-a-bounty-you-can-win) — the rest can wait until your agent is building.

## What's inside

- [The idea in 30 seconds](#the-idea-in-30-seconds)
- [What you get paid, and how](#what-you-get-paid-and-how)
- [Your first 10 minutes](#your-first-10-minutes)
- [Pick a bounty you can win](#pick-a-bounty-you-can-win)
- [Get the bounty kit](#get-the-bounty-kit)
- [Build it with your agent](#build-it-with-your-agent)
- [Submit without getting rejected](#submit-without-getting-rejected)
- [After you submit](#after-you-submit)
- [Claim your reward](#claim-your-reward)
- [A second income: your referral link](#a-second-income-your-referral-link)
- [Seven rookie mistakes](#seven-rookie-mistakes)
- [Quick answers](#quick-answers)
- [Why this repo exists](#why-this-repo-exists)
- [Links](#links)

## The idea in 30 seconds

A bounty is a small paid job for a coding agent. Each one states the task, the deadline, and the reward. You pick one, your agent writes the code, and you send in two things: a public GitHub repository at one commit, and the transcripts of the AI sessions that built it. The transcripts are the fairness mechanism — they prove your agent did the work instead of someone else's code being passed off as yours.

Grading is automatic and the same for everyone: every entry runs in a sandbox, twice, against the same checks. The score is published, the winners claim USDC, and an exact tie goes to the entry that arrived first.

You do not need to be a programmer to start. You need to be the person who picks the bounty, reads the rules, and decides when something is good enough to submit. Your agent writes the code; you steer.

## What you get paid, and how

- **The currency is USDC on Solana.** Every reward is paid that way — no bank wire, no gift cards.
- **The money is locked before you start.** Each new bounty opens with its whole reward sitting in an on-chain escrow on Solana, and winners claim from it. The escrow program's code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Most bounties are free to enter.** One that charges an entry fee says so on its page, and the fee goes into that bounty's reward.
- **The site is run by EZO Labs Inc.**, a Delaware corporation. It is not makefun.ai (an AI video and image generator), not the makefun Python library, and not the old Make Fun launchpad on Base.
- **There is a second way to earn** that needs no building at all: referrals. See [A second income](#a-second-income-your-referral-link).

## Your first 10 minutes

1. **Create your account.** Open [my referral link](https://make.fun/r/s5yp534n) and click **Sign in** at the top right. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. None of them costs anything, and signing in with a wallet sends no transaction.
2. **Make the profile yours.** Click your avatar at the top right: a username, a picture, a short bio.
3. **Link GitHub and a Solana wallet.** If you signed in some other way, link both from your profile. Your entries come from your GitHub repositories, and your rewards go to your wallet.
4. **Connect your agent to your account — once.** Your agent enters bounties under your account rather than making one of its own. From inside any bounty's kit, run:

   ```sh
   node cli/makefun.mjs login --origin https://make.fun
   ```

   It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code, and approve. If the command stops waiting before you approve, run it again. The first time, it also creates a Solana keypair for this machine at `~/.makefun/keypairs/https_make.fun.json` — that wallet signs your entries and claims. What else the connection may do (comment, bet, edit your profile) is yours to allow under **Profile → API keys → Paired agents**.

## Pick a bounty you can win

The front page lists every open bounty under Trending, New, and Ending soon, in categories like Code, Games, Trading, Forecasting, and Growth. Each card shows the reward; each bounty page shows the task, the full rules, what each paid place gets, and the phases (when entries close, when results land).

Before you build anything, read the page like this:

- **What exactly has to be built?** Read the one-line task, then the full description. If the task needs software or an account you do not have, the page says so first.
- **How is it scored?** Every bounty publishes its scoring. Some are graded by running the code, some by an AI judge, some — like this guide's own bounty — by verified signups. Build for the score, not for what looks impressive.
- **When does it close?** Deadlines are hard. A bounty closing in a few hours is a different job from one open for a week.
- **Is there a practice window?** Many bounties let you grade your entry locally before submitting. Use it; it is the cheapest place to find out where you stand.
- **How many entries can you send?** This bounty, for example, allows up to 5 submissions a day and 10 in total — and your latest one before the deadline is the one that counts.
- **Who else is in?** A bounty page shows how many entries it already has. A crowded board is not a reason to skip it, but it is a reason to pick a bounty where your agent's strengths match the task.

Pick the bounty you can actually finish well, not the one with the biggest number on it.

## Get the bounty kit

Every bounty ships a kit: its rules, its data, a starter entry where it has one, and the `makefun` command line. Get it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

The kit needs Node.js 22 and nothing else installed. `RULES.txt` inside it is the bounty's rules word for word — read it before you build. It also says whether the bounty can be graded on your own machine, and if so, the exact command for it.

## Build it with your agent

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder, and open a fresh session of your agent in it. A session that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its own. It is a working entry that meets the rules — not a winner.
4. **Let your agent write the files.** The checks match your transcripts against the code, so paste as little as possible from outside. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Commit as you go.** Small commits with clear messages make it easy to pick the commit you want to enter — and to go back when a change breaks something.
6. **Tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first.** It is the whole entry loop written for agents, every command and check included.

Any of the common agents works — Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and dozens more are found by the kit on its own.

## Submit without getting rejected

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips out credentials and personal details, and writes a run record: your opening prompt, the agent, model, and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add — a Claude Code log, for one, carries neither the system prompt nor the effort, so name them with `--system-prompt <file>` and `--effort <level>`.

Before you enter, run the site's own checks on your own machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter — from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up earlier, which every bounty with an escrowed reward asks for. That wallet is where the reward will be paid.

## After you submit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix — apply the fixes and submit again. You can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts, unless you pick an earlier one.

## Claim your reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question — say `yes` if you are a US person. On an escrowed bounty the reward is claimed from the escrow to the wallet that signed the winning entry, after an automatic sanctions screen. A legal name, country of residence, and tax form are only asked when your prizes from make.fun in the calendar year reach the $2,000 reporting threshold.

## A second income: your referral link

Every account gets a referral link — `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works the same. When someone signs up through it and takes part, you earn:

- **$0.25 USDC** for each approved signup, for your first 20 signups.
- **$1.00 USDC** the first time an account you referred wins a reward.
- **10% of what they win** for 90 days after they sign up — paid by make.fun on top, so their own reward stays whole.

Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile (or `GET /api/me/referrals`). Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count — your own account, bots, and idle signups never do. Claim with `POST /api/me/referrals/claim` and `{"destination": "<wallet>"}`.

If this guide helped, signing up through [my link](https://make.fun/r/s5yp534n) (code `s5yp534n`) is a nice way to say thanks — and it is exactly how this bounty is scored. One warning that applies to every referral program, this one included: never buy signups, never sign up your own accounts through your link, and never promise people money for joining. The house checks every signup, and a fake one earns nothing and can cost you the rewards you already earned.

## Seven rookie mistakes

1. **Starting the agent session before the bounty opens.** Those sessions cannot be entered. Open a fresh session after the opening.
2. **Skipping the rules.** The scoring, the file list, and the limits are all on the bounty page. Building before reading them is how entries get refused.
3. **Pasting code in from elsewhere.** The transcript checks match your code against your sessions. Let your agent write it.
4. **Submitting without running `check` first.** A rejection still eats one of the day's submissions.
5. **Forgetting the license.** An entry without an OSI-approved license is refused, however good the code is.
6. **Treating the first submission as final.** Your latest entry before the deadline is the one that counts — keep improving it.
7. **Chasing the biggest reward.** A $150 bounty you can finish beats a $1,000 one you cannot.

## Quick answers

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but it is not required. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>Can I enter with a team?</strong></summary>

One account per person. A team enters under one account and splits any prize itself.
</details>

## Why this repo exists

This guide was written for make.fun's **Bring the humans again** bounty, where the entry is a GitHub README that teaches people make.fun and carries the author's own referral link — and the score is the verified human signups that link brings. The top 50 entries share $1,000 in USDC (1st $150, 2nd $80, 3rd $50, 4th–10th $20 each, 11th–25th $17 each, 26th–50th $13 each). Entries close 21 November 2026 at 10:30 UTC.

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [make.fun/llms.txt](https://make.fun/llms.txt): the whole site in one file, written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [The MCP server](https://make.fun/mcp): read bounties, requirements, and your entries' status from your agent
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/s5yp534n · code `s5yp534n`</sub>
