# axe-core ルールと WCAG 2.1 達成基準の対照表

Deque Systems, Inc. が開発、公開しているウェブアクセシビリティ検証ツール「axe」のコアエンジン「axe-core」の Rule ID と、WCAG 2.1 の達成基準の、対照表です。Google スプレッドシートで公開しています。

- [axe-core ルールと WCAG 2.1 達成基準の対照表 (Google スプレッドシート)](https://docs.google.com/spreadsheets/d/1ihy8gqs-NP31mFk8_SFGPgFntGhtZDy-_SXh-G85vfs/edit?usp=sharing)

Deque Systems, Inc. の以下のドキュメントをもとに、作成しています。

- [github.com/dequelabs/axe-core リポジトリの「Rule Descriptions」](https://github.com/dequelabs/axe-core/blob/develop/doc/rule-descriptions.md) 
- [Duque University の「List of axe 4.4 Rules」](https://dequeuniversity.com/rules/axe/4.4) 

## 対照表の各列の説明

<img width="1277" alt="axe-core ルールと WCAG 2.1 達成基準の対照表 (Google スプレッドシート)" src="https://user-images.githubusercontent.com/17394690/175891945-b4765baa-e605-41f9-b4d5-846ec6805639.png">

<dl>
<dt>SEQ</dt>
<dd>Rule ID がいくつあるかを把握するための、通し番号です。</dd>

<dt>axe-core Rule ID</dt>
<dd>「axe-core」の Rule ID です。</dd>

<dt>概要</dt>
<dd>Rule ID が意味するルールの、概要を記載しています。<a href="https://dequeuniversity.com/rules/axe/4.4">Duque University の「List of axe 4.4 Rules」</a>の日本語訳から引用しています　(一部、日本語訳が存在しないルールについては、私が翻訳しています)。</dd>

<dt>WCAG 2.1 達成基準</dt>
<dd>Rule ID に対応する、WCAG 2.1 の達成基準を記載しています。</dd>

<dt>レベル</dt>
<dd>Rule ID に対応する、WCAG 2.1 の達成基準の、レベル (A、AA、AAA) を記載しています。</dd>

<dt>Experimental</dt>
<dd><a href="https://github.com/dequelabs/axe-core/blob/develop/doc/rule-descriptions.md">github.com/dequelabs/axe-core リポジトリの「Rule Descriptions」</a>において、Experimental Rules として挙げられえているルールに対して、フラグ (○印) を付しています。</dd>
</dl>

## 「axe-test.js」との併用

この対照表を、「[axe-test.js](https://github.com/caztcha/axe-test)」によるテスト結果にマージすることによって、テスト結果のスプレッドシートの各行に記載された個々の問題 (axe-core ルール) が、WCAG 2.1 のどの達成基準に関連するかを、見やすくすることができます。以下、その手順です。

1. 「axe-test.js」によるテスト結果のスプレッドシート (Google スプレッドシートや Excel) と同じブックの別シート (たとえば「collation」というシート名を新規で作成します) に、この対照表をコピー&ペーストします。
    - 新規作成したシートに対照表をコピー＆ペーストする際は、いちばん左上のセル (A1) を起点にペーストします (そうすることで、下記の説明に出てくる VLOOKUP 関数をそのままお使いいただけます)。
2. テスト結果シート各行の空白セルに、VLOOKUP 関数を入力します (例 : 「`=VLOOKUP(B2,collation!$B$2:$E$98,3,FALSE)`」)。<img width="1368" alt="axe-test.js のテスト結果の空白セルに「VLOOKUP(B2,collation!$B$2:$E$98,3,FALSE)」と入力" src="https://user-images.githubusercontent.com/17394690/175894361-ee731938-88d4-4818-b551-e8756396fffa.png">
    - 上記の VLOOKUP 関数の例は、テスト結果シートの2行目の空白セルに入力することを想定しています。
    - 「テスト結果シートの `B2` セル (当該行で axe-core Rule ID が記載されている) を、collation シートのセル範囲 `$B$2:$E$98` と照合し、axe-core Rule ID が完全一致する行があれば、collation シートの`3`列目 (WCAG 達成基準が記載されている) の内容を取得する」という意味です。
    - `FALSE` のひとつ前にある `3` を、`4` に変更すると、collation シートの`4`列目 (WCAG 達成基準のレベル) を取得することができます。<img width="1368" alt="xe-test.js のテスト結果の空白セルに「VLOOKUP(B2,collation!$B$2:$E$98,4,FALSE)」と入力" src="https://user-images.githubusercontent.com/17394690/175894388-2dc9be7c-fabe-461b-8764-39c23f6c2c27.png">
3. VLOOKUP 関数を、すべての行にわたってコピー＆ペーストします　(上記の例の`B2` の部分は、ペーストされる行に応じて、`B3`、`B4`、`B5` ... となるはずです)。<img width="1357" alt="VLOOKUP 関数をすべての行にわたってコピー＆ペースト" src="https://user-images.githubusercontent.com/17394690/175894420-10225bbe-d3d4-4283-a991-68470d81b937.png">
