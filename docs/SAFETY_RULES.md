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

## GitHub Actions Safety

GitHub Actionsは分析・生成・artifact保存・Pages公開に限定します。

GitHub Actionsからgit commit / git pushしてはいけません。

## Trading Boundary

Tactical Swing OSが生成するSignal、Proposal、Patch、Reviewはすべて研究用です。

Signalは発注命令ではありません。Proposalは自動採用されません。Patchは適用候補であり、`weights.json` 本体を更新しません。
