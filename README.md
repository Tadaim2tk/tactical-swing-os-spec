# Tactical Swing OS Spec

Tactical Swing OSは、マーケットデータ、シグナル、評価、フィードバック、提案、監査、人間レビューを通じて、トレード仮説を継続的に検証する研究プロジェクトです。

このリポジトリは、Tactical Swing OS本体のコードではなく、設計思想、安全条件、ロードマップ、運用ルールを管理する仕様リポジトリです。

## 本リポジトリの目的

- Tactical Swing OSの設計思想を明文化する
- 安全条件と禁止事項を固定する
- Phaseごとの進捗と今後のロードマップを管理する
- Codex / ChatGPT / Human Review の運用ルールを整理する
- Dashboard中心の研究プロジェクトとして、判断根拠を残す

## tactical-swing-os本体との違い

`tactical-swing-os` 本体リポジトリは、Pythonスクリプト、GitHub Actions、Dashboard生成、CSV/JSON/Markdown artifact生成などの実装を管理します。

この `tactical-swing-os-spec` リポジトリは、実装ではなく仕様を管理します。設計判断、安全境界、Phase計画、レビュー方針、Dashboardの読み方を記録する場所です。

## 実売買システムではありません

Tactical Swing OSは実売買システムではありません。

- 実売買を行いません
- 発注を行いません
- XMや証券会社を操作しません
- `weights.json` を自動更新しません
- `generate_signal.py` を自動変更しません

## Dashboard中心の研究プロジェクト

Tactical Swing OSの中心はDashboardです。Dashboardは、Signals、Evaluations、AI Feedback、News Narrative、Rule Proposals、Model State Proposals、Safety Audit、Weights Patch Reviewをまとめ、人間が判断するための研究画面です。

すべての改善は提案・監査・レビューを経て、人間承認を前提に扱います。
