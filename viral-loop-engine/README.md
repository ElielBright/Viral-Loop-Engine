# 🔄 Viral Loop Engine

> A data-driven content optimization pipeline built with [OpenClaw](https://openclaw.ai) — the open-source autonomous AI agent.

## The Problem

Content creators post blindly. They see engagement numbers but can't systematically extract **why** certain posts go viral and others flop. Even with analytics dashboards, the gap between raw data and actionable content strategy remains wide.

## The Solution

The Viral Loop Engine closes the feedback loop between **performance analytics** and **content creation** using a 3-skill OpenClaw pipeline:

```
📊 Analytics Data → [Skill 1: Data Analyst] → 🏆 Winning Posts
                      ↓
🏆 Winning Posts → [Skill 2: Pattern Architect] → 📋 Winning Playbook
                      ↓
📋 Playbook + New Content → [Skill 3: Strategic Creator] → 📱 Optimized Posts
```

## How It Works

### Skill 1: Data Analyst (`skills/data-analyst/`)
Parses your social media analytics and identifies the top 5% of posts using a **Weighted Engagement Rate (WER)** formula:

```
WER = ((likes × 1) + (comments × 2) + (shares × 3) + (saves × 2.5)) / impressions × 100
```

**Why weighted?** A share (3x) is worth more than a like (1x) because the reader is putting their reputation on the line. Comments (2x) indicate deeper engagement than passive likes.

**Input:** CSV/JSON analytics data with engagement metrics  
**Output:** Ranked Winning Case Studies with full metric breakdowns

### Skill 2: Pattern Architect (`skills/pattern-architect/`)
Reverse-engineers the winning posts across 5 dimensions:
- **Hooks:** How do winners open? (Bold claims, curiosity gaps, numbers)
- **Structure:** How is information paced? (Short punchy vs. narrative)
- **Tone:** What emotional register works? (Authoritative, vulnerable, provocative)
- **Content:** What topics and specificity levels win?
- **Platform signals:** What platform-specific patterns emerge?

**Input:** Winning Case Studies from Skill 1  
**Output:** Winning Playbook with 3-5 concrete, actionable rules backed by evidence

### Skill 3: Strategic Creator (`skills/strategic-creator/`)
Takes any new source content and "skins" it in the proven winning pattern. Generates platform-optimized variants:
- **LinkedIn:** Professional, spaced, 1,000-1,300 chars, ends with CTA question
- **Twitter/X:** Punchy, provocative, 280 chars, high opinion density
- **Instagram:** Personal, story-driven, hook in first 125 chars, 5-10 hashtags

**Input:** Winning Playbook + source content (URL, text, or idea)  
**Output:** 3 platform-optimized posts with rule citations

## Quick Start

### Prerequisites
- [Node.js](https://nodejs.org/) v22+
- [OpenClaw](https://openclaw.ai) installed globally
- [Ollama](https://ollama.ai) running locally (or any LLM API key)

### Setup

```bash
# 1. Install OpenClaw
npm install -g openclaw

# 2. Clone this repo
git clone https://github.com/YOUR_USERNAME/viral-loop-engine.git
cd viral-loop-engine

# 3. Run OpenClaw onboarding (select Ollama as provider)
openclaw onboard

# 4. Start the agent
openclaw start
```

### Usage

**Step 1: Feed your analytics**
```
You: "Analyze my social media analytics"
→ Paste your CSV data or point to a file
→ Data Analyst identifies your top-performing posts
```

**Step 2: Extract the winning formula**
```
You: "What patterns made these posts successful?"
→ Pattern Architect creates your Winning Playbook (3-5 rules)
```

**Step 3: Create optimized content**
```
You: "Create a LinkedIn post about [topic] using the playbook"
→ Strategic Creator generates platform-optimized posts following YOUR winning formula
```

## Project Structure

```
viral-loop-engine/
├── SOUL.md                          # Agent personality and identity
├── USER.md                          # User context and preferences
├── AGENTS.md                        # Operational rules and pipeline workflow
├── IDENTITY.md                      # Agent display name and emoji
├── README.md                        # This file
├── sample-analytics.csv             # Sample data (12 posts across 3 platforms)
└── skills/
    ├── data-analyst/
    │   └── SKILL.md                 # Skill 1: Analytics parsing and WER calculation
    ├── pattern-architect/
    │   └── SKILL.md                 # Skill 2: Pattern analysis and playbook creation
    └── strategic-creator/
        └── SKILL.md                 # Skill 3: Content generation with playbook rules
```

## Sample Data

The included `sample-analytics.csv` contains 12 social media posts across LinkedIn, Twitter/X, and Instagram with real-world engagement metrics. Use it to test the pipeline before connecting your own analytics.

## Tech Stack

- **Agent Runtime:** [OpenClaw](https://openclaw.ai) (open-source, local-first)
- **AI Model:** Ollama (local LLM — llama3.1, qwen2.5, or gemma4)
- **Configuration:** Markdown-based skill system (SKILL.md, SOUL.md, AGENTS.md)
- **Data Format:** CSV/JSON analytics input

## Why OpenClaw?

OpenClaw's skill system is perfect for this use case because:
1. **Modular skills** — each stage of the pipeline is a self-contained skill that can be improved independently.
2. **Local-first** — your analytics data never leaves your machine.
3. **Model agnostic** — works with Ollama (free, local) or any cloud API.
4. **Persistent memory** — the agent remembers your playbook across sessions.
5. **Hackable** — the entire system is defined in markdown files you can edit.

## License

MIT