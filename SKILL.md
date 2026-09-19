---
name: loop-resume-writer
description: "Chinese-first QA-loop resume skill for 中文简历与求职信 — JD-matched rewriting with a target-role gate, scored rubric QA, and a career-facts ledger that never invents experience. 适用于写中文简历、改简历、简历诊断打分、JD 匹配优化、STAR/CAR 简历成就句量化改写、求职信、一页简历压缩、平台搜索命中优化（Boss直聘/猎聘等）、秋招/社招/跳槽简历。只做真实经历的表达优化，不编造经历与数字。Do not use for interview answer prep（面试准备 → loop-interview-writer）, English-market ATS resumes, 在职周报/述职（→ loop-report-writer）, or LinkedIn profiles."
license: MIT
metadata:
  version: "0.3.2"
---

# Loop Resume Writer

## Overview

Use this skill to turn Chinese resume writing into a controlled loop instead of one-shot generation.

Default output language is Chinese unless the user requests another language.

Core workflow:

```text
Define -> Ledger -> JD Parse -> Mapping -> Draft -> QA Loop -> Polish -> Ship Check
```

This is an instruction-only skill by design. It ships no scripts or runner; all behavior lives in these instructions.

## Operating Principles

- Treat the resume as a claims document: every line is a claim that a recruiter may probe in an interview.
- **Ledger discipline**: all experience content comes from the career-facts ledger built from user input (`references/career-facts-ledger.md`). Every quantified point carries one of three source tags: user-provided / reasonable-inference (with stated basis) / `〔待补数据〕`. A `〔待补数据〕` slot must never silently become a concrete number.
- **Fabrication refusal**: if the user asks to invent experience, jobs, or numbers (e.g. "帮我编个实习", "写个大概的数据"), decline that goal, state the boundary, and offer the honest alternative: mining their real experience for under-expressed value. Do not silently produce fabricated content under a recited disclaimer. 本 skill 只做真实经历的表达优化，不编造经历与数字。
- Not an AI-detector-evasion tool. This skill improves resume quality and truthful expression; it does not target or optimize for passing any AI-content detector. If the user's explicit goal is "降 AI 率 / 检测不出来就行", decline that goal, state this boundary, and offer only the honest quality revision.
- Chinese job-search reality, not US ATS lore: the algorithmic layer that matters for most Chinese candidates is platform recommendation and recruiter keyword search (Boss直聘 etc.), not an auto-rejecting ATS. Do not sell ATS panic. See `references/evidence-notes.md` for what is evidenced versus practitioner consensus.
- When quantified data is missing, generate a follow-up question list for the user instead of inventing numbers.
- Ask clarification only when missing information blocks the task; ask no more than 3 questions.
- Stop after 2 full QA revision loops unless the user requests more (a gate-only fast iteration does not count).

Default assumptions:

- Target: a specific Chinese-market JD or role profile.
- Length: one page for new grads and candidates within ~5 years of experience; two pages allowed beyond that.

## Required Brief

Convert the request into a Resume Brief before touching the resume. Use `assets/resume-brief-template.md` when a structured template is useful.

```markdown
## Resume Brief

- Target role / JD:
- Candidate stage: 应届 / 1-5 年 / 5 年+ / 转行
- Delivery form: 平台在线简历 / 附件 PDF / 双形态
- Current resume: 有（原文）/ 无（从账本新建）
- Career-facts ledger: 已建 / 待建
- Constraints (page limit, sensitive items, gaps to address):
- Missing materials:
```

## Workflow

### 1. Define — Target-Role Gate

**Gate question: is there a concrete JD or a target-role profile?**

- No JD and no clear target -> run a gate-only fast iteration: build a role profile (industry / role / level, plus at least 1 real JD sample the user finds or provides). Do not edit the resume before the gate passes.
- Only a role title + salary band available (common on the hiring side) -> degrade: build a rough role profile from title and known role requirements, and mark "JD 正文缺失，按岗位画像粗匹配" in the output. Do not block on a missing full JD when a title is present.
- Gate passes -> record the target in the Brief.

If the request is a hiring-side / third-party review of someone else's resume (evaluate a candidate, "该不该约面"), switch to Resume Audit mode (`references/resume-audit-mode.md`) instead of the candidate-side loop.

### 2. Ledger

Build or import the career-facts ledger (`references/career-facts-ledger.md`).

- Every entry comes from user input. Classify quantified points with the three source tags.
- Missing numbers -> add to the follow-up question list (concrete questions such as "这个项目上线后转化率/耗时/成本变化是多少？"), keep `〔待补数据〕` in place.
- The ledger is reusable: offer to save it so loop-interview-writer can build interview answers from the same facts.

### 3. JD Parse

Extract from the JD: hard requirements, soft preferences, keyword set (skills, tools, domain terms as actually written), and level signals. Use `references/jd-mapping-guide.md`.

### 4. Mapping

Build the mapping matrix: ledger entries × JD requirements.

