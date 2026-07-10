# z: parser proof

このreferenceを読むときは、このファイルだけで判断せず、関連するreferencesも必ず読むこと。

## AST契約

- 全AST nodeの`kind`とend-exclusiveな`range`を検証する。
- tokenは各nodeへ持たせず、token tableからrangeで逆引きする。
- file rangeはsource全体、EOF rangeはsource末尾を表すことを検証する。
- `raw`を持つnodeでは`raw === source.slice(range.start.offset, range.end.offset)`を検証する。
- 全`WordNode`でpartsを連結したsource textが`raw`と一致することを検証する。
- lexerとparserのdiagnosticsなし、`UnknownNode`なしは必要条件であり、ASTの完全性の十分条件にしない。
- syntax ASTと`semantic`を分けて確認する。`local`などのcommand構造をsemanticへ置き換えない。
- `FileNode.comments`はfile全体の索引であり、個別nodeの所有関係を表すものとして判定しない。

## 回帰対象

最低限、次を局所testと全file検証の両方で確認する。

- 配列代入の括弧、空白、改行、comment、空配列、prefix assignment。
- `$1`、`$@`、`$?`、`$!`、`$$`、`$#`などの位置・特殊parameter。
- `${#name}`の`#`とcomment開始の区別、および後続の`&&`や`||`。
- nested parameter expansion、command substitution、arithmetic expansion。
- reserved command、opaque command、対応する終端、内部の終端名、後続redirect。
- DocBlockとinline comment、unknown delimiter、欠落した終端。
- command name、argument、assignment、redirect、semanticの責務分離。

testはgrammarまたはparser責務ごとに配置する。
優先度分類や包括的な`basic.test.ts`へ集約しない。

## 全file proof

1. commit、dirty diff、untracked内容を含む対象snapshotを固定する。
2. 現行repoから対象`*.zsh`を列挙し、除外規則を含むmanifestを保存する。
3. 全対象を現行のLexerとParserで処理する。
4. lexer/parser diagnostics、token coverage、unknown、EOF、range、raw、word parts、構造、comment、redirect、semanticを検証する。
5. validatorへ既知の壊れたfixtureを与え、各違反を検出できることを確認する。

## Consumer接続

- 接続を変更する前に現行consumerと公開surfaceを確認する。
- 依頼されていないconsumer接続をparser実装のついでに行わない。
- 接続を変更した場合はparser単体だけでなくconsumer経路も検証する。

## 完了表現

全対象と全verdictを監査できた場合も、形式手法を使っていなければ
「現行commitと現行corpusに対する全件実証」と表現する。
