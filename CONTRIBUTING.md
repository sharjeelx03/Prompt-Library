# 🤝 Contributing to PromptLibrary

Thank you for taking the time to contribute! PromptLibrary is a community-driven project and every contribution — big or small — makes a real difference.

Please read this guide carefully before submitting. It ensures a smooth review process and keeps the library consistent and high quality.

---

## 📋 Table of Contents

- [Ways to Contribute](#ways-to-contribute)
- [Before You Start](#before-you-start)
- [Prompt Submission Template](#-prompt-submission-template)
- [Workflow Submission Template](#-workflow-submission-template)
- [Resource / Guide Submission Template](#-resource--guide-submission-template)
- [File Naming Conventions](#file-naming-conventions)
- [Step-by-Step Contribution Process](#step-by-step-contribution-process)
- [Quality Standards](#quality-standards)
- [Community Guidelines](#community-guidelines)

---

## Ways to Contribute

| Type | Description |
|---|---|
| 🧠 Add a Prompt | Submit a new prompt to any category folder |
| ✏️ Improve a Prompt | Refine wording, add examples, or fix errors |
| ⚙️ Add a Workflow | Submit a multi-step AI workflow |
| 📖 Write a Guide | Add a tutorial or prompt engineering guide |
| 📊 Add a Benchmark | Compare prompt results across models |
| 🐛 Report an Issue | Flag a broken, outdated, or low-quality prompt |
| 💡 Suggest a Category | Propose a new folder or topic area |

---

## Before You Start

- Check if a similar prompt already exists to avoid duplicates
- Make sure your contribution fits into the correct folder
- Test your prompt on at least one LLM before submitting
- Follow the templates below exactly — PRs without proper formatting will be asked to revise

---

## 🧠 Prompt Submission Template

Create a new `.md` file inside the correct `prompts/<category>/` folder.

**File name format:** `kebab-case-descriptive-name.md`
Example: `debug-python-error.md`, `write-cold-email.md`

---

```markdown
# [Prompt Title]

## Metadata

| Field | Details |
|---|---|
| **Category** | e.g. Coding / Research / Writing / Business |
| **Difficulty** | Beginner / Intermediate / Advanced |
| **Models Tested** | e.g. ChatGPT, Claude, Gemini |
| **Author** | Your GitHub username |

---

## Description

<!-- What does this prompt do? What problem does it solve? 2-3 sentences max. -->

---

## The Prompt

```
[Paste your full prompt here. Use [BRACKETS] for variables the user should replace.]

Example variables: [TOPIC], [LANGUAGE], [TONE], [AUDIENCE]
```

---

## Example Usage

**Input:**
```
[Show a real filled-in version of the prompt]
```

**Output:**
```
[Paste a real example output from an LLM]
```

---

## Tips for Best Results

- Tip 1: ...
- Tip 2: ...
- Tip 3: ...

---

## Variations

<!-- Optional: List modified versions of this prompt for different use cases -->

- **Variation 1:** ...
- **Variation 2:** ...
```

---

## ⚙️ Workflow Submission Template

Create a new folder inside `workflows/` with a `README.md` inside it.

**Folder name format:** `kebab-case-workflow-name/`
Example: `workflows/research-paper/README.md`

---

```markdown
# [Workflow Name]

## Overview

| Field | Details |
|---|---|
| **Goal** | What this workflow produces |
| **Time Estimate** | e.g. 30–60 minutes |
| **Difficulty** | Beginner / Intermediate / Advanced |
| **Models Recommended** | e.g. GPT-4, Claude Opus |
| **Author** | Your GitHub username |

---

## When to Use This Workflow

<!-- Describe the use case. Who is this for? What problem does it solve? -->

---

## Prerequisites

- [ ] Requirement 1
- [ ] Requirement 2

---

## Steps

### Step 1: [Step Title]

**Goal:** What you're trying to achieve in this step.

**Prompt:**
```
[Paste the prompt for this step]
```

**Expected Output:** Describe what the LLM should return.

---

### Step 2: [Step Title]

**Goal:** ...

**Prompt:**
```
[Paste the prompt for this step]
```

**Expected Output:** ...

---

<!-- Repeat for all steps -->

## Final Output

Describe what the completed workflow produces.

---

## Tips

- ...
- ...
```

---

## 📖 Resource / Guide Submission Template

Place guides inside `resources/guides/` or `resources/tutorials/` or `resources/frameworks/`.

```markdown
# [Guide Title]

## What You'll Learn

- Point 1
- Point 2
- Point 3

---

## Prerequisites

<!-- What should the reader already know? -->

---

## Introduction

<!-- Brief intro paragraph -->

---

## [Section 1 Title]

<!-- Content -->

---

## [Section 2 Title]

<!-- Content -->

---

## Summary

<!-- Key takeaways in 3-5 bullet points -->

---

## Further Reading

- [Link title](URL)
- [Link title](URL)
```

---

## File Naming Conventions

| Type | Convention | Example |
|---|---|---|
| Prompt file | `kebab-case.md` | `summarize-research-paper.md` |
| Workflow folder | `kebab-case/` | `startup-validation/` |
| Guide file | `kebab-case.md` | `chain-of-thought-guide.md` |
| Benchmark file | `model-vs-model-task.md` | `gpt4-vs-claude-coding.md` |

---

## Step-by-Step Contribution Process

```
1. Fork this repository
       ↓
2. Clone your fork locally
   git clone https://github.com/YOUR-USERNAME/Prompt-Library.git
       ↓
3. Create a new branch
   git checkout -b add/your-prompt-name
       ↓
4. Add your file using the correct template
       ↓
5. Commit your changes
   git commit -m "feat: add [prompt name] to [category]"
       ↓
6. Push to your fork
   git push origin add/your-prompt-name
       ↓
7. Open a Pull Request on GitHub
   → Go to the original repo → Click "Compare & pull request"
   → Fill in the PR description clearly
       ↓
8. Wait for review — we'll respond within 3–5 days
```

---

## Quality Standards

To be accepted, your contribution must:

- ✅ Follow the correct template exactly
- ✅ Be tested on at least one LLM
- ✅ Include a real example output (not made up)
- ✅ Use `[VARIABLES]` for user-replaceable fields
- ✅ Be placed in the correct folder
- ✅ Use kebab-case file naming
- ✅ Not duplicate an existing prompt
- ✅ Be written in clear, concise English

Contributions that don't meet these standards will be asked to revise before merging.

---

## Community Guidelines

- Be respectful and constructive in all discussions
- Welcome contributors of all experience levels
- Give helpful feedback on PRs, not just approval or rejection
- Focus on quality over quantity
- Credit original sources if your prompt is inspired by existing work

---

## Questions?

Open an [Issue](https://github.com/sharjeelx03/Prompt-Library/issues) with the label `question` and we'll get back to you.

---

*Thank you for helping build the world's best open-source prompt library.* 🚀
