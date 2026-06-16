# Roadmap

## Current Position

**Phase 25 completed.** （最終同期: 2026-06-16）

Tactical Swing OS は、日次分析・週次レビュー・月次較正・AI Feedback・News Narrative・
Dashboard・Model State Proposal・Safety Audit・Weights Patch（提案+人間レビュー）に加え、
提案採用追跡・重み履歴・メタ学習・自動較正候補・人間オーバーライド分析・ポートフォリオ層、
さらに統計的健全性（SG/RD/NQ/BC/DSR/TC）と**監査・品質トラック**
（Narrative Lookahead Audit / Adversarial Review / Data Health / Operational Runbook）まで到達。

到達点の3層:
- **計器**: 各分析レイヤー
- **監査網**: Narrative Lookahead Audit / Adversarial Review
- **計器の健全性**: Data Health / Freshness

KPI は EVALUATIONS 蓄積件数（目標: 100 → 300 → 1000）。

## Completed Phases

- Phase 1: Artifact-based daily cycle
- Phase 2: Google Sheets sync
- Phase 3: Sheets deduplication keys
- Phase 4: Sheets header repair
- Phase 5: Evaluation engine improvement
- Phase 6: Weekly review
- Phase 7: Weekly review from Sheets
- Phase 8: Monthly calibration
- Phase 9 / 9.1 / 9.2: Dashboard / Pages publishing / Japanese localization
- Phase 10 / 10.4: AI Feedback / JST timestamp display
- Phase 11 / 11.1: News narrative layer / conflict handling
- Phase 12: Pending re-evaluation and latest evaluation view
- Phase 13 / 13.1: Model State update proposals / safety audit
- Phase 14 / 14.1: Human-approved weights patch / human review
- Phase 15: Proposal Adoption Tracking
- Phase 16: Weight Version History
- Phase 17: Impact Measurement
- Phase 18: Meta Learning Layer
- Phase 19: Auto Calibration Candidates
- Phase 20: Human Override Analytics
- Phase 21: Portfolio Layer
- SPEC layers: SPEC-SG-001 / SPEC-RD-001 / SPEC-NQ-001 / SPEC-BC-001 / SPEC-DSR-001 / SPEC-TC-001
- Phase 22: Narrative Lookahead Audit
- Phase 23: Adversarial Review Agent
- Phase 24: Data Health / Freshness
- Phase 25: Operational Runbook & Spec Sync

## 番号の繰り延べ (renumbering)

旧ROADMAPは Phase 22 に **Cross Asset Regime Engine** を予定していたが、本セッションでは
監査・品質トラックを優先し Phase 22〜25 を再割り当てした。Cross Asset Regime Engine は
**未実装** であり、下記「Future Phases」へ繰り延べる。

## Next Target

これ以上レイヤーを増やすより、まず**運用実態を固める**段階。

### Phase 26 候補（運用 / 仕様の地固め）

- spec repo 同期の継続運用（本体 `docs/phase_status.md` を正とする）
- `config/cost_model.json` に XMTrading 実測コストを source 付きで記入 → ネットR有効化
  （現状 status=unconfigured）
- Narrative Lookahead / Adversarial Review の辞書・source分類を運用しながら調整

## Future Phases

### Cross Asset Regime Engine（旧 Phase 22、繰り延べ）

指数・USD・金利・ゴールド・オイル・ボラ・暗号資産のクロスアセット関係を解釈する
レジーム層。SPEC-RD-001（レジーム較正と忘却）の上に構築する。

### LLM-based Adversarial Agent

現在ルールベースの Adversarial Review に、LLM による反証エージェントを追加。
要 APIキー・課金、要 Narrative Lookahead 監査の前段（未来情報混入チェック）。

### EVALUATIONS Accumulation（継続）

実データが溜まると Data Health が healthy へ向かい、各統計ゲート（SG/DSR等）が本格稼働。
KPI 100 → 300 → 1000 件を追う。
