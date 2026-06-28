# 副作用管理

このreferenceを読むときは、このファイルだけで判断せず、関連するreferencesも必ず読むこと。

## 事前確認

次に触れる場合は、作業前に副作用を列挙する。

- ユーザー設定領域
- state/cache/config/log
- daemon/background process
- Docker container/network/volume/image
- GitHubや外部API

## 隔離

- テストではグローバル変数を必要に応じて隔離する。
- ユーザー領域に書かない。

## 後始末

- daemonを起動したら停止を確認する。
- orphan processがないか確認する。
- Docker resourceを作ったら削除方針を確認する。
- ユーザー領域に生成物を作った場合は、隠さず報告し、削除可否を確認する。
- 明示的に自分が作った副作用で、削除してよいものは残さない。
