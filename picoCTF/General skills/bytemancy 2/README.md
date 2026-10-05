## category
General skills
## probrem
Can you conjure the right bytes? The program's source code can be downloaded here
. Connect to the program with netcat:

$ nc xebec.cylabacademy.net 32593
## 難しさ
簡単
## 解法
まずはファイルを読み込んでみる。
```
if user_input == b"\xff\xff\xff":
```
これを送ればflagをゲット。ncでつなぎターミナルで送るがしかし何回やっても上手く行かず。
調べてみるとキーボードから打つものはどうしてもアスキー文字としての```f```になる。
いまサーバーが求めているのは16進数の```f```です。なのでヒントにある通りpwtoolsを使って送ってみる。
```
from pwn import *

p = remote("chatelaine.cylabacademy.net", 24942)

p.sendline(b"\xff\xff\xff")

p.interactive()
```
これでpythonファイルを実行するとフラグをゲット。
## 使用コマンド
## 答え
```academy{3ff5_4_d4yz_ea415b31}```
## ここから学んだこと
pwntoolsの存在、キーボードからターミナルへの裏側の動作
## つぎに考えること
シリーズ化しているのでもっといろいろなツールを使いこなせるようになる。
