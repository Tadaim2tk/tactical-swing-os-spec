# Safety Rules

Tactical Swing OS is a research and analysis system. It is not an automated trading system.

## Prohibited

The following actions are prohibited.

- 実売買
- 発注
- XM操作
- 証券会社操作
- `generate_signal.py` 自動変更
- `weights.json` 自動更新
- GitHub Actionsからの自動git push
- Secretsや個人口座情報の表示
- Google Sheetsへの不要な書き込み
- 人間承認なしのpatch適用

## Allowed

The following actions are allowed.

- 分析
- 評価
- シミュレーション
- 提案
- レビュー
- 監査
- Dashboard表示
- Artifact生成
- CSV / JSON / Markdownレポート生成

## Human Approval

全変更はHuman Approval必須です。

特に以下は人間の明示承認なしに実行してはいけません。

- `weights.json` への反映
- ルール変更の採用
- Model State更新の採用
- Portfolio risk設定の変更
- 実運用に関わる設定変更

**人間による最終判断は、Tactical Swing OS内での発注許可を意味しない。**
実資金・発注・証券会社操作は本プロジェクトの範囲外であり、このworkflowには含めない。
人間の役割は研究上の採否とマージの判断に限られる。

## GitHub Actions Safety

GitHub Actionsは分析・生成・artifact保存・Pages公開に限定します。

GitHub Actionsからgit commit / git pushしてはいけません。

## Trading Boundary

Tactical Swing OSが生成するSignal、Proposal、Patch、Reviewはすべて研究用です。

Signalは発注命令ではありません。Proposalは自動採用されません。Patchは適用候補であり、`weights.json` 本体を更新しません。

## Audit Layer Invariants（監査・品質トラック）

Phase 22以降の監査レイヤー（Narrative Lookahead Audit / Adversarial Review / Data Health）
にも以下を適用します。

- 監査結果は**提案・警告のみ**。各 finding / summary に `requires_human_approval=true`、
  `weights_json_updated=false`、`generate_signal_updated=false` を固定で持たせる。
- **LLM API・有料APIは新規利用しない**。蓄積済みCSV/JSONのみを読む
  （ルールベースの監査。LLMベース敵対エージェントは将来フェーズ）。

## False Confidence を避ける（憲章思想）

最大の事故源は「分析が壊れる」ことより**「古い/空のデータを正常だと思って読む」**こと。

- **偽の緑を出さない**: false healthy / false passed / false fresh を避ける設計を優先する。
  - Adversarial Review: 提案が0でも「passed」ではなく `unavailable`（何もレビューしていない）。
  - Data Health: 古いデータは `stale`、空は `empty`、欠損は `missing` として正直に表示。
  - `critical` は「失敗」ではなく「正直な異常表示」。隠すより出す。
