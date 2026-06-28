---
name: milkeclair
description: コードベースを参照する全ての依頼に使用する。コーディングに関係のある作業での不使用は認めない。
---

# milkeclair

作業時はこのファイルだけで判断せず、該当セクションのreferencesを必ず読むこと。
個別リポジトリの規約は`references/repo/`に置く。
対象リポジトリのreferencesがある場合は読むこと。

スキルを使用する場合は、ちゃんと読む。
指定されたスキルは全て使用する。例外は認めない。

## AGENTS.md

実装作業に入る前に、AGENTS.md相当のreferencesを必ず読む。

- `references/agents/*md`

## 作業フロー

`references/workflow.md`、`references/scope-control.md`を必ず読む。

## バグ修正

`references/reproduction.md`を必ず読む。
再現できていない原因に対して修正を始めない。

## リポジトリ規約

`references/repository-conventions.md`を必ず読む。

## テスト

`references/testing.md`を必ず読む。
テスト不要と明示された場合でも、構文確認、差分確認、副作用確認など、依頼に反しない検証を行う。

## 副作用

process、Docker、ユーザー設定領域、外部サービス、ネットワーク、生成ファイルに触れる場合は
`references/side-effects.md`を必ず読む。

## ツール運用

`references/tooling.md`を必ず読む。

## 完了前レビュー

`references/final-review.md`を必ず読む。
実装が終わったと思っても、触った全ファイルと関連docs/testを見返すこと。
