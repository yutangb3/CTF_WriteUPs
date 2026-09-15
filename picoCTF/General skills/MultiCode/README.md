## category
General skills
## probrem
We intercepted a suspiciously encoded message, but it’s clearly hiding a flag. No encryption, just multiple layers of obfuscation. Can you peel back the layers and reveal the truth?
## 難しさ
簡単
## 解法
まずはファイルの中身を確認する。
```
file message.txt
message.txt: ASCII text
```
なので中身をcatコマンドで出力してみる。
```
cat message.txt
NjM3NjcwNjI1MDQ3NTMyNTM3NDI2MTcyNjY2NzcyNzE1ZjcyNjE3MDMwNzE3NjYxNzQ1ZjM4NzE3MTMwMzM3MjczNzIyNTM3NDQ=
```
末尾に＝があるのでbase64のエンコードの可能性が高い
```
 echo NjM3NjcwNjI1MDQ3NTMyNTM3NDI2MTcyNjY2NzcyNzE1ZjcyNjE3MDMwNzE3NjYxNzQ1ZjM4NzE3MTMwMzM3MjczNzIyNTM3NDQ= | base64 -d
637670625047532537426172666772715f72617030717661745f3871713033727372253744
```
16進数が並んでいるので文字変換してみる。
```
 echo 637670625047532537426172666772715f72617030717661745f3871713033727372253744 | xxd -r -p
cvpbPGS%7Barfgrq_rap0qvat_8qq03rsr%7D
```
%がでてきたのでurlエンコードと予測。
```
echo cvpbPGS%7Barfgrq_rap0qvat_8qq03rsr%7D | nkf -Ww --url-input
cvpbPGS{arfgrq_rap0qvat_8qq03rsr}
```
規則性からもしかしたらROT13かもしれない。
```
echo 'cvpbPGS{arfgrq_rap0qvat_8qq03rsr}'| tr 'a-zA-Z' 'n-za-mN-ZA-M'
picoCTF{nested_enc0ding_8dd03efe}
```
フラグが出現。
## 使用コマンド
### base64のデコード
```
base64 -d
```
### URL
nkfはnet work kanji filterの略。<br>
-W UTF-8の入力を指定<br>
-w UTF-8の出力を指定<br>
-url-input URLデコードをサポート<br>
```
nkf -Ww --url-input
```
### hex(16進数)
-r 逆変換<br>
-p プレーン。アドレスや空白なく連続しているときに使用。<br>
```
xxd -r -p
```
### ROT13
```
tr 'a-zA-Z' 'n-za-mN-ZA-M'
```
## 答え
```picoCTF{nested_enc0ding_8dd03efe}```
## ここから学んだこと
それぞれのエンコードの特徴
### 16進数
数字(0^9)と英語(a-f)のみ
### URLデコード
%が一番の特徴。
### base64デコード
末尾の**=**
base64の仕組みとして6bit(2**6で64種類の文字)を区切って足りないところを=で補うから。
### ROT13
同じ文字が繰り返し使われている。
例）pi**c**o**C**TF => cv**p**b**P**GS
## つぎに考えること
cyberctfでの効率化。
ペンテスターを目指しているのでlinuxのみで頑張る。
