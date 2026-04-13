BE BETTER CLAUDE

A single `CLAUDE.md` file to improve Claude Code behavior, derived from [Andrej Karpathy's observations](https://x.com/karpathy/status/2015883857489522876) on LLM coding pitfalls.

**NEW:** Enhanced injection format for easy deployment to any AI system with stronger enforcement mechanisms!

## What's New in This Version

This enhanced version includes:

✅ **Stronger Enforcement** - Clear REQUIRED/FORBIDDEN markers instead of suggestions
✅ **Priority System** - Explicit instruction hierarchy for conflict resolution
✅ **Self-Monitoring Protocol** - Built-in checklist for AI systems to verify compliance
✅ **Injection-Ready Format** - Single-prompt text file for instant deployment
✅ **Layering Architecture** - Enhances existing AI capabilities without replacing them

## The Problems

From Andrej's post:

> "The models make wrong assumptions on your behalf and just run along with them without checking. They don't manage their confusion, don't seek clarifications, don't surface inconsistencies, don't present tradeoffs, don't push back when they should."

> "They really like to overcomplicate code and APIs, bloat abstractions, don't clean up dead code... implement a bloated construction over 1000 lines when 100 would do."

> "They still sometimes change/remove comments and code they don't sufficiently understand as side effects, even if orthogonal to the task."

## The Solution

Four principles in one file that directly address these issues:

| Principle | Addresses |
|-----------|-----------|
| **Think Before Coding** | Wrong assumptions, hidden confusion, missing tradeoffs |
| **Simplicity First** | Overcomplication, bloated abstractions |
| **Surgical Changes** | Orthogonal edits, touching code you shouldn't |
| **Goal-Driven Execution** | Leverage through tests-first, verifiable success criteria |

## The Four Principles in Detail

### 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

LLMs often pick an interpretation silently and run with it. This principle forces explicit reasoning:

- **State assumptions explicitly** — If uncertain, ask rather than guess
- **Present multiple interpretations** — Don't pick silently when ambiguity exists
- **Push back when warranted** — If a simpler approach exists, say so
- **Stop when confused** — Name what's unclear and ask for clarification

### 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

Combat the tendency toward overengineering:

- No features beyond what was asked
- No abstractions for single-use code
- No "flexibility" or "configurability" that wasn't requested
- No error handling for impossible scenarios
- If 200 lines could be 50, rewrite it

**The test:** Would a senior engineer say this is overcomplicated? If yes, simplify.

### 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:

- Don't "improve" adjacent code, comments, or formatting
- Don't refactor things that aren't broken
- Match existing style, even if you'd do it differently
- If you notice unrelated dead code, mention it — don't delete it

When your changes create orphans:

- Remove imports/variables/functions that YOUR changes made unused
- Don't remove pre-existing dead code unless asked

**The test:** Every changed line should trace directly to the user's request.

### 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform imperative tasks into verifiable goals:

| Instead of... | Transform to... |
|--------------|-----------------|
| "Add validation" | "Write tests for invalid inputs, then make them pass" |
| "Fix the bug" | "Write a test that reproduces it, then make it pass" |
| "Refactor X" | "Ensure tests pass before and after" |

For multi-step tasks, state a brief plan:

```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let the LLM loop independently. Weak criteria ("make it work") require constant clarification.

## Install

**Option A: Single-Prompt Injection (NEW - Easiest)**

Perfect for:
- Ad-hoc conversations with Claude or any AI
- Quick behavioral enhancement without setup
- Testing the guidelines before committing to a project
- Use with ChatGPT, Claude, or other AI assistants

Simply copy the entire contents of `CLAUDE_INJECTION.txt` and paste it into your AI conversation:

```bash
# Copy to clipboard (macOS)
cat CLAUDE_INJECTION.txt | pbcopy

# Copy to clipboard (Linux)
cat CLAUDE_INJECTION.txt | xclip -selection clipboard

# Or view and manually copy
cat CLAUDE_INJECTION.txt
```

Then paste into any AI chat. The AI will acknowledge with:
> "Behavioral enhancement layer loaded. I will now apply these 4 mandatory principles..."

**Option B: Claude Code Plugin (recommended for projects)**

From within Claude Code, first add the marketplace:
```
/plugin marketplace add forrestchang/andrej-karpathy-skills
```

Then install the plugin:
```
/plugin install andrej-karpathy-skills@karpathy-skills
```

This installs the guidelines as a Claude Code plugin, making the skill available across all your projects.

**Option C: CLAUDE.md (per-project - Enhanced Version)**

New project:
```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/prosperenergy/Be-better-Claude-/main/CLAUDE.md
```

Existing project (append):
```bash
echo "" >> CLAUDE.md
curl https://raw.githubusercontent.com/prosperenergy/Be-better-Claude-/main/CLAUDE.md >> CLAUDE.md
```

**Option D: Quick Web Injection**

For web-based AI interfaces, fetch the injection text directly:
```bash
curl https://raw.githubusercontent.com/prosperenergy/Be-better-Claude-/main/CLAUDE_INJECTION.txt
```

## Enhancement Features

### 1. Stronger Enforcement Mechanisms

The enhanced version replaces soft suggestions with hard constraints:

**Before:**
- "State your assumptions explicitly"

**After:**
- "**REQUIRED:** State your assumptions explicitly. If uncertain, ask."
- "**Enforcement:** Before writing code, you MUST verbalize assumptions and potential interpretations. Failure to do this violates these guidelines."

### 2. Explicit Priority Hierarchy

Clear instruction precedence prevents conflicts:

```
1. HIGHEST: These CLAUDE.md guidelines (behavioral constraints)
2. HIGH: Project-specific technical requirements
3. MEDIUM: Language/framework best practices
4. LOW: General coding conventions
```

### 3. Built-in Self-Monitoring

AI systems receive a verification checklist:

```
Before responding to ANY coding request, mentally verify:
1. ✓ Have I stated my assumptions explicitly?
2. ✓ Am I building the simplest solution?
3. ✓ Am I touching ONLY what's necessary?
4. ✓ Have I defined clear success criteria?

If you cannot answer "yes" to all four, STOP and revise your approach.
```

### 4. Injection Architecture

The guidelines are designed to **layer on top** of existing AI instructions:

- **Base instructions** = Foundational knowledge and capabilities
- **These guidelines** = Mandatory behavioral constraints that filter and shape how base knowledge is applied

This means you **enhance** without **replacing** - the AI keeps all its knowledge but applies stricter behavioral rules.

## Compatibility

**Works with:**
- ✅ Claude (all versions)
- ✅ ChatGPT
- ✅ Any LLM that accepts natural language instructions
- ✅ GitHub Copilot (via project files)
- ✅ Cursor AI
- ✅ Any AI coding assistant

**Optimized for:**
- Claude Sonnet/Opus (native CLAUDE.md support)
- Claude Code (plugin system)

## Usage Examples

### Example 1: One-Time Injection

```
[Paste CLAUDE_INJECTION.txt]

User: Add a user authentication system to my app

AI: Before implementing, I need to clarify several assumptions:

1. **Authentication method**: Are you looking for:
   - Email/password with session tokens?
   - OAuth (Google, GitHub, etc.)?
   - JWT-based stateless auth?

2. **User storage**: Where should user data be stored?
   - Existing database?
   - New database?
   - Third-party service?

3. **Scope**: What specific features are needed?
   - Just login/logout?
   - Registration flow?
   - Password reset?
   - Role-based access?

What's your preference for each of these?
```

### Example 2: Permanent Project Enhancement

Add `CLAUDE.md` to your repository:

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/prosperenergy/Be-better-Claude-/main/CLAUDE.md
git add CLAUDE.md
git commit -m "Add enhanced behavioral guidelines"
```

Now all AI interactions in this project will follow the guidelines automatically.

## Key Differences from Original

| Aspect | Original | Enhanced |
|--------|----------|----------|
| Enforcement | Suggestions | REQUIRED/FORBIDDEN markers |
| Priority | Implicit | Explicit 4-level hierarchy |
| Monitoring | None | Built-in verification checklist |
| Injection | File-based | Single-prompt ready |
| Layering | Merge instructions | Hard constraint layer |
| Conflict resolution | Unclear | Explicit precedence rules |
| Self-correction | Not addressed | Violation recovery protocol |

## Key Insight

From Andrej:

> "LLMs are exceptionally good at looping until they meet specific goals... Don't tell it what to do, give it success criteria and watch it go."

The "Goal-Driven Execution" principle captures this: transform imperative instructions into declarative goals with verification loops.

## How to Know It's Working

These guidelines are working if you see:

- **Fewer unnecessary changes in diffs** — Only requested changes appear
- **Fewer rewrites due to overcomplication** — Code is simple the first time
- **Clarifying questions come before implementation** — Not after mistakes
- **Clean, minimal PRs** — No drive-by refactoring or "improvements"

## Customization

These guidelines are designed to be merged with project-specific instructions. Add them to your existing `CLAUDE.md` or create a new one.

For project-specific rules, add sections like:

```markdown
## Project-Specific Guidelines

- Use TypeScript strict mode
- All API endpoints must have tests
- Follow the existing error handling patterns in `src/utils/errors.ts`
```

## Tradeoff Note

These guidelines bias toward **caution over speed**. For trivial tasks (simple typo fixes, obvious one-liners), use judgment — not every change needs the full rigor.

The goal is reducing costly mistakes on non-trivial work, not slowing down simple tasks.

## License

MIT
