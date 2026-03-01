---
name: research-and-scraps
description: scrapsフォルダ内の外部情報の要約(summarize_scrap)、およびWeb検索による新しいモデル改善アイデアの収集と追加(add_scrap), 深掘り調査のプロンプト生成(make_deepresearch_prompt)を行う際に使用します。
---

# Research & External Knowledge Management

このスキルは、KaggleのDiscussion、外部のNotebook、論文、ブログ記事などの知見を収集し、プロジェクトの改善アイデアとして活用可能な状態に整理するためのものです。

## When to use this skill

- ユーザーが新しい参考資料（PDF、Markdown、Notebook）を `scraps/` フォルダに追加したとき
- 現在のアプローチで行き詰まり、外部（Webや学習データ）から新しいアーキテクチャや特徴量のアイデアを探したいとき

## Actions

### 1. summarize_scrap (Scrapの要約)
1. `scraps/` フォルダ内に新しく追加されたファイル（`**/*.ipynb`, `**/*.md`, `**/*.pdf`）を読み込む。
2. その資料から、現在のプロジェクトに適用できそうな以下の要素を抽出する。
   - 有効な特徴量（Feature Engineering）の手法
   - モデルアーキテクチャやLoss関数の工夫
   - ハイパーパラメータのチューニング方針
   - 特殊な交差検証（CV）や後処理（Post-processing）の手法
3. 抽出した要素を整理し、`scraps/summary.md` に追記・更新する。情報が重複している場合は統合して見やすく整理する。

### 2. add_scrap (新規アイデアの検索と追加)
1. 現在のモデルの課題（例: 「特定のマイノリティクラスの精度が低い」「過学習が激しい」など）を明確にする。
2. Web検索機能（利用可能な場合）や自身の知識ベースを活用し、課題解決につながる新しいアプローチを調査する。
3. 有用な情報が見つかった場合、その内容をまとめたMarkdownファイル（例: `scraps/idea_handling_imbalanced_data.md`）を新規作成する。
4. 新規作成後、自動的に `summarize_scrap` の手順を実行し、`scraps/summary.md` に情報を反映させる。
5. （オプション）即座に試すべき強力なアイデアであれば、`ideas.md` にも提案として追記する。

### 3. make_deepresearch_prompt (深掘り調査のプロンプト生成)
1. 自身の検索能力を超えてより高度な調査エージェントに依頼するため、GeminiやChatGPTのDeepResearch機能を活用するためのプロンプトを生成する。プロンプトには以下の要素を含める。
   - 調査の目的と背景
   - 調査対象の具体的な内容（例: 「過学習を抑えるための新しい正則化手法」）
   - 期待するアウトプットの形式（例: 「有用な手法のリストと簡単な説明」）