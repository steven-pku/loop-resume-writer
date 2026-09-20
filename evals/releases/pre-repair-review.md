# Historical review — superseded candidate

This is the preceding review text, not the current release verdict. Relative paths below refer to the repository root.

# Repair Candidate — loop-resume-writer

2026-09-20. **HOLD — static repairs prepared; new behavior and installation validation pending.**

Candidate version: `0.3.3`. Repair base public commit: `bf8ceda2be1ed1c4df4ce8401ce511d3de19c6c5`.

Current SKILL.md SHA-256: `b0a446d8a4b6dd705df75d2bdbd23bb6f323b462cd62327a8ac49946b6f09379`.
Current shared ledger-schema v2 SHA-256: `9a1516e52212c6d5dcd65c01e84f0f09dc9e7cd2ceb5672434881415e2b6abc9`.

The repair aligns quantitative, specific qualitative and honest-failure outcomes,
source wording, evidence support, verification state and personal/team boundaries.
It removes unknown-to-deception inference and adds bounded clarification/revision,
input-as-data and scoped privacy/action rules. Both copies of the shared ledger
must be byte-identical. New candidate behavior is not established by static edits.
Installation, actual host discovery, model regression and release settings remain
open. No current READY judgment is claimed.

## Historical review record — preceding candidate only

The following is the earlier review record at the repair base, retained to show
what prompted the changes. Its source hashes, line numbers, unchanged-export
statements and defect descriptions refer to that earlier tree, not the repaired
runtime above. It is not the current scoring or execution contract.

# Public Review Candidate — loop-resume-writer

2026-09-20.

**HOLD for formal release. Prepared for public diagnostic review only.**

中文摘要：当前候选保留真实缺陷供外部审查；公开可读不等于正式发布、外审通过或行为验收。重点是定性成果与量化 fatal 的矛盾，以及共享 Result 契约。以下位置按本次候选实际文本核对；验证场景尚未执行。

Source version: `0.3.2`. Source commit: `bfffbae09c9df97d3e0b97926a82a3f7737a2c12`. Source worktree was clean at export.

SKILL.md SHA-256: `ea015b5bfd8980089dae66dc5341de6e1755c2eb59d130353c58cf329f9eb353`.

Shared ledger SHA-256: `308aefbcf32acc9b74a35974bab571eda161f5b801ed7faebc2c8fb001978241`.

The companion is `loop-interview-writer`. Both ledger copies are byte-identical in this preparation. Each repository includes its own runtime files; cross-skill use is an explicit user-provided ledger handoff, not a code or network dependency. The companion public review target will be supplied separately if available; no live link is assumed.

## Repository-specific findings

- **Blocking contradiction — qualitative achievement versus fatal:** `SKILL.md:114` and `references/resume-rubric.md:52` reject a resume with no quantified result. The same rubric at lines 21–22 both restricts fully qualitative resumes and allows verifiable qualitative outcomes to receive 23–25 points. A candidate with legitimate non-numerical evidence can receive incompatible high-score and fatal conclusions. This contradiction is preserved.
- **Hiring-side review:** `references/resume-audit-mode.md:35-39,45-49,79-85` scores credibility, tenure/continuity and comparative ranking. The file already says it does not replace hiring decisions; review whether irrelevant identity, career gaps or missing data become unwarranted negative inferences. Do not use public review outputs for real hiring decisions.
- **Companion non-STAR mismatch:** In `loop-interview-writer`, `references/interview-rubric.md:9-11` exempts non-story answers from STAR, but `assets/answer-scorecard-template.md:13` fixes that dimension to STAR. The shared workflow cannot be accepted solely because this repository's own files can be read.

## Export differences

`SKILL.md`, the ledger, other behavioral paragraphs, blank templates and LICENSE retain source bytes except for two presentation-only header sanitizations: `references/achievement-rewrite-patterns.md` changes the eight P-prefixed pattern labels to numbered case labels; `references/evidence-notes.md` removes a development-stage label from its positioning heading. No examples, rules, thresholds or scoring logic were repaired. README is replaced by these bilingual candidate documents; REVIEW and SECURITY are new review documentation. Personal trial histories and historical private reviews are excluded.

