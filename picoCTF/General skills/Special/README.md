## category
General skills
## probrem
Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)

Start your instance to see connection details.
## 難しさ
普通
## 解法
何を打っても意図通りにはならない。
そこで外部コマンドをパスで指定して実行してみる。
```
Special$ /bin/ls
Absolutely not paths like that, please!
```
うまく行きませんでした。
パラメータを利用して調べていきます。
今回文字を打つとすべて変換されてしまいます。そこで
記号であれば変換されません。そこでパラメーター展開で文字列を{}の中に
しのびこませて実行してみます。
```
Special$ ${x=ls}
${x=ls}
blargh
```
つぎは```blargh```について調べてみます。
```
Special$ ${x=ls blargh}
${x=ls blargh}
flag.txt
```
答えがありそうなのでcatコマンドで正解を出します。
```
Special$ ${x=cat blargh/flag.txt}
${x=cat blargh/flag.txt}
academy{5p311ch3ck_15_7h3_w0r57_399408e7}Special$
```
するとフラグが出現。
## 使用コマンド
### 変数を代入。
```
${変数名＝値｝
```
## 答え
```picoCTF{nEtCat_Mast3ry_0d33dA2C}```
## ここから学んだこと
### シェルとは
入力された文字列を適切なコマンドに解釈するプログラム。概念名。
### bashとは
入力された文字列を適切なコマンドに解釈するシェルの一種。具体例。
### bash組み込みコマンドとは
bash内で完結するコマンドです。
### コマンドに別の名前をつけて実行。
```
alias ll=[コマンド]
```
実行範囲はbash内です。
### 外部コマンドとは
bashの外部に実行ファイルとしてありそれらを呼び出して実行するのものです。
## つぎに考えること
なぜ今回いけたのか。またターミナルへの深い理解。
