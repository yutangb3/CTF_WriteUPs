## category
General skills
## probrem
Our server seems to be leaking pieces of a secret flag in its logs. The parts are scattered and sometimes repeated. Can you reconstruct the original flag?

Download the logs
 and figure out the full flag from the fragments.
## 難しさ
簡単
## 解法
ファイルの中身を確認する。
```
file server.log
server.log: ASCII text
```
stringsで一回見てみると先頭の行にこれが出てきた。
```
strings server.log
[1990-08-09 10:00:10] INFO FLAGPART: picoCTF{us3_
```
つまりflagpartでgrep検索をかければフラグが得られそう。
```
 strings server.log | grep -i 'flagpart'
[1990-08-09 10:00:10] INFO FLAGPART: picoCTF{us3_
[1990-08-09 10:02:55] INFO FLAGPART: y0urlinux_
[1990-08-09 10:05:54] INFO FLAGPART: sk1lls_
[1990-08-09 10:05:55] INFO FLAGPART: sk1lls_
[1990-08-09 10:10:54] INFO FLAGPART: cedfa5fb}
[1990-08-09 10:10:58] INFO FLAGPART: cedfa5fb}
[1990-08-09 10:11:06] INFO FLAGPART: cedfa5fb}
```
フラグをゲット
## 使用コマンド
### 文字列検索
-iオプションは大文字小文字を無視。
## 答え
``` picoCTF{us3_y0urlinux_sk1lls_cedfa5fb}```
## ここから学んだこと
grepコマンドの使い方
## つぎに考えること
フラグが何回かリピートしていたので繰り返しを表示しないなどの
時間短縮をめざす。
