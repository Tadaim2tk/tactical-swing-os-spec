# Dashboard Guide

DashboardはTactical Swing OSの研究結果を読むための中心画面です。自動売買画面ではなく、判断補助のための画面です。

> 毎朝の確認順序・ステータス解釈・異常時の一次対応は、本体repo
> `docs/operations_runbook.md` を正とする。原則は「土台（Data Health → 監査網）が
> 赤いまま中身を読まない」。偽の緑（false healthy / passed / fresh）の方が危険。

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

## Proposal Adoption / Weight History / Meta Learning / Auto Calibration / Human Override / Portfolio

提案のライフサイクルとメタ分析の補助レイヤー群。Proposal Adoption Trackingは提案が
採用/保留/却下/置換のどれになったかを追跡し、Weight Version Historyは承認済み重み変更を
版管理します（自動変更はしない）。Meta Learningはどの提案が成績を改善したかを分析し、
Auto Calibrationはより上位の較正候補を生成、Human Override Analyticsは人間の判断と
その後の結末を分析、Portfolio Layerは相関・集中・日次リスク予算などのポートフォリオ層
研究指標を提示します。すべて提案・分析であり、人間承認を前提とします。

## Prediction Calibration / Narrative Reliability / Transaction Cost

統計的健全性の表示層。Prediction Calibration (SPEC-BC-001) はAIの確信度を実績で採点
（Brier / BSS）。Narrative Reliability (SPEC-NQ-001) はナラティブの統計的価値を検定。
Transaction Cost (SPEC-TC-001) はネットR評価のための分析モデル（実コストは出典付きで
記入するまで status=unconfigured で理論値）。いずれも weights.json を更新しません。

## Audit Report / Narrative Lookahead Audit / Adversarial Review

監査網。Audit Reportは統合状態（PASS/WARNING）。Narrative Lookahead Audit (Phase 22) は
ニュース/AI要約への未来情報・評価結果の混入を検出（passed/warning/high_risk/blocked/
unavailable）。Adversarial Review (Phase 23) は提案レイヤーを横断レビューし、自動適用違反・
サンプル不足の強提案・過剰最適化・矛盾・過信表現を検出（提案が0なら passed ではなく
unavailable＝偽passed防止）。いずれも警告のみで自動適用しません。

## Data Health / Freshness

計器の健全性 (Phase 24)。各分析レイヤーの最終生成時刻・行数・鮮度を一覧化し、
`fresh / stale / empty / missing / unavailable / unknown_age / future_timestamp` に分類。
全体は `healthy / watch / degraded / critical`。「古い/空のデータを正常と誤読しない」ための
ガード。`critical` は失敗ではなく正直な異常表示。表示専用で weights.json を更新しません。
