# Current plans and completed results — October 19, 2026

Latest evidence: October 19, late evening Eastern. Deadline: **October 20, 11:59 p.m. Eastern**. This is a timestamped snapshot, not a live dashboard. [Sanitized machine-readable status](research/current_runs_public_20261019.json).

## Original full-length candidate: complete, strict objective failed

Training completed **5,625 finite updates / three epochs**, exactly **15K unique prompts and 45K presentations**, with all final model tensors finite. Evaluation job **1206228 completed successfully at 6:04 p.m. Eastern**, elapsed 6:42:08. All nine matched internal evaluations contain 1,974 records and eight samples each. The candidate passed **2/9 frozen integer gates: Minerva and GPQA**. Strict all-nine success was not achieved.

| Benchmark | Solved at pass@8 | Required gate | Pass@1 | Truncated samples | Gate |
| --- | ---: | ---: | ---: | ---: | --- |
| AMC | 24/40 | 33/40 | 35.00% | 60 | Failed |
| AIME 2025 | 5/30 | 8/30 | 6.67% | 87 | Failed |
| AIME 2024 | 5/30 | 8/30 | 6.67% | 99 | Failed |
| MATH | 428/500 | 451/500 | 64.00% | 377 | Failed |
| CN Math 2024 | 11/30 | 14/30 | 12.50% | 44 | Failed |
| Kaoyan | 135/199 | 138/199 | 29.40% | 176 | Failed |
| Minerva | 129/272 | 95/272 | 25.92% | 394 | Passed |
| OlympiadBench | 355/675 | 385/675 | 28.43% | 1213 | Failed |
| GPQA | 131/198 | 121/198 | 18.94% | 519 | Passed |

The native matched seven-task pass@8 macro is **49.62%**, versus **49.55%** for matched base (difference +0.074 percentage points). The seven tasks are AIME 2025, CN Math 2024, Kaoyan, AMC, Minerva, OlympiadBench, GPQA. This macro is not the nine-gate objective and is not a claim of historical runtime equivalence.

The complete manifest's non-model protocol, hardware, data hashes and problem identities match the frozen baseline. All nine individual artifacts were checked for expected identities and complete eight-sample fields. The driver produced paired question-cluster confidence intervals; these are per-task intervals without multiple-comparison adjustment:

| Benchmark | Pass@8 difference vs matched base, percentage points | Paired 95% CI, percentage points |
| --- | ---: | ---: |
| AMC | -17.50 | [-32.50, -5.00] |
| AIME 2025 | +3.33 | [-6.67, +16.67] |
| AIME 2024 | -6.67 | [-20.00, +6.67] |
| MATH | +0.40 | [-2.40, +3.20] |
| CN Math 2024 | +13.33 | [-3.33, +30.00] |
| Kaoyan | +11.06 | [+4.08, +17.68] |
| Minerva | -2.21 | [-6.99, +2.21] |
| OlympiadBench | +3.11 | [-0.30, +6.52] |
| GPQA | -10.61 | [-18.18, -2.53] |

CPU-only job 1210369 completed native aggregate verification for every benchmark, using the unchanged reporting definition for generation length and repeated eight-grams. [Aggregate diagnostics and paired confidence intervals](research/full_length_public_diagnostics_20261019.json) include no private source identities or responses. Per-task CIs and aggregate counts do not establish why the model failed.


| Benchmark | Mean output tokens | Mean repeated-eight-gram fraction |
| --- | ---: | ---: |
| amc | 13548.1 | 0.2034 |
| aime25 | 20700.3 | 0.3244 |
| aime | 22119.0 | 0.3557 |
| math | 7882.1 | 0.1269 |
| cn_math_2024 | 17309.0 | 0.2365 |
| kaoyan | 11234.3 | 0.1949 |
| minerva | 11494.9 | 0.2331 |
| olympiadbench | 14275.6 | 0.2251 |
| gpqa | 15834.0 | 0.4147 |

## Two new plans

**Stage 2 is complete:** job 1207378 ended successfully with exactly 750 finite updates / two epochs on 2,997 original examples and all final model tensors finite. Its benchmark accuracy remains **unmeasured**. The fixed parent development control solved 111/200 but truncated 331/1,600 samples, above the maximum 80. It therefore supplied no qualified control. The predeclared rule blocks both the Stage 2 development comparison and its terminal all-nine evaluation. No gate was relaxed and no replacement control was invented.

**Assistance training timed out:** job 1207518 reached its six-hour limit at 10:29 p.m. Eastern before the required 5,625 updates. The highest structurally complete native checkpoint is **4,400**, with all 4,400 loss/gradient records finite, all four RNG rank files and optimizer/scheduler/model files present, and all saved checkpoint model tensors CPU-verified finite. The interrupted checkpoint 4,450 lacks complete native recovery state and is preserved without adoption. **1,225 updates remain; this model has not been evaluated.**

CPU-only job 1210354 verified a review proposal for one four-B200, two-hour native resume. It would reassign eight unused Stage 2 evaluation GPU-hours while preserving the **97 GPU-hour total** and the assistance model's eight-hour final evaluation reserve. This is **not yet authorized**, and no recovery GPU job has been submitted. Scheduler-only tests currently do not demonstrate training plus full evaluation fitting the deadline. Estimates are provisional; an earlier eligible slot would still be required. Existing source responses, total schedule, loss, optimizer recovery and effective batch are preserved in the disabled proposal.

## Resource and publication boundaries

The original approved envelope remains **40 prior committed + 57 additional = 97 physical GPU-hours**, using conservative full-allocation charges. Failure or early completion does not reset that ledger. Blocked Stage 2 reserves are not automatically available for another training allocation; the review proposal needs explicit approval and renewed deadline feasibility.

All heavy audits, serialization, tensor scans, model/data hashing, tests and guarded admission modules execute on compute nodes or locally. Login nodes are used only for lightweight scheduler/file/log operations. After transient connection errors, IPv4 SSH worked; no VPN repair or causal network fix is claimed.

This public repository receives code and sanitized aggregates only. Private proposal originals, source/question IDs, authorization records, raw logs, detailed receipts, datasets and model weights remain excluded. The ordinary-SFT submission fallback is preserved. Hugging Face upload approval remains separate and outstanding.

[Implemented plans](TWO_PLAN_SETUP_20261019.md). Earlier dated report entries are historical and superseded by this snapshot.
