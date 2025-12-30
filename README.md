# Programming Advisor

A Claude Code skill that helps you make informed build vs. buy decisions before writing code.

## What It Does

This skill acts as a "Reinventing the Wheel" detector. When you describe something you want to build, it will:

1. **Search for existing solutions** - Libraries, open source tools, and SaaS options
2. **Estimate vibe coding costs** - Token burn, development time, maintenance burden
3. **Present a comparison table** - Side-by-side analysis of all options
4. **Make a recommendation** - When to use existing solutions vs. build custom

## Installation

### From Claude Code Marketplace

```bash
claude skill install @gaupoit/programming-advisor
```

### Manual Installation

Clone this repository into your Claude Code skills directory:

```bash
git clone https://github.com/gaupoit/programming-advisor.git ~/.claude/skills/programming-advisor
```

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

```
## Existing Solutions Found

I found 5 existing solutions before we write custom code:

### Libraries/Packages
- **pdf-lib**: Create and modify PDFs | 6.5K stars | npm

### SaaS Options
- **DocRaptor**: HTML to PDF API | From $15/mo

## Build vs Buy Comparison

| Option | Type | Cost | Setup | Maintenance | Est. Tokens |
|--------|------|------|-------|-------------|-------------|
| pdf-lib | Library | Free | 10 min | Updates | 0 |
| DocRaptor | SaaS | $15/mo | 5 min | None | 0 |
| Custom | Build | Free | 4-8 hrs | High | ~50K |

## Recommendation

Use pdf-lib for most use cases...
```

## Reference Files

- `references/common-solutions.md` - Exhaustive list of commonly reinvented wheels
- `references/token-estimates.md` - Detailed token burn estimates by task type

## Philosophy

> Before writing a single line of code, determine if the wheel already exists.

Vibe coding burns tokens, time, and creates maintenance burden. Existing solutions often provide:
- Better quality through community testing
- Security patches and updates
- Documentation and support

## License

MIT
