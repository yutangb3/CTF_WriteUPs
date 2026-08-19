## category
General skills
## probrem
Can you find the flag in the file? This would be really tedious to look through manually, something tells me there is a better way.
## 難しさ
簡単
## 解法
まずはファイルの種類を調べる
```
file file
```
すると以下のようにでる。
```
file: ASCII text, with very long lines (14545)
```
文字のバイナリが並んでいるのは分かったがstringsで文字化しても
フラグを見つけるのは難しそう。
なのでgrepの単語検索機能を使う。
```
strings file|grep -i picoctf
```
それでもなお長い一文が表示されるが探していく。
するとフラグが出現。
## 使用コマンド
**ファイルの種類を検索**
```
file ファイル名
```
**grep使用コマンド（-iは大文字小文字を無視。）**
```
strings ファイル名 | grep オプション 検索ワード
```
## 答え
```
picoCTF{grep_is_good_to_find_things_e3C4b360}
```
## ここから学んだこと
grepという検索機能があるということ。
パイプラインの仕組み
-iのオプションの意味
## つぎに考えること
もっと効率的な方法を考える。
ほかにも幾つかやり方があった。
知っておいて損はないので一旦まとめる。
### lessの利用
```
strings ファイル名|grep オプション　検索ワード|less
```
これは長い分を1ページずつ見るためのコマンドです。<br>
<br>
```↑```
上にスクロール<br>
```↓```
下にスクロール<br>
```/検索ワード```
検索したところに飛べる。<br>
また検索候補が複数ある場合は次のコマンドが使える。<br>
```N```
前の検索候補へ<br>
```n```
次の検索候補へ<br>
```q```
quitのqで終了。<br>

### 正規表現の利用
まず正規表現とは文字のルールなどです。
検索ワードなどのところに入れます。<br>
```.```
任意の一文字<br>
```*```
ゼロ回以上の繰り返し<br>
```+```
一回のみ<br>
```[abc]```
aまたはbまたはcのどれか<br>
```^```
否定<br>

これらを利用する。<br>
基本的にflagはpicoCTF{文字｝なので<br>
picoCTF{<br>
”}”じゃない文字の指定<br>
｝<br>
のように考えれる。<br>
```
picoCTF{ [^}]* }
```
実際に検索してみる。
```
strings file|grep -io 'picoctf{[^}]*}'
```
フラグが出現。

### 検索候補の前後の文字数を指定
```
文字\{回数\}
```
\{と\}で回数を挟むのがポイント。
aという文字が0文字以上50文字以下なら
```
a\{0,50\}
```
aの部分を.にするとどんな文字でも0から50文字とるという風に設定できる。
今回の場合であれば
```
strings file|grep -io '.\{0,50\}picoctf.\{0,50\}'
```