- Each hard requirement maps to ledger evidence, or goes into an explicit "无法覆盖" list. Never pad with invented or stretched claims.
- Surface the "无法覆盖" list to the user before drafting: they may have unlisted experience, or accept the gap.

### 5. Draft

Write Draft v1 from the mapping matrix, not from the old resume's ordering.

Style rules:

- Every bullet: action -> result, quantified where the ledger allows (`references/achievement-rewrite-patterns.md`).
- Specific nouns and verbs; no 「精通/熟悉/负责」 without evidence behind them.
- Reverse chronological; current role carries the most weight.
- Cut experience irrelevant to the target role rather than compressing everything equally.

Do not over-polish Draft v1. Strict QA after a rough draft reveals the real revision targets.

### 6. QA Loop

Grade with `references/resume-rubric.md` (or `assets/qa-scorecard-template.md`).

Order of checks:

1. Truthfulness audit first: every claim traceable to the ledger; every number carries a source tag; no `〔待补数据〕` turned into a concrete figure.
2. Then score the six dimensions (JD match & search hit / quantified achievement / truthfulness risk / structure & density / language / scan-friendliness).
3. For every deduction, cite the exact line.

Fatal issues:

- fabricated experience or numbers (including a `〔待补数据〕` slot silently filled)
- no quantified result anywhere
- irrelevant experience dominating the page
- bare skill-list claims (「精通 X」 with nothing behind it)
- unexplained timeline gaps
- a JD hard requirement neither covered nor declared in the 无法覆盖 list

Decision thresholds:

- Pass: total >= 85 and no fatal issue.
- Borderline: 82-84 and no fatal issue -> one targeted revision on the 2 lowest dimensions, then re-check.
- Revise: < 82 or any fatal issue.

**Hard stop after 2 full QA revision loops.** Track the count in every scorecard (`QA loop: 1/2`, `2/2`). At `2/2`, enter a Graceful Halt: output the best version, list unresolved flaws and the material gaps (usually missing numbers) that block them, and hand control back to the user.

### 7. Polish — Delivery-Form Fit

- 平台在线简历: keyword-search hit orientation — concrete stack and skill terms as recruiters search them (`references/platform-search-guide.md`; platform claims are practitioner-consensus grade, marked accordingly).
- 附件 PDF: scan-path orientation — current role and dates land in the first eye sweep; timeline continuity visible; one-page discipline enforced.
- Both forms share the same ledger facts; only emphasis and formatting differ.

### 8. Ship Check

```markdown
## Ship Check

- Target role fit: Ready / Needs revision
- Strongest section:
- Weakest remaining section:
- 无法覆盖 list status: (accepted by user / pending material)
- Follow-up questions still open:
- Truthfulness audit: clean / issues listed
- Suggested next step: (e.g. 用同一账本跑 loop-interview-writer)
```

## Output Modes

- Full Loop: Brief, Ledger, JD Map, Draft, QA Scorecard, Polished Version, Ship Check.
- QA Only: diagnosis + scorecard + fatal issues + revision rules for an existing resume; revised version only if requested.
- Rewrite Only: diagnosis summary, revision rules, rewritten version, Ship Check.
- One-Page Compression: cut to one page by target-role relevance, not uniform shrinking.
- Ledger Only: build and save the career-facts ledger for later use (including by loop-interview-writer).
- Cover Letter: generate 求职信 from a resume that has already passed QA, same ledger facts.
- Resume Audit (hiring-side / third-party): evaluate someone else's resume you cannot verify. Output an audit report + interview-probe list, not a rewrite (`references/resume-audit-mode.md`).
- Multi-Candidate Compare: several resumes for the same role at once — per-candidate audit, then a comparison table + differentiated probes + ranked recommendation (`references/resume-audit-mode.md`). Never compare across different roles.

Infer the mode from the request. Default to Full Loop for candidate-side creation, QA Only for an existing resume asking for diagnosis, Resume Audit for one candidate the user is evaluating, and Multi-Candidate Compare when several same-role resumes arrive together.

## References And Templates

**Actually read these files; do not reconstruct them from memory.** They hold calibrated anchors, the ledger schema, and evidence-graded claims.

Load only what the current step needs:

- `references/career-facts-ledger.md`: building or validating the ledger; the follow-up-question pattern; source tags.
- `references/jd-mapping-guide.md`: JD parsing and the mapping matrix.
- `references/resume-rubric.md`: QA scoring.
- `references/achievement-rewrite-patterns.md`: action->result rewriting.
- `references/platform-search-guide.md`: platform online-resume polish.
- `references/evidence-notes.md`: which screening/platform claims are evidenced vs consensus; cite honestly.
- `references/resume-audit-mode.md`: hiring-side / third-party review — audit rubric (with tenure dimension), probe-list output, interview handoff.
- `assets/resume-brief-template.md`, `assets/ledger-template.md`, `assets/qa-scorecard-template.md`: corresponding steps.
