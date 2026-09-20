# loop-resume-writer · Chinese Resume

> **PUBLIC REVIEW CANDIDATE — HOLD — NOT A FORMAL RELEASE.** The repair candidate changes instructions and still requires behavior validation. Use this tree for review and synthetic experiments, not as an accepted job-search or hiring tool. See [REVIEW.md](REVIEW.md).

English | [中文](README.md)

An instruction-only candidate for Chinese resume preparation: target-role gate, career-facts ledger, JD mapping, drafting, scoring, and bounded revision. A separate mode supports hiring-side review.

The `0.3.3` value in `SKILL.md` identifies the development baseline, not a stable release. Source tracking, refusal to fabricate, and bounded revision are instruction requirements, not guarantees about model behavior, factual truth, or hiring outcomes.

## Review first

This candidate repairs the shared ledger-schema v2, qualitative and honest-failure outcomes, evidence-state handling, bounded clarification/revision, input trust and privacy boundaries. Resume hiring review and Interview non-story handling remain subject to new behavior tests. No new behavior or installation pass is claimed by these edits.

Read [SKILL.md](SKILL.md), the relevant `references/`, and blank `assets/` templates. [REVIEW.md](REVIEW.md) provides issue locations and proposed verification scenarios. [SECURITY.md](SECURITY.md) describes sensitive-material and reporting boundaries. There is no runtime script or behavior-test runner; the repository workflow validates the skill format only. Installation, host compatibility, and first successful loading have not been verified in this preparation. File availability or static checks do not prove effective loading or correct behavior.

## Paired use

The companion candidate is `loop-interview-writer`, intended for joint public review; its remote availability is not assumed here. Both repositories include their own copy of `references/career-facts-ledger.md`. Those copies are byte-identical in this export, and each repository can be inspected independently.

The user explicitly carries the same ledger between skills; no automatic synchronization service is provided. Schema bytes and static alignment do not prove paired behavior. Use both frozen repair commits when testing the handoff.

## Evidence and privacy

No real resumes, personal career records, trial logs, or private review history are included. Export checks cover file identity, declared sanitization, and local references only. They do not prove scoring correctness, fabrication refusal, hiring fairness, or installation success.

Use synthetic or adequately de-identified review inputs. Do not submit identity documents, contact details, exact compensation, or identifiable third-party histories. The host and model provider may retain inputs or write files. Source tags cannot verify user-provided truth, and scores cannot replace hiring judgment or predict success. Instruction requirements and static checks are not guarantees of model behavior.

## License

[MIT](LICENSE), copied byte-for-byte from the source repository.
