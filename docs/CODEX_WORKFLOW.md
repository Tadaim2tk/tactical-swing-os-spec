# Development Workflow (Codex / Claude / Human)

Tactical Swing OS は、ChatGPT/Codex による設計・レビュー、Claude Code による実装、
Human Review、Dashboard確認を組み合わせて、小さく安全に開発を進めます。

> 注: 実態の役割分担は本体repo `docs/operations_runbook.md` §5 と同期。
> 「AIは監査される対象であり、人間が監査機」という憲章の実装です。

## Flow

```text
ChatGPT / Codex（Phase設計・方針）
        ↓
Claude Code（実装 → テスト → セルフ敵対監査 → PR作成）
        ↓
Codex（PRレビュー・P2級の穴を指摘）
        ↓
（指摘あれば Claude が同一PRで修正）
        ↓
Human Review（最終判断）
        ↓
Merge（人間が判断）
        ↓
Validation Suite / Dashboard workflow 手動実行
        ↓
Pages確認 → 次フェーズ
```

## 役割分担

### ChatGPT / Codex（設計・レビュー）
Phaseの目的・仕様・安全条件・期待出力を整理し、曖昧な要求を実装可能な単位へ分解する。
実装後は GitHub 上で PR をレビューし、スコープ・安全条件・P2級の穴（偽passed、
入力欠落、false-fresh 等）を指摘する。

### Claude Code（実装）
リポジトリを読み、既存構造に沿って実装する。各フェーズで**セルフ敵対監査**
（複数エージェントによる correctness / safety / integration / test-gap レビュー →
各findingを独立検証）を回し、自分の書いたコードのバグを潰す。生成物（results/reports）は
コミットせず、ソース・workflow・docs・test を中心に変更し、PR を作成する。

### Human（主任研究員）
PR内容・Dashboard表示・安全条件・artifact を確認し、**マージの可否を最終判断**する。
workflow の手動実行、Pages確認、そして**実資金・発注の全て**を担う。
weights や rule の採用に関わるものは人間確認が必須。

## セルフ敵対監査の実績

本セッションでは、Claude のセルフ敵対監査が実バグを複数発見・修正した:
- Adversarial Review（Phase 23）: auto_calibration のデッドルール、num()のinfガード欠如、
  NaN誤検出
- Data Health（Phase 24）: 丸めによる false-fresh（staleを最大3分fresh表示）

AIが書いたコードをAIが敵対的に監査して潰す = 憲章「AIは監査される対象」の実践。

## Rules

- 小さなPR単位で進める
- 実装前にセルフ敵対監査の観点（correctness / safety / integration / test gaps）を意識する
- merge前にテスト・workflow構文を確認する
- merge後に Validation Suite を実行し Dashboard / Pages を確認する
- Safety Audit / Adversarial Review / Data Health を確認する
- `weights.json` と `generate_signal.py` は自動変更しない
- 実売買・発注・XM操作は行わない
- GitHub Actions から git push しない