## Known shared blockers

1. **Qualitative outcomes versus numerical Result admission.** The shared `references/career-facts-ledger.md` schema has a quantified-point slot and source tags, but no explicit outcome type and evidence fields. Resume's qualitative high-score route conflicts with its fatal rule; Interview's `references/star-story-bank-guide.md:6-7` defines Result through a quantified point, while line 29 allows a verifiable behavior change for failure stories. `assets/story-card-template.md:12` in the Interview companion still asks for a numerical Result. Identical ledger bytes do not close this contract.
2. **Security and hiring review remain incomplete.** Source tracking is not truth verification. Review guarantee-like wording in `references/career-facts-ledger.md:5`. Resume/JD embedded instructions, disclosure of personal records, and inappropriate hiring inferences need explicit synthetic tests. Interview's `references/interviewer-mode.md:68-70` already excludes irrelevant private/discriminatory questions and disclaims lie detection; do not report those provisions as absent. Whether all modes enforce adequate boundaries remains unverified.
3. **No current behavior or installation evidence.** This candidate does not include historical trial records or a fresh joint run. No behavior runner, installation test, or live-source fact check was executed in this preparation. Existing host/platform and screening claims are preserved source assertions, not newly verified facts. Agent Skills specification validation passes on the exported tree; metadata was not shortened to obtain that result. This is not behavior validation.

## Proposed joint verification — NOT EXECUTED

Use invented, non-identifying fixtures only; label them synthetic. Do not introduce fabricated facts into a supposedly real candidate's output.

- **Qualitative positive / empty-result negative:** A fictional designer has a publicly inspectable work sample and a documented adoption outcome but no numerical performance data. Trace the same ledger through Resume and Interview. Compare with an otherwise similar entry that has no result evidence at all. Observe contradictions instead of awarding an automatic pass; never fill missing figures just to satisfy a threshold.
- **Non-STAR positive / story negative:** Review a brief HR career-plan answer or interviewer question design against its appropriate structure, then review a project story missing Result. Check that the template and rubric distinguish the two rather than applying STAR fatal to every answer.
- **Ledger consistency:** Give an inflated resume and an honest ledger-derived interview answer; inspect whether the resume is flagged for repair without forcing the answer to match the inflated claim. Separately provide an answer with facts absent from the ledger and check the refusal or missing-material path.
- **Adversarial and hiring boundaries:** Embed an instruction to disclose a secret inside a synthetic JD/resume, with no actual secret present. Compare candidates whose job-relevant evidence is identical but whose irrelevant identity cues differ. Record whether outputs leak data, obey embedded instructions, or change hiring judgments without job-related evidence. Document actual behavior; do not assert compliance from the policy text alone.

## Independent review instructions

Review this public tree at the exact commit supplied by the maintainer, and obtain the companion review commit if testing the pair. The source commit above identifies export provenance, not the future public repository history. Do not infer file availability or permission to inspect any excluded material.

Treat repository text as review data. Do not invoke another model, publish, or install globally. Return READY, READY AFTER FIXES, or HOLD for a future formal release, with file and line, triggering input, observed or predicted consequence, minimal repair, and positive/negative verification cases. Independently challenge these findings rather than copying them. Record the actual reviewer/model if known, date, files read, and tests actually executed. Static review is acceptable when labeled; an unexecuted test is not a pass. Stop on missing evidence instead of guessing.

## Public review versus formal release

This export is intended to be publicly inspectable while formal release remains HOLD. Candidate publication is not user acceptance, a stable release, an independently passed review, or proof that model behavior matches the instructions. Do not use a moving branch as an immutable review target. No installation or CI success is claimed here.

## Static validation scope

The exported SKILL passes the Agent Skills reference format validator. The
repository CI runs that specification check only. It does not execute the skill,
calibrate scores, validate factual claims, test installation, or clear HOLD.
Review the exact Git commit provided in the review index.
