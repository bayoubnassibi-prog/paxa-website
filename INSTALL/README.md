# PAXA Claude Code System — Installation Guide
**For: Ayoub**
**Read this first. Follow every step in order.**

---

## WHAT THIS FOLDER CONTAINS

```
paxa-claude-system/
├── INSTALL/
│   └── README.md              ← you are here
├── .claude/
│   ├── agents/
│   │   ├── paxa-supervisor.md   ← master orchestrator (start here)
│   │   ├── paxa-seo.md          ← SEO specialist
│   │   ├── paxa-content.md      ← content creator
│   │   ├── paxa-ads.md          ← Meta ads specialist
│   │   ├── paxa-analytics.md    ← data & reporting
│   │   └── paxa-competitor.md   ← market intelligence
│   └── skills/
│       └── paxa-brand/
│           └── SKILL.md         ← brand context (auto-loaded)
```

---

## STEP 1 — INSTALL CLAUDE CODE

Open terminal and run:

**Mac/Linux:**
```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**Windows (PowerShell):**
```powershell
irm https://claude.ai/install.ps1 | iex
```

Then run `claude` and sign in with the Anthropic account.

**Requirement:** You need a Claude Pro ($20/month) or Max plan. Free plan will not work for agents.

---

## STEP 2 — CREATE YOUR PAXA PROJECT FOLDER

```bash
mkdir paxa-project
cd paxa-project
```

---

## STEP 3 — COPY THE AGENT FILES

Copy the entire `.claude` folder from this package into your `paxa-project` folder:

**Mac/Linux:**
```bash
cp -r paxa-claude-system/.claude paxa-project/.claude
```

**Windows:**
```powershell
xcopy /E /I paxa-claude-system\.claude paxa-project\.claude
```

Your folder should now look like:
```
paxa-project/
└── .claude/
    ├── agents/
    │   ├── paxa-supervisor.md
    │   ├── paxa-seo.md
    │   ├── paxa-content.md
    │   ├── paxa-ads.md
    │   ├── paxa-analytics.md
    │   └── paxa-competitor.md
    └── skills/
        └── paxa-brand/
            └── SKILL.md
```

---

## STEP 4 — INSTALL EXTERNAL SKILLS FROM GITHUB

These are free community skills that make the agents more powerful. Run these commands from inside your `paxa-project` folder:

### SEO Skills (priority — install this first)
```bash
git clone --depth 1 https://github.com/AgriciDaniel/claude-seo.git
cp -r claude-seo/skills/* .claude/skills/
rm -rf claude-seo
```

### Marketing Skills (Corey Haines — best marketing library)
```bash
npx skills add coreyhaines31/marketingskills
```
This installs: seo-audit, ai-seo, copywriting, ad-creative, email-sequence, content-strategy, analytics-tracking, competitor-alternatives, social, marketing-psychology

### SEO + GEO Skills (20 skills for search + AI search)
```bash
npx skills add aaron-he-zhu/seo-geo-claude-skills
```

### Content Research Writer (from ComposioHQ)
```bash
npx skills add ComposioHQ/content-research-writer
```

---

## STEP 5 — TEST THE SYSTEM

Navigate to your project folder and start Claude Code:

```bash
cd paxa-project
claude
```

Test each agent with these commands:

```
# Test supervisor
Use paxa-supervisor to plan this week's PAXA marketing tasks

# Test SEO agent
Use paxa-seo to find 10 keyword opportunities for paxapet.co.uk

# Test content agent
Use paxa-content to write 2 Instagram captions about the 40-minute cortisol peak

# Test ads agent
Use paxa-ads to write 3 Meta ad variations for the hook: "your dog isn't badly behaved"

# Test analytics (paste some fake numbers to test)
Use paxa-analytics to report on this data: 3 sales this week at £29 each, 0 refunds, 45% email open rate

# Test competitor agent
Use paxa-competitor to research what competing dog separation anxiety products exist in the UK
```

---

## STEP 6 — OPTIONAL: ENABLE AGENT TEAMS (PARALLEL WORK)

This lets multiple agents work simultaneously on big tasks. Add to `~/.claude/settings.json`:

```json
{
  "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
}
```

Then you can run:
```
Run the full weekly PAXA workflow using all agents
```

And all 5 agents will work in parallel and deliver a combined output.

---

## DAILY USAGE — CHEAT SHEET

| What you want | What to type in Claude Code |
|--------------|----------------------------|
| Plan the week | `Use paxa-supervisor to run the weekly PAXA workflow` |
| Write Instagram posts | `Use paxa-content to write 3 Instagram captions about [topic]` |
| Write a TikTok script | `Use paxa-content to write a TikTok script about [hook]` |
| Find keywords | `Use paxa-seo to find keywords for [topic]` |
| Audit the site | `Use paxa-seo to audit paxapet.co.uk` |
| Write Meta ads | `Use paxa-ads to write 3 ad variations for: [hook]` |
| Check competitor | `Use paxa-competitor to research UK dog anxiety competitors` |
| Analyze data | `Use paxa-analytics to report on: [paste data]` |
| Write a blog post | `Use paxa-content to write a 1500-word blog post about: [title]` |

---

## HAMZA'S USAGE (no coding needed)

Hamza can use Claude.ai (the web interface) for his tasks. He should paste the brand context from the paxa-brand SKILL.md file at the start of every conversation, then ask for:
- Reddit comment drafts for r/dogs, r/puppy101
- Facebook group responses
- Customer support email replies
- Community management scripts

---

## TROUBLESHOOTING

**"Agent not found" error:**
Make sure the `.claude/agents/` folder is inside your project folder, not in home directory.

**"npx skills not recognized":**
Install Node.js first: https://nodejs.org — then retry.

**Agent gives generic output:**
Make sure you're running `claude` from inside the `paxa-project` folder, not from a different directory. The agents only load when Claude Code detects the `.claude` folder.

**Skills not loading:**
Run `claude /skills list` to see what's installed.

---

## SUPPORT

If something breaks, send Youness a screenshot of the error message. Do not spend more than 30 minutes debugging alone — get help.
