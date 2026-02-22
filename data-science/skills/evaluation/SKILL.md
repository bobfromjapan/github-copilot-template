---
name: analyze-metrics
description: logs/内のログファイルやmetrics.json、reports/内の推論結果を読み込み、モデルの評価、過学習の兆候分析、弱点特定を行う際に使用します。
---

# Metric Analysis & Model Evaluation

このスキルは、実験終了後にモデルのパフォーマンスを客観的に評価し、次の改善アクションに繋げるためのものです。

## When to use this skill

- ユーザーが `versionN` の学習を完了し、結果の分析を求めたとき
- `reflect.py` を実行するか、ログファイルを直接読み込んでOverfittingの兆候を確認するとき

## Actions

### analyze_metrics (指標分析)
1. 対象バージョンの `logs/metrics.json` またはテキストログを読み込む。
2. Training LossとValidation Lossの推移を比較し、Overfitting（過学習）やUnderfitting（学習不足）の兆候がないか判定する。
3. `reports/` 内にクラス別の評価指標（Confusion MatrixやClassification Reportなど）がある場合、モデルが最も苦手としているデータクラスや傾向を特定する。
4. 分析結果（Overfittingの有無、弱点、次への課題）を簡潔にまとめ、対象バージョンの `memo.md` およびルートの `change_logs.md` に追記する。