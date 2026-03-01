---
name: experiment-planning
description: change_logs.mdの振り返り、実装アイデアの生成(idea_generation)、およびアイデアの優先順位付け(idea_prioritization)を行う際に使用します。
---

# Experiment Planning & Idea Management

このスキルは、Kaggle/機械学習によるデータ分析での実験サイクル（仮説立案と優先順位付け）を管理・推進するためのものです。

## When to use this skill

- 過去の実験結果（`change_logs.md`）を振り返るよう指示されたとき
- 次の実装アイデアを生成・提案するよう求められたとき
- `ideas.md`に記載されたアイデアの優先順位付けや整理を行うとき

## Actions

### 1. reflect_on_change_logs (振り返り)
1. `change_logs.md` を読み込み、直近のバージョンでのスコアの推移（改善・悪化）を確認する。
2. 何の工夫がスコア向上に寄与したか、または悪化させたかを分析する。
3. 分析結果をもとに、次に取り組むべき方向性を `ideas.md` の末尾に追記する。

### 2. idea_generation (アイデア生成)
1. 改善に行き詰まった際、`scraps/summary.md`、`change_logs.md`、および現在の `ideas.md` を読み込む。
2. 既存のアプローチとは異なる視点（特徴量エンジニアリング、アーキテクチャ変更、ロス関数の変更など）から新しいアイデアを3〜5つ生成する。
3. 生成したアイデアを `ideas.md` に追記する。

### 3. idea_prioritization (優先順位付け)
1. `ideas.md` の内容を批判的に検討する。
2. データセットの特性やこれまでの実験結果から「本質的な改善につながらない」と判断されるアイデアは、理由を添えてコメントアウト（``）する。
3. 実装コストが低く、スコア向上の見込みが高い順にアイデアを並び替え、次のバージョンで実装するターゲットを1つ決定する。