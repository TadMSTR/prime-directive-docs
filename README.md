# Distributed AI Memory System for Multi-Project Work

A practical approach to managing context across multiple projects when working with Claude AI, optimized for ADHD/ASD cognitive patterns but useful for anyone juggling concurrent technical work.

## What Problem Does This Solve?

**If you:**
- Work on multiple technical projects simultaneously
- Hit token/usage limits trying to maintain context
- Re-explain the same preferences in every conversation
- Lose track of decisions when conversations compress
- Need external memory to compensate for working memory limits
- Want your AI context to persist across devices and sessions

**This system helps by:**
- Separating stable context (who you are) from project work (what you're doing)
- Isolating projects to prevent context bleeding and save tokens
- Making all context explicit and version-controlled
- Working across Claude.ai Web, Desktop, and Mobile
- Letting you refresh degraded context from a stable source

## How It Works

**Four-tier architecture, each with different persistence requirements:**

### Tier 0: Your Foundation (GitHub Repository)
Stable documentation about you - how you work, think, and communicate.

**What goes here:**
- Cognitive profile (ADHD/ASD patterns, learning style)
- Communication preferences (direct, code examples, minimal formatting)
- Technical context (infrastructure, tools, environment)
- Workflows (how you approach different types of work)
- Project custom instructions

**Why GitHub:**
- Version controlled (track changes over time)
- Accessible from any Claude instance
- Explicit (you write it, you control it)
- Portable (works anywhere, not locked to one platform)

**Example structure:**
```
your-repo/
├── profile/              # Who you are
│   ├── cognitive-style.md
│   └── communication-preferences.md
├── workflows/            # How you work
│   └── your-development-process.md
├── infrastructure/       # Your environment
│   └── setup-overview.md
└── project-instructions/ # Per-project context
    ├── project-a.md
    └── project-b.md
```

### Tier 1: Strategic Chat (Coordination)
One conversation for high-level thinking - routing between projects, meta-decisions, planning.

**Can degrade over time** (that's okay - principles matter more than details). Refresh from Tier 0 when needed.

### Tier 2: Project Chats (Execution)
Separate conversation per project - isolated contexts prevent cross-contamination.

**Each project loads:**
- Reference to Tier 0 (your preferences)
- Project-specific custom instructions
- Only that project's conversation history

**Result:** ~50-60% token savings per session, no context bleeding between projects.

### Tier 3: Code Repositories
Your actual implementations - version controlled, canonical source of truth.

## Real-World Results

**What this enabled:**
- Work on Docker backups, PowerShell tools, and personal projects simultaneously
- Jump between projects without re-explaining context
- Use Claude across desktop/web/mobile with consistent preferences
- Reduce cognitive load through clear boundaries and external memory
- Track how preferences evolve over time (git history)

**Token efficiency:**
- Before: All context loaded in every conversation
- After: Only relevant tier loaded per conversation
- Savings: ~50-60% tokens per project session

## Getting Started

### Step 1: Create Your Foundation Repository

**On GitHub:**
1. Create a new private repository (e.g., `claude-context`)
2. Clone it locally: `git clone git@github.com:yourusername/claude-context.git`

**Basic structure to start:**
```
claude-context/
├── README.md
├── profile/
│   └── communication-preferences.md
├── workflows/
│   └── how-i-work.md
└── project-instructions/
    └── README.md
```

**What to document:**

**In `profile/communication-preferences.md`:**
- How you prefer responses (direct, detailed, casual?)
- Code style preferences (comments, error handling, structure)
- What to avoid (excessive formatting, assumptions, certain patterns)

**In `workflows/how-i-work.md`:**
- Your development process (test-driven? Iterative?)
- Tools you use (languages, frameworks, environment)
- Constraints you work within (company policies, technical limits)

**Start small.** You don't need everything documented on day one. Add as you notice patterns.

### Step 2: Connect Claude to GitHub

**In Claude.ai settings:**
1. Go to Settings → Integrations
2. Add GitHub integration
3. Authorize access to your repository
4. Test: In any chat, say "Reference my [your-repo-name] repo"

**For Claude Desktop:**
1. Settings → Filesystem
2. Add your local repository directory
3. Test: Claude can now read your local files directly

### Step 3: Set Up Project Chats

**For each major project:**

1. Create a new Claude Project (or conversation)
2. Add custom instructions:

```
User context: [YourUsername]/claude-context

Project: [Project Name]
Purpose: [What you're building/doing]

Key patterns from my repo:
- See profile/ for communication preferences
- See workflows/ for my development process

This project: [Specific context for this project]
- Tech stack: [Languages, frameworks, tools]
- Current status: [Where you are in the project]
- Key constraints: [Important limitations or requirements]
```

3. Reference your main repo when needed: "Check my claude-context repo for [topic]"

### Step 4: Required Claude Settings

**Critical configuration:**

1. Go to Settings → Capabilities → Memory
2. **Enable:** "Search and reference chats" (allows past conversation access)
3. **Disable:** "Generate memory from chat history" (prevents automatic assumptions)

**Why these settings:**
- You control context explicitly (not AI extraction)
- Can search past conversations when useful
- No invisible memory creating errors

## Adapting to Your Needs

**This system is a template, not a prescription.** Adapt based on:

### Your Cognitive Style

**ADHD patterns (like mine):**
- External memory for working memory limits
- Clear project boundaries reduce decision fatigue
- Explicit documentation prevents "out of sight, out of mind"
- Version control shows what changed when (no mystery edits)

**Neurotypical patterns:**
- Might need less external structure
- Could use fewer tiers (combine 1 and 2)
- May prefer different organization

**The point:** Match the system to how your brain actually works.

### Your Work Type

**For developers:**
- Tier 0: Coding standards, preferred patterns, tech stack
- Tier 2: Per-project repos (backend, frontend, mobile)
- Tier 3: Actual code repositories

**For writers:**
- Tier 0: Style guide, voice, themes
- Tier 2: Per-book or per-client projects
- Tier 3: Draft repositories

**For researchers:**
- Tier 0: Methodology, citation style, focus areas
- Tier 2: Per-research-question projects
- Tier 3: Data and analysis repos

**For consultants:**
- Tier 0: Your expertise, approach, deliverable templates
- Tier 2: Per-client projects
- Tier 3: Client repositories

**My use case** (sysadmin/homelab):
- Tier 0: ADHD patterns, infrastructure, homelab context
- Tier 2: Docker backups, PowerShell tools, personal projects
- Tier 3: Script repositories

**Your use case will differ.** That's expected and fine.

### Scale to Your Needs

**Minimal version:**
- Single README.md with preferences
- One project chat
- Reference as needed

**Medium version:**
- Organized folders (profile, workflows)
- 2-3 project chats
- Regular updates

**Full version:**
- Complete documentation
- Multiple active projects
- Infrastructure context
- Workflow documentation
- Regular maintenance

**Start minimal, expand as you see value.**

## Common Adaptations

### Single Large Project
Don't need Tier 2 separation. Use Tier 0 for stable context, one chat for everything.

### Multiple Clients
Each client gets a Tier 2 project. Client-specific context isolated, your preferences consistent.

### Team Collaboration
Share sanitized Tier 0 docs with team (communication preferences, standards). Keep personal cognitive patterns private.

### Learning/Education
Tier 0: Learning goals, knowledge gaps, preferred explanation styles
Tier 2: Per-course or per-topic projects

## Why This Works Better Than Alternatives

### vs. Claude's Memory Feature
- **Memory:** Automatic extraction, invisible assumptions, no version control, global scope
- **This:** Explicit documentation, you control accuracy, git history, scoped per tier

[See comparison document for full breakdown]

### vs. Single CLAUDE.md File
- **CLAUDE.md:** Project-focused, single context, all-or-nothing loading
- **This:** Identity-focused, multi-project, load only what's needed per conversation

### vs. Manual Re-explanation
- **Manual:** Repeat yourself every conversation, waste tokens, forget details
- **This:** Write once, reference always, version controlled, consistent

## Maintenance

**Weekly (optional):**
- Review what worked/didn't in projects
- Update preferences if patterns changed
- Commit with message explaining why

**Monthly (optional):**
- Review project instructions (still accurate?)
- Archive completed projects
- Add new patterns you've discovered

**As needed:**
- Add new projects
- Update infrastructure context
- Refine communication preferences

**The system works even with minimal maintenance.** Updates are incremental, not required.

## Troubleshooting

**"Claude isn't referencing my repo"**
- Check GitHub integration is connected
- Try explicitly: "Reference my [repo-name] repo"
- Verify repo is private (if needed) or public

**"Context still feels scattered"**
- Are you using separate project chats? (Tier 2 isolation)
- Check if auto-memory is disabled (Settings → Memory)
- Consider whether projects are actually separate or related

**"Too much overhead"**
- Start smaller (just communication preferences)
- Don't document everything (just patterns you repeat)
- It's okay to add incrementally

**"Not sure what to document"**
- Notice when you repeat yourself
- Document that
- Build up over time

## Resources

**Documentation in this repository:**
- Casual overview: How this system emerged organically
- Technical deep-dive: Cognitive science parallels and design principles  
- Implementation report: How it was built and validated
- Memory comparison: Why explicit context beats automatic extraction

**Core concept:**
Separate memory by persistence requirements, not content type. Different context needs different longevity.

## Who This Helps Most

**This system is particularly useful if you:**
- Have ADHD/ASD and need external memory
- Work on 3+ concurrent technical projects
- Need context to persist across devices/sessions
- Want to understand what AI "remembers" about you
- Prefer explicit documentation over implicit behavior
- Work within token/usage limits
- Value version control for everything, including preferences

**You might not need this if:**
- Working on one project at a time
- Casual Claude usage
- Don't mind re-explaining context
- Prefer automatic over explicit
- Have excellent working memory

**It's a tool, not a requirement.** Use what helps, ignore what doesn't.

## Getting Help

**Questions or adaptations:**
- Open an issue in this repository
- Share how you've adapted it for your use case
- Suggest improvements

**Contributing:**
- Documentation improvements welcome
- Share your use case adaptations
- Help others implement their version

## License

Documentation shared freely under MIT License. Use, adapt, improve as needed.

---

**Bottom line:** If you work on multiple technical projects and Claude keeps losing context, separating by persistence requirements might help. It's worked for managing homelab infrastructure, work scripts, and personal projects simultaneously. Your mileage may vary - adapt to your needs.

*From "how do I backup my Docker containers" to "distributed memory architecture" in one week of asking the right questions.*
