# Dashboard Guide

DashboardはTactical Swing OSの研究結果を読むための中心画面です。自動売買画面ではなく、判断補助のための画面です。

## Signals

Signalsは、日次で生成された市場仮説です。asset、side、rank、entry、SL、TP、reason_code、scoreなどを確認します。Signalは発注命令ではありません。

## Evaluations

Evaluationsは、Signalが評価期間内にどう推移したかを記録します。Entry、SL、TP、MFE、MAE、R multiple、outcome、error_typeを確認し、仮説が機能したかを検証します。

## Pending Re-Evaluations

Pending Re-Evaluationsは、まだ決着していないSignalを後日再評価するための結果です。初回評価時点でpendingだったものが、その後どうなったかを追跡します。

## Latest Evaluations

Latest Evaluationsは、EVALUATIONSとPENDING_REEVALUATIONSを統合したsignal_idごとの最新評価ビューです。Dashboardでは、可能な限りこの最新状態を優先します。

## AI Feedback

AI Feedbackは、シグナル、評価、市場状態、narrativeの整合性を振り返る補助レイヤーです。改善仮説を提示しますが、自動でルールやweightsを変更しません。

## News Narrative

News Narrativeは、RSSニュース見出しからrisk_on、risk_off、geopolitical_risk、inflation_pressureなどのテーマを分類します。方向予測ではなく、市場テーマの強さと混在状況を把握するための補助情報です。

## Rule Proposals

Rule Proposalsは、reason_codeやno_trade_reasonなどの分析から生まれるルール改善候補です。すべて提案であり、自動適用されません。

## Model State Proposals

Model State Proposalsは、asset、side、rank、type、reason_code、narrativeなどの重み調整候補です。`weights.json` の自動更新は行わず、人間レビューの材料として扱います。

## Safety Audit

Safety Auditは、Model State Proposalsが安全条件を満たしているかを確認します。blocked、warning、passedを表示し、blockedの場合は採用候補化を止めます。

## Weights Patch Review

Weights Patch Reviewは、Weights Patch候補をcandidate、hold、reject、blockedに分類します。candidateでも自動適用せず、人間がweight path、sample_count、根拠品質、deltaの大きさを確認します。
