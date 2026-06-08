# Model Evolution

## Philosophy

Tactical Swing OSの目的は、単に予測を当てることではありません。

目的は、予測を継続的に検証し改善することです。

マーケット予測は不確実です。したがって、重要なのは一回の的中ではなく、仮説、評価、反省、改善提案、監査、人間レビューの循環を維持することです。

## Improvement Loop

```text
Signal
↓
Evaluation
↓
Feedback
↓
Proposal
↓
Audit
↓
Review
↓
Next Signal
```

## Signal

Signalは市場に対する仮説です。Entry、SL、TP、rank、reason_code、narrativeなどを含みますが、取引命令ではありません。

## Evaluation

EvaluationはSignalがどのように機能したかを検証します。Entry到達、SL、TP、MFE、MAE、R multiple、missed opportunityを記録します。

## Feedback

AI FeedbackやNews Narrativeは、Signalと市場環境の整合性を見直すための補助情報です。方向予測そのものではなく、仮説の文脈を補います。

## Proposal

Rule ProposalやModel State Proposalは、過去の結果から改善候補を生成します。提案は自動適用されず、人間レビューの材料です。

## Audit

Safety Auditは、提案が安全条件を破っていないかを確認します。blockedの場合、後続の採用候補化を止めます。

## Review

Human Reviewは、採用すべきか、保留すべきか、却下すべきかを判断するための段階です。ここでも自動適用は行いません。

## Next Signal

人間承認済みの改善だけが、将来のSignal生成に影響する候補になります。現段階では、すべての変更にHuman Approvalが必要です。
