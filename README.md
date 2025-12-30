# Programming Advisor

A Claude Code skill that helps you make informed build vs. buy decisions before writing code.

## What It Does

This skill acts as a "Reinventing the Wheel" detector. When you describe something you want to build, it will:

1. **Search for existing solutions** - Libraries, open source tools, and SaaS options
2. **Estimate vibe coding costs** - Token burn, development time, maintenance burden
3. **Present a comparison table** - Side-by-side analysis of all options
4. **Calculate total cost of ownership** - Year 1 vs Year 3 costs for SaaS vs DIY
5. **Make a recommendation** - When to use existing solutions vs. build custom
6. **Plan the integration** - When you accept a recommendation, get complete setup instructions tailored to your project

## Installation

### As a Plugin (Recommended)

```bash
# Add the marketplace
/plugin marketplace add gaupoit/programming-advisor

# Install the plugin
/plugin install programming-advisor
```

### Manual Installation

Clone this repository:

```bash
git clone https://github.com/gaupoit/programming-advisor.git
cd programming-advisor

# Install as local plugin
claude --plugin-dir .
```

## Demo

Try the plugin with our sample project:

```bash
git clone https://github.com/gaupoit/dont-reinvent-the-wheel-demo.git
cd dont-reinvent-the-wheel-demo
claude
```

Then ask: *"I want to add form validation to my LoginForm component"*

## Usage

The skill triggers automatically when you describe something you want to build:

- "I want to build a PDF generator"
- "Help me create an authentication system"
- "Can you code a rate limiter?"
- "I need a CLI tool for..."

Or invoke it directly:

```
/programming-advisor
```

## Example Output

### Step 1: You ask to build something

> "I want to add form validation to my LoginForm"

```
## 🔍 Existing Solutions Found

### Libraries/Packages
- **Zod**: TypeScript-first schema validation | 35K+ stars
- **React Hook Form**: Performant form library | 41K+ stars

## 📊 Build vs Buy Comparison

| Option | Type | Cost | Setup | Maintenance | Est. Tokens |
|--------|------|------|-------|-------------|-------------|
| Zod + RHF | Library | Free | 15 min | Updates | ~2K |
| Custom | Build | Free | 1-2 hrs | High | ~15-30K |

## 💡 Recommendation

Use Zod + React Hook Form...
```

### Step 2: You accept the recommendation

> "Let's use Zod with React Hook Form"

```
## 🚀 Integration Plan: Zod + React Hook Form

### Your Project Context
- **Detected**: Next.js 14, pnpm, TypeScript
- **Project structure**: src/app/, src/components/

### Step 1: Install Dependencies
pnpm add zod react-hook-form @hookform/resolvers

### Step 2: Create New Files
📁 src/schemas/login.ts
[starter code with your schema]

### Step 3: Update Existing Files
📝 src/components/LoginForm.tsx
[integration code matching your style]

### ⚠️ Notes
- React Hook Form v7+ requires React 16.8+ ✅
```

## Reference Files

- `references/common-solutions.md` - Exhaustive list of commonly reinvented wheels
- `references/token-estimates.md` - Detailed token burn estimates by task type
- `references/integration-patterns.md` - Project detection and starter code patterns
- `references/pricing-data.md` - SaaS pricing and cost calculation data

## Features

### Build vs Buy Analysis
- Searches npm, pip, cargo, and other package ecosystems
- Finds open source tools and SaaS alternatives
- Estimates token burn for custom implementations
- Presents clear comparison tables

### Integration Planning (v1.1.0)
When you accept a recommendation, the plugin:
- **Detects your project** - Package manager, framework, TypeScript/JavaScript
- **Generates install commands** - Exact commands for npm/yarn/pnpm/pip/etc.
- **Creates starter code** - Matching your project's style and structure
- **Updates existing files** - Shows how to integrate with your current code
- **Warns about conflicts** - Version requirements and peer dependencies

### Cost Calculator (v1.2.0)
For significant decisions (auth, payments, email), get TCO analysis:

```
| Option | Setup | Monthly | Year 1 | Year 3 | Notes |
|--------|-------|---------|--------|--------|-------|
| Auth0 | 10min | $35 | $420 | $1,260 | Free: 7.5K MAU |
| Clerk | 10min | $25 | $300 | $900 | Free: 10K MAU |
| DIY | 8hrs | $0 | ~$1,500 | ~$2,100 | + maintenance |

💡 Break-even: DIY only cheaper at >100K MAU
⚠️ Hidden costs: Security audits, compliance, on-call
```

Includes pricing data for: Auth, Email, Payments, Database, Storage, Search, Monitoring, Analytics, AI/LLM, Cron jobs

## Philosophy

> Before writing a single line of code, determine if the wheel already exists.

Vibe coding burns tokens, time, and creates maintenance burden. Existing solutions often provide:
- Better quality through community testing
- Security patches and updates
- Documentation and support

## License

MIT
