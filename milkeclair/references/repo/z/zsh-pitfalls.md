# z: 落とし穴

このreferenceを読むときは、このファイルだけで判断せず、関連するreferencesも必ず読むこと。

## 特殊変数

次の名前を安易にlocal変数に使わない。

- `path`
- `status`
- `commands`
- `options`
- `functions`

`path`はPATHと結びつき、`status`はread-onlyな特殊変数。

## REPLYとstatus

- `REPLY`は多くのz関数が返り値として使う。
- `z.t.expect.status.*`や別helperの呼び出しで`REPLY`が上書きされる。
- 必要な`REPLY`は検証前に別変数へ退避する。
- 終了ステータスを見るhelperが引数を使うとは限らない。実装を確認する。

## fdとdaemon

- TCP socketもfdとして扱われる。
- 親子processでfdは同じsocketを指してもtableは別。
