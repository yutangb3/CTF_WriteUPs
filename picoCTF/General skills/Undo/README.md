## category
General skills
## probrem
Can you reverse a series of Linux text transformations to recover the original flag?
## 難しさ
簡単
## 解法
まずはnetcatでつないでみる。
```
nc foggy-cliff.picoctf.net 50151
```
すると以下の文が出現。
```
===Welcome to the Text Transformations Challenge!===

Your goal: step by step, recover the original flag.
At each step, you'll see the transformed flag and a hint.
Enter the correct Linux command to reverse the last transformation.

--- Step 1 ---
Current flag: KTgxMzkzOW4zLWZhMDFnQHplMHNmYTRlRy1nazNnLXRhMWZlcmlyRShTR1BicHZj
Hint: Base64 encoded the string.
Enter the Linux command to reverse it:
```
base64というバイナリをテキストデータに変換するものです。
それをデコードすればよいので
```
Enter the Linux command to reverse it: base64 -d
```
すると
```
Correct!

--- Step 2 ---
Current flag: )813939n3-fa01g@ze0sfa4eG-gk3g-ta1ferirE(SGPbpvc
Hint: Reversed the text.
Enter the Linux command to reverse it:
```
逆に並び替えたらいいので
```
Enter the Linux command to reverse it: rev
```
すると
```
Correct!

--- Step 3 ---
Current flag: cvpbPGS(Eriref1at-g3kg-Ge4afs0ez@g10af-3n939318)
Hint: Replaced underscores with dashes.
Enter the Linux command to reverse it:
```
**_** を　**-**　に置換したと書いてあるので置換コマンドを用いて逆の操作を行います。
```
Enter the Linux command to reverse it: tr '-' '_'
```
すると
```
Correct!

--- Step 4 ---
Current flag: cvpbPGS(Eriref1at_g3kg_Ge4afs0ez@g10af_3n939318)
Hint: Replaced curly braces with parentheses.
Enter the Linux command to reverse it:
```
｛｝から（）に置換されているので先ほど同様に戻していきます。
```
Enter the Linux command to reverse it: tr '()' '{}'
```
すると
```
Correct!

--- Step 5 ---
Current flag: cvpbPGS{Eriref1at_g3kg_Ge4afs0ez@g10af_3n939318}
Hint: Applied ROT13 to letters.
Enter the Linux command to reverse it:
```
**ROT13**とは英語の文字を13文字ずつずらしたシーザー暗号なので
もう一度13文字ずらすともとに戻せます。
```
Enter the Linux command to reverse it: tr 'a-zA-Z' 'n-za-mN-ZA-M'
```
するとフラグが出現。
## 使用コマンド
### base64で暗号化されたものを復号　-d(オプション)
```
base64 -d
```
### 文字を逆さまにするコマンド
```
rev
```
### 文字を置換する。
一気に指定できる。
例）tr 'abcd' 'efgh' 順番で対応している。
```
tr '置換する前の文字' '置換した後の文字'
```
## 答え
```picoCTF{Revers1ng_t3xt_Tr4nsf0rm@t10ns_3a939318}```
## ここから学んだこと
linuxコマンドの基礎。
## つぎに考えること
sedコマンドとtrコマンドの違い。
trではrot13などの一文字変換が向いている。
それに対して  sedコマンドは単語などの文字列の置換に向いている。
