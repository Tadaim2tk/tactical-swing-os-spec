# Architecture

Tactical Swing OSは、予測を一度出して終わる仕組みではなく、予測、評価、再評価、分析、提案、監査、レビューを連結した研究用パイプラインです。

## 全体構造

```text
Market Data
↓
Signal Generation
↓
Evaluation
↓
Pending Re-Evaluation
↓
Latest Evaluation View
↓
Reason Analysis
↓
Rule Proposal
↓
Model State Proposal
↓
Safety Audit
↓
Human Review
↓
Dashboard
```

## Market Data

BTC、GOLD、WTI、USDJPY、SPX、NASDAQ、DXY、VIX、US10Yなどの市場データを取得し、OHLCVとmarket snapshotを生成します。分析の土台であり、実売買や発注には接続しません。

## Signal Generation

市場データからテクニカル指標、rank、entry、SL、TP、スコアを持つシグナルを生成します。これは仮説生成であり、取引命令ではありません。

## Evaluation

シグナルごとにEntry、SL、TP、MFE、MAE、R損益、missed opportunity、error_typeを評価します。目的は予測の正誤と改善材料を記録することです。

## Pending Re-Evaluation

まだ決着していないシグナルを後日再評価します。初回評価だけで判断せず、時間経過後の結果を蓄積します。

## Latest Evaluation View

EVALUATIONSとPENDING_REEVALUATIONSを統合し、signal_idごとの最新評価ビューを作ります。Dashboardや分析はこの最新状態を優先します。

## Reason Analysis

reason_codeやno_trade_reasonごとの成績を分析します。どの理由が有効で、どの理由が弱いかを見えるようにします。

## Rule Proposal

Reason Analysisなどをもとに、ルール改善候補を生成します。提案は自動適用されず、人間レビューの材料として扱います。

## Model State Proposal

asset、side、rank、type、reason_code、narrativeなどの重み調整候補を生成します。`weights.json` の自動更新は行いません。

## Safety Audit

Model State Proposalに対して、安全条件違反、過大delta、自動適用フラグ、データ不足などを監査します。blockedの場合は後続のpatch候補化を止めます。

## Human Review

Weights Patch候補をcandidate、hold、reject、blockedに分類し、人間が採用可否を判断するためのチェックリストを提供します。

## Dashboard

全パイプラインの結果を集約する研究画面です。Dashboardは判断補助であり、自動売買画面ではありません。
