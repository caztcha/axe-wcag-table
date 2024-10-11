# axe-core ルールと WCAG 2.2 達成基準の対照表

Deque Systems, Inc. が開発、公開しているウェブアクセシビリティ検証ツール「axe」のコアエンジン「axe-core」の Rule ID と、WCAG 2.2 の達成基準の、対照表です。Google スプレッドシートで公開しています。

- [axe-core ルールと WCAG 2.2 達成基準の対照表 (Google スプレッドシート)](https://docs.google.com/spreadsheets/d/1ihy8gqs-NP31mFk8_SFGPgFntGhtZDy-_SXh-G85vfs/edit?usp=sharing)

Deque Systems の axe-core リポジトリの「[Rule Descriptions](https://github.com/dequelabs/axe-core/blob/develop/doc/rule-descriptions.md)」をもとに作成しています。各 Rule ID は、axe-core のバージョン 4.10.0 で定義されているものです。

この対照表は、「[axe-test.js](https://github.com/caztcha/axe-test)」(axe-core を利用して、ウェブサイトのアクセシビリティ自動テストを一括的に実行するためのスクリプト) のテスト結果と併用することを想定しています。詳しくは下記の [「axe-test.js」との併用](#axe-testjsとの併用) をご参照ください。


## 対照表の各列の説明

<img width="1286" alt="axe-core ルールと WCAG 2.2 達成基準の対照表 (Google スプレッドシート)" src="https://github.com/user-attachments/assets/1cb40677-dfce-4bb2-b5d9-6686507ec4cd">

<dl>
<dt>SEQ</dt>
<dd>Rule ID がいくつあるかを把握するための、通し番号です。</dd>

<dt>axe-core Rule ID</dt>
<dd>「axe-core」の Rule ID です。</dd>

<dt>Description</dt>
<dd>Rule ID が意味するルールの説明を記載しています。Deque Systems の axe-core リポジトリの「[Rule Descriptions](https://github.com/dequelabs/axe-core/blob/develop/doc/rule-descriptions.md)」から引用しています。</dd>

<dt>WCAG 2.2 達成基準</dt>
<dd>Rule ID に対応する、WCAG 2.2 の達成基準を記載しています。</dd>

<dt>レベル</dt>
<dd>Rule ID に対応する、WCAG 2.2 の達成基準の、レベル (A、AA、AAA) を記載しています。</dd>

<dt>Experimental</dt>
<dd>Deque Systems の axe-core リポジトリの「[Rule Descriptions](https://github.com/dequelabs/axe-core/blob/develop/doc/rule-descriptions.md)」において、Experimental Rules として挙げられているルールに対して、フラグ (○印) を付しています。</dd>
</dl>

## 「axe-test.js」との併用

この対照表を、「[axe-test.js](https://github.com/caztcha/axe-test)」によるテスト結果にマージすることによって、テスト結果のスプレッドシートの各行に記載された個々の問題 (axe-core ルール) が、WCAG 2.2 のどの達成基準に関連するかを、見やすくすることができます。以下、その手順です。

1. 「axe-test.js」によるテスト結果のスプレッドシート (Google スプレッドシートや Excel) と同じブックの別シート (たとえば「collation」というシート名を新規で作成します) に、この対照表をコピー&ペーストします。
    - 新規作成したシートに対照表をコピー＆ペーストする際は、いちばん左上のセル (A1) を起点にペーストします (そうすることで、下記の説明に出てくる VLOOKUP 関数をそのままお使いいただけます)。
2. テスト結果シート各行の空白セルに、VLOOKUP 関数を入力します (例 : 「`=VLOOKUP(B2,collation!$B$2:$E$101,3,FALSE)`」)。<img width="1368" alt="axe-test.js のテスト結果の空白セルに「VLOOKUP(B2,collation!$B$2:$E$101,3,FALSE)」と入力" src="https://github.com/user-attachments/assets/953a6b6d-ebcf-4f7b-8820-02826a330cad">
    - 上記の VLOOKUP 関数の例は、テスト結果シートの2行目の空白セルに入力することを想定しています。
    - 「テスト結果シートの `B2` セル (当該行で axe-core Rule ID が記載されている) を、collation シートのセル範囲 `$B$2:$E$101` と照合し、axe-core Rule ID が完全一致する行があれば、collation シートの`3`列目 (WCAG 達成基準が記載されている) の内容を取得する」という意味です。
    - `FALSE` のひとつ前にある `3` を、`4` に変更すると、collation シートの`4`列目 (WCAG 達成基準のレベル) を取得することができます。<img width="1368" alt="xe-test.js のテスト結果の空白セルに「VLOOKUP(B2,collation!$B$2:$E$98,4,FALSE)」と入力" src="https://github.com/user-attachments/assets/b85706c0-7658-4888-8ed4-70c11a50f766">
3. VLOOKUP 関数を、すべての行にわたってコピー＆ペーストします (上記の例の `B2` の部分は、ペーストされる行に応じて、`B3`、`B4`、`B5` ... となるはずです)。<img width="1357" alt="VLOOKUP 関数をすべての行にわたってコピー＆ペースト" src="https://github.com/user-attachments/assets/42147db0-bce0-4e82-80c4-6ae82771aaa2">

---

以上
