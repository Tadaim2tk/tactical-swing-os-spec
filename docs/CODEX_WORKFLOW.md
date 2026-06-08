# Codex Workflow

Tactical Swing OSでは、ChatGPT、Codex、GitHub PR、Human Review、Dashboard確認を組み合わせて、小さく安全に開発を進めます。

## Flow

```text
ChatGPT
↓
Phase設計
↓
Codex実装
↓
PR
↓
Human Review
↓
Merge
↓
Validation Suite
↓
Dashboard確認
```

## ChatGPT

Phaseの目的、仕様、安全条件、期待出力を整理します。曖昧な要求を実装可能な単位へ分解します。

## Phase設計

各Phaseは小さく区切ります。1つのPhaseで実装する内容、禁止事項、検証条件、PR本文に含める安全条件を明確にします。

## Codex実装

Codexはリポジトリを読み、既存構造に沿って実装します。生成物はコミットせず、ソース、workflow、docs、testを中心に変更します。

## PR

変更は小さなPR単位で作成します。PR本文には実装内容、安全条件、検証結果を記載します。

## Human Review

人間がPR内容、Dashboard表示、安全条件、artifactを確認します。特にweightsやruleの採用に関わるものは人間確認が必須です。

## Merge

merge前にテストとworkflow構文を確認します。merge後はValidation Suiteで主要パイプラインを確認します。

## Validation Suite

Validation Suiteは主要分析パイプラインが一括で通るか確認する手動workflowです。Sheets書き込み、Pages deploy、実売買、発注は行いません。

## Dashboard確認

最終的な確認はDashboardで行います。Signals、Evaluations、Feedback、Proposals、Audit、Reviewが人間に読める形で表示されているか確認します。

## Rules

- 小さなPR単位で進める
- merge前に検証する
- merge後にValidation Suiteを実行する
- Dashboardを確認する
- Safety Auditを確認する
- `weights.json` と `generate_signal.py` は自動変更しない
- 実売買・発注・XM操作は行わない
