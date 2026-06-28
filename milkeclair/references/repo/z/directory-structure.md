# z: ディレクトリ構成

このreferenceを読むときは、このファイルだけで判断せず、関連するreferencesも必ず読むこと。

## 基本規則

最後のsegmentは関数名。直前までがnamespace。

- `z.a`は`lib/a/process.zsh`または`mod/a/process.zsh`
- `z.a.b`は`a`直下の関数なので`a/process.zsh`、`a/analysis.zsh`、`a/operator.zsh`
- `z.a.b.c`は`b`直下の関数なので`a/b/process.zsh`など
- `z.a.b.c.d`は`c`直下の関数なので`a/b/c/process.zsh`など

## ファイル種別

- 値を返す関数は`analysis.zsh`
- 状態更新や処理実行は`process.zsh`
- 真偽判定は`operator.zsh`

`analysis/process/operator`は階層ではなく、関数の性質。

## 禁止する形

- `z.job.run`があるのに、裏namespaceとして`z.job._run`を作らない。
- `z.job.run._child`のように、public namespaceの下位helperとして表す。
- directory名に`_`を含めない。

## テスト配置

テストは実装と同じ階層に置く。

- `lib/a/process.zsh` -> `test/lib/a/process_test.zsh`
- `lib/a/b/process.zsh` -> `test/lib/a/b/process_test.zsh`
- `mod/a/b/operator.zsh` -> `test/mod/a/b/operator_test.zsh`
