# Quick Start Guide - Enhanced AI Injection

## 🚀 Fastest Way to Use (30 seconds)

1. **Copy the injection text:**
   ```bash
   cat CLAUDE_INJECTION.txt
   ```

2. **Paste into any AI chat** (Claude, ChatGPT, etc.)

3. **Wait for acknowledgment:**
   > "Behavioral enhancement layer loaded. I will now apply these 4 mandatory principles..."

4. **Start coding!** The AI will now follow enhanced behavioral guidelines.

---

## 📋 What You Get

After injection, the AI will **automatically**:

✅ **Ask before assuming** - No silent interpretation of vague requests
✅ **Keep it simple** - No unnecessary abstractions or features
✅ **Make surgical changes** - Only touch what's necessary
✅ **Define success criteria** - Clear verification steps for every task

---

## 💡 Example Usage

### Before Injection
```
User: Add user authentication
AI: [Immediately writes 500 lines with OAuth, JWT, session management,
     password reset, email verification, 2FA...]
```

### After Injection
```
User: Add user authentication

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

What's your preference for each of these?
```

---

## 📁 Installation Options

### Option 1: One-Time Injection (Easiest)
Copy `CLAUDE_INJECTION.txt` and paste into any AI conversation.

**Use when:**
- Quick tasks or experiments
- Testing the guidelines
- Working with different AIs
- No long-term project setup needed

### Option 2: Per-Project (CLAUDE.md)
Add to your repository:
```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/prosperenergy/Be-better-Claude-/main/CLAUDE.md
git add CLAUDE.md
git commit -m "Add behavioral guidelines"
```

**Use when:**
- Working on a specific project
- Want guidelines to persist across sessions
- Team collaboration (everyone gets same guidelines)
- Using Claude Code or Cursor

### Option 3: Claude Code Plugin
```
/plugin marketplace add forrestchang/andrej-karpathy-skills
/plugin install andrej-karpathy-skills@karpathy-skills
```

**Use when:**
- Using Claude Code
- Want guidelines across all your projects
- Prefer plugin management

---

## 🎯 The 4 Mandatory Principles

### 1️⃣ Think Before Coding
**Before** writing code, **MUST**:
- State assumptions explicitly
- Present multiple interpretations if ambiguous
- Ask when unclear

### 2️⃣ Simplicity First
**FORBIDDEN**:
- Features not requested
- Abstractions for single-use code
- Unnecessary configurability

### 3️⃣ Surgical Changes
**FORBIDDEN**:
- "Improving" adjacent code
- Refactoring unrelated code
- Changing existing style

### 4️⃣ Goal-Driven Execution
**REQUIRED**:
- Define success criteria before coding
- Specify verification method
- Create step-by-step plan with checks

---

## 🔍 How to Verify It's Working

You'll know the injection is active when you see:

✅ **Clarifying questions BEFORE implementation**
- Not: "I'll add that feature" → [writes code]
- But: "Before implementing, I need to clarify..."

✅ **Simpler code suggestions**
- Not: 200 lines with abstractions
- But: 50 lines that solve the problem

✅ **Surgical edits**
- Not: Reformats entire file while fixing bug
- But: Changes only the 3 lines needed

✅ **Explicit verification steps**
- Not: "I'll implement and test"
- But: "1. Write test → verify: fails with bug. 2. Fix code → verify: test passes"

---

## ⚠️ Troubleshooting

### AI not following guidelines?
1. **Re-inject** - Copy/paste `CLAUDE_INJECTION.txt` again
2. **Explicitly reference** - Say "Following the behavioral guidelines..."
3. **Point out violations** - "You're adding features I didn't request (violates Simplicity First)"

### Guidelines too strict for quick tasks?
The guidelines include a tradeoff note:
> "For trivial tasks (simple typo fixes, obvious one-liners), use judgment"

Say: "This is a trivial task, just fix the typo" - the AI will skip full rigor.

### Want to disable temporarily?
Say: "Temporarily suspend behavioral guidelines for this task"

---

## 🔄 Updating

To get the latest version:

```bash
# For CLAUDE.md
curl -o CLAUDE.md https://raw.githubusercontent.com/prosperenergy/Be-better-Claude-/main/CLAUDE.md

# For injection text
curl -o CLAUDE_INJECTION.txt https://raw.githubusercontent.com/prosperenergy/Be-better-Claude-/main/CLAUDE_INJECTION.txt
```

---

## 📚 Learn More

- **Full Documentation:** [README.md](README.md)
- **Examples:** [EXAMPLES.md](EXAMPLES.md)
- **Source:** [Andrej Karpathy's Tweet](https://x.com/karpathy/status/2015883857489522876)

---

## 💬 Quick Comparison

| Scenario | Without Guidelines | With Guidelines |
|----------|-------------------|-----------------|
| Vague request | Assumes and implements | Asks for clarification |
| Simple feature | 200 lines + abstractions | 50 lines, direct solution |
| Bug fix | Changes 20 files | Changes only affected lines |
| New task | "I'll do X, Y, Z" | "Plan: 1→verify, 2→verify, 3→verify" |

---

## License

MIT - Feel free to use, modify, and share!

Based on [Andrej Karpathy's observations](https://x.com/karpathy/status/2015883857489522876) about LLM coding pitfalls.
