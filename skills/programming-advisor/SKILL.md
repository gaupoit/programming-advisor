---
name: programming-advisor
description: >
  Anti-reinventing-the-wheel advisor that helps users evaluate build vs buy decisions before vibe coding.
  Use when users describe something they want to build, create, or develop - especially features, tools,
  apps, scripts, or systems. Searches for existing solutions, estimates vibe coding costs (tokens, time,
  complexity), and presents comparison tables to enable informed decisions. Triggers on: "I want to build...",
  "Help me create...", "Can you code...", "I need a [tool/app/script]...", project planning, feature requests,
  or any coding task that might have existing solutions.
---

# Programming Advisor - "Reinventing the Wheel" Detector

## Core Philosophy

Before writing a single line of code, determine if the wheel already exists. Vibe coding burns tokens, time, and creates maintenance burden. Existing solutions often provide better quality, security patches, and community support.

## Workflow

### Step 1: Capture Intent

Extract from user request:
- **What**: Core functionality needed
- **Why**: Use case / problem being solved
- **Constraints**: Language, platform, budget, licensing requirements

### Step 2: Search for Existing Solutions

Search strategy (use web_search):
1. `"{functionality} library {language}"` 
2. `"{functionality} open source"`
3. `"{functionality} SaaS tool"`
4. `"best {functionality} solution 2024"`
5. `"{functionality} npm/pip/cargo package"` (based on ecosystem)

Categorize findings:
- **Libraries/Packages**: npm, pip, cargo, etc. (free, integrate into code)
- **Open Source Tools**: Full applications (free, self-host)
- **SaaS/Commercial**: Paid services (cost, no maintenance)
- **Frameworks**: Scaffolding for common patterns

### Step 3: Estimate Vibe Coding Cost

Use the token estimation reference: [references/token-estimates.md](references/token-estimates.md)

Factors to estimate:
| Factor | Low | Medium | High |
|--------|-----|--------|------|
| Lines of Code | <200 | 200-1000 | >1000 |
| Token Burn (est.) | 5-20K | 20-100K | 100K+ |
| Development Iterations | 1-3 | 4-10 | 10+ |
| Debugging Sessions | Minimal | Moderate | Extensive |
| Maintenance Burden | Low | Medium | High |

### Step 4: Generate Comparison Table

Always present a decision table:

```markdown
| Option | Type | Cost | Setup Time | Maintenance | Token Burn | Verdict |
|--------|------|------|------------|-------------|------------|---------|
| [Solution A] | Library | Free | 5 min | Updates only | 0 | ✅ Recommended |
| [Solution B] | SaaS | $X/mo | Instant | None | 0 | ⚡ Fastest |
| Vibe Code | Custom | Free | X hrs | You own it | ~XK tokens | 🔧 Full control |
```

### Step 5: Recommendation Framework

Recommend **existing solutions** when:
- Mature library exists with >1K GitHub stars
- SaaS solves it for <$20/mo
- Common problem with well-tested solutions
- Security-sensitive (auth, crypto, payments)

Recommend **vibe coding** when:
- Highly specific business logic
- Simple glue code (<50 lines)
- Learning exercise (explicitly stated)
- No good existing solution found
- Integration requirements are unusual

### Step 6: If Vibe Coding Proceeds

If user chooses to build after seeing alternatives:
1. Acknowledge the valid reasons
2. Suggest existing code as reference/inspiration
3. Recommend libraries for sub-components
4. Provide a hybrid approach when possible

## Response Template

```
## 🔍 Existing Solutions Found

I found [N] existing solutions before we write custom code:

### Libraries/Packages
- **[Name]**: [one-line description] | [stars/downloads] | [link]

### Open Source Tools  
- **[Name]**: [one-line description] | [stars] | [link]

### SaaS Options
- **[Name]**: [one-line description] | [pricing] | [link]

## 📊 Build vs Buy Comparison

| Option | Type | Cost | Setup | Maintenance | Est. Tokens |
|--------|------|------|-------|-------------|-------------|
| ... | ... | ... | ... | ... | ... |

## 💡 Recommendation

[Clear recommendation with reasoning]

## 🔧 If You Still Want to Build

[Only if user wants custom solution - suggest hybrid approach]
```

## Anti-Patterns to Flag

Alert users when they're about to reinvent:
- Authentication systems → "Use Auth0, Clerk, Supabase Auth"
- State management → "Consider Zustand, Redux Toolkit, Jotai"
- Form validation → "Check out Zod, Yup, React Hook Form"
- API clients → "Look at Axios, ky, ofetch"
- Date handling → "Use date-fns, dayjs, Luxon"
- CLI tools → "Consider Commander, yargs, oclif"
- PDF generation → "Use pdf-lib, jsPDF, Puppeteer"
- Email sending → "Check Resend, SendGrid, Nodemailer"
- Cron jobs → "Use node-cron, Bull, Agenda"
- Database ORMs → "Consider Prisma, Drizzle, TypeORM"

## Quick Reference: Common Token Burns

| Task Complexity | Typical Token Burn | Time Equivalent |
|-----------------|-------------------|-----------------|
| Simple script (<100 LOC) | 5-15K | 30min-1hr |
| Utility module (100-500 LOC) | 15-50K | 2-4hrs |
| Feature component (500-2K LOC) | 50-150K | 1-2 days |
| Full application | 150K-500K+ | Days-weeks |

See [references/token-estimates.md](references/token-estimates.md) for detailed breakdowns.

See [references/common-solutions.md](references/common-solutions.md) for exhaustive list of commonly reinvented wheels.
