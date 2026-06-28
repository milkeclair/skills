# AGENTS.md: git

このreferenceを読むときは、このファイルだけで判断せず、関連するreferencesも必ず読むこと。

## 基本ルール

- githubの確認には、ghコマンドを必ず使用する。

## worktree

基本的にすべてのプロジェクトはgit worktreeを使用する。その際、以下のルールに従うこと。

- 明らかに削除してはいけないブランチを削除しない。
  - ブランチ名の命名は既存のブランチを参考にし、規則性が分からない場合は、feat/short-descriptionの形式を使用する。
- worktreeに関しては、git.worktree.to関数を使用する。
  - 実態は~/.zsh/git/worktree.zsh。
- worktreeを使用した開発では、ポートの競合が良く起こる。
  - この時、z.wtproxyを必ず使用して、競合を起こさないようにすること。
  - z.wtproxy.helpで使用方法が確認できる。
  - ただし、z.wtproxyを使ったコードなどをコミットするのは禁止。
    - 絶対にやらないこと。
