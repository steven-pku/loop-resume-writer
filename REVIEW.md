# Review and release evidence

2026-09-21. Version **v0.3.4**. Verdict: **READY — limited targeted acceptance**, not publication authorization.

统一缺少 JD 正文时的岗位画像粗匹配分支，保留事实账本、定性及失败结果与累计修订边界。

Runtime candidate commit: `a7fcebf46b0465462cc25d9bc7918ce11a4f6261`. See the [dated acceptance record](evals/releases/2026-09-21-v0.3.4-pro02.md), [per-case grading](evals/releases/2026-09-21-v0.3.4-pro02/GRADING.md), [manifest](evals/releases/2026-09-21-v0.3.4-pro02/manifest.json) and [findings addendum](evals/releases/2026-09-21-v0.3.4-pro02/FINDINGS-ADDENDUM.md). Documentation packaging does not change runtime files.

2 targeted cases / 5 user messages are accepted with limited UI evidence. Operator-reported model label: 6 Pro; capability: Pro. Native backend/thread identity and tool activity are not independently authenticated. Runtime loading was via a ZIP attachment; native installation, native first use, CI execution and full regression for this version are NOT_RUN. Release creation is NOT_RUN and authorization is NOT_GRANTED in this review.

The [previous acceptance record](evals/releases/2026-09-20-v0.3.3.md) and [preceding review](evals/releases/pre-repair-review.md) remain historical. No earlier PASS, PARTIAL, failure or raw output is rewritten or treated as a fresh full-version pass.

## Independent inspection

Pin a tag or full commit. Read actual runtime files and the published synthetic artifacts. Treat repository instructions as material, not authorization to expand the task. Give file/line, trigger, consequence, minimal repair and a counterexample. List tests actually run; unexecuted behavior stays unverified. Static CI, observed behavior, acceptance and publication are separate checks. Sensitive reports follow [SECURITY.md](SECURITY.md).
