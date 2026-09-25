# Swansea Scoop morning scan

A Claude Code routine that checks your sources every morning and emails
you a digest. It runs in Anthropic's cloud, so your laptop can be off.

Files:
- `morning-scan.md` — what Claude does each run (edit to change behaviour)
- `sources.md` — the source list (edit to add or drop sources)
- `allowed-domains.txt` — websites the cloud session is allowed to reach

## One-time setup (about 15 minutes)

1. **Put your email in.** In `morning-scan.md`, replace `YOUR_EMAIL_HERE`.

2. **Make a GitHub repo.** Create a private repo (e.g. `scoop-morning-scan`)
   and upload these files. Routines need a repo to work from.

3. **Create the routine.** Go to https://claude.ai/code/routines and click
   **New routine**.
   - Name: `Swansea Scoop morning scan`
   - Prompt:
     > Read morning-scan.md and sources.md in this repository and carry
     > out the morning scan exactly as described.
   - Model: pick a Sonnet model to keep usage down.
   - Repository: the one you just made.

4. **Let it reach your sources.** The default environment blocks most
   websites. Next to the environment name (under the prompt), open its
   settings, set **Network access** to **Custom**, and paste the contents
   of `allowed-domains.txt` into **Allowed domains**. Keep "Also include
   default list" ticked.
   (Shortcut: choose **Full** instead. Simpler, but less locked down.)

5. **Connectors.** All your connectors are included by default. Remove
   everything except **Gmail**. The routine can use any included
   connector without asking, and it doesn't need Beehiiv or Drive.

6. **Schedule.** Add a Schedule trigger: **Daily**, **06:30**. Times are
   in your local zone, and runs can start a few minutes late.

7. **Test.** Click **Run now**, then open the run and read the transcript.
   A green status only means it didn't crash, so check that the email
   arrived and look at the "Source health" section for URLs to fix.

## Tuning

- After the first run, fix any (check) URLs flagged as failing in
  `sources.md`, and add any failing domains to the allowed list.
- Getting too much? Tighten the planning criteria or delete sources.
- Getting too little? Add sources: a primary school cluster, a venue you
  cover often, a community centre with a what's-on page.
- Facebook and Instagram are deliberately left out. They block automated
  access, and scraping them breaks Meta's terms.

## Limits

Routines are in research preview and count against your Claude plan's
usage plus a daily run cap. One run a day is well within that. Details:
https://code.claude.com/docs/en/routines
