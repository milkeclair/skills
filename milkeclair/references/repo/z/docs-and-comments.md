# z: docsとコメント

このreferenceを読むときは、このファイルだけで判断せず、関連するreferencesも必ず読むこと。

## docs

- public/privateに関係なく、全関数にdocsが必要。
- 外部に見せるdocsは英語。
- completionやhoverに出る説明も英語。
- README、helpも英語。

## 関数内コメント

- 関数内コメントは日本語。
- ただし既存ファイルが英語で統一されている場合は、その局所規約に合わせる。
- コードを見れば分かるコメントは書かない。

## 消してはいけないコメント

- `zls: ignore`はLSP制御コメント。不要コメントとして削除しない。
- shellcheck、lint、formatterも同じ。
- 削除前に、説明コメントか制御コメントかを分類すること。
