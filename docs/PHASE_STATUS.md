# Phase Status

Current Target: Phase 26 (next) — Phase 25 completed.

> 本体実装repo (tactical-swing-os) の `docs/phase_status.md` と同期。
> 最終同期: 2026-06-16（Phase 25 完了時点）。
> PR番号は実装repoの履歴に基づく。

| Phase | Status | PR | Merged | Notes |
|---|---|---|---|---|
| Phase 1 | completed | #1 | yes | Artifact-based daily cycle |
| Phase 2 | completed | #2 | yes | Optional Google Sheets sync |
| Phase 3 | completed | #3 | yes | Sheets deduplication keys |
| Phase 4 | completed | #4 | yes | Sheets header repair |
| Phase 5 | completed | #5 | yes | Weekly review generation |
| Phase 6 | completed | #6 | yes | Weekly review from Google Sheets |
| Phase 7 | completed | #7 | yes | Evaluation engine precision improvements |
| Phase 8 | completed | #8 | yes | Monthly calibration layer |
| Phase 9 | completed | #9 | yes | HTML dashboard generation |
| Phase 9.1 | completed | #10 | yes | GitHub Pages dashboard publishing |
| Phase 9.2 | completed | #11 | yes | Japanese dashboard localization |
| Phase 10 | completed | #12-#18 | yes | AI Feedback and Dashboard integration fixes |
| Phase 10.4 | completed | #19 | yes | JST timestamp display |
| Phase 11 | completed | #20 | yes | News narrative layer |
| Phase 11.1 | completed | #21 | yes | News conflict handling and Japanese summaries |
| Phase 12 | completed | #22-#28 | yes | Pending re-evaluation and latest evaluation view stabilization |
| Phase 13 | completed | #29-#31 | yes | Model State proposals and tabulate dependency fix |
| Phase 13.1 | completed | #32 | yes | Model State safety audit |
| Phase 14 | completed | #33 | yes | Human-approved weights patch proposals |
| Phase 14.1 | completed | #34 | yes | Weights patch human review |
| Phase 15 | completed | #35 | yes | Proposal Adoption Tracking |
| Phase 16 | completed | #36 | yes | Weight Version History |
| Phase 17 | completed | #37-#38 | yes | Impact Measurement (proposal_impact in meta learning) |
| Phase 18 | completed | #37 | yes | Meta Learning Layer |
| Phase 19 | completed | #40 | yes | Auto Calibration Candidates (datetime audit #39) |
| Phase 20 | completed | #41 | yes | Human Override Analytics |
| Phase 21 | completed | #42 | yes | Portfolio Layer |

## Statistical / Quant Hardening (SPEC layers)

旧ROADMAPには列挙されていなかったが、Phase 21 以降に統計的健全性を固める層を挿入。
いずれも `active (frozen)`。

| Spec | Layer | PR | Notes |
|---|---|---|---|
| SPEC-SG-001 | Statistical Guards (過学習ブレーキ) | #43 | n>=30 + 一標本t検定 p<0.05 + 増加はSharpe>0.5 |
| SPEC-RD-001 | Regime & Time Decay (忘却) | #44 | 半減期90日の指数減衰 |
| SPEC-NQ-001 | Narrative × Quant (Welch検定) | #46-#47 | ナラティブ信頼性ゲート + 月次較正統合 |
| SPEC-BC-001 | Prediction Calibration (Brier / BSS) | #48 | AI確信度の採点 |
| SPEC-DSR-001 | Deflated Sharpe Ratio (多重検定補正) | #49 | 選択バイアス割引で偽陽性セルを棄却 |
| SPEC-TC-001 | Transaction Cost (ネットR評価) | #50 | 証拠主義: コストは出典なしには採用しない |
| — | Integration / Dashboard 統合 | #45, #51 | main未到達チェーンの統合 |
| — | Dashboard Modularization | #52-#53 | io/summaries/render/build 分割 + `__main__`復元 |

## Audit & Quality Track (本セッション)

| Phase | Status | PR | Merged | Notes |
|---|---|---|---|---|
| Phase 22 | completed | #54 | yes | **Narrative Lookahead Audit** — ニュース/AI要約への未来情報・評価結果混入を監査 |
| Phase 23 | completed | #55 | yes | **Adversarial Review Agent** — 提案レイヤーの横断敵対監査（ルールベース） |
| Phase 24 | completed | #56 | yes | **Data Health / Freshness** — 計器の鮮度ガード（古い/空を正常と誤読しない） |
| Phase 25 | completed | #57 (+ spec sync PR) | yes | **Operational Runbook & Spec Sync** — 運用手順とフェーズ進捗の整理 |

## 番号についての注記 (divergence)

旧ROADMAPは **Phase 22 = Cross Asset Regime Engine** を予定していたが、本セッションでは
統計的健全性と**監査・品質トラック**（Lookahead / Adversarial / Data Health / Runbook）を
優先したため、Phase 22〜25 の番号をそちらに割り当てた。

旧予定の **Cross Asset Regime Engine は未実装** であり、将来フェーズ候補として
ROADMAP に繰り延べる（[ROADMAP.md](ROADMAP.md) 参照）。

Note: Pending entries may be updated after merge.
