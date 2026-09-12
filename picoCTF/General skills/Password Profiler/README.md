## category
General skills
## probrem
We intercepted a suspicious file from a system, but instead of the password itself, it only contains its SHA-1 hash. Using OSINT techniques, you are provided with personal details about the target. Your task is to leverage this information to generate a custom password list and recover the original password by matching its hash.

Download the following files:

userinfo
: Contains the personal details.

hash
: Contains the SHA-1 hash of the password.

check_password
: Script to test passwords against the hash.
## 難しさ
簡単
## 解法
pythonファイルと個人情報とハッシュ値がある。
ハッシュ値から逆探知も考えたが個人情報が引っかかる。
そしてpythonファイルを読むとパスワードリストをcuppで作る必要があるらしい。
なのでcuppを使う。
```
PS C:\Users\yutan\Downloads\Password Profiler\cupp> python3 cupp.py -i
```
会話モードで個人情報が効かれるので答えていくと
パスワードリストを作成してくれる。
あとはそのリストをpythonコードに読み込ませるとflagが出現。
## 使用コマンド
cuppを **会話モード(-i)** で起動
```
python3 cupp.py -i
```
## 答え
```picoCTF{Aj_15901990}```
## ここから学んだこと
CUPPという個人情報をもとにしたツールの使い方
今回の手法は総当たりより精密で精度が高め。
## つぎに考えること
個人情報ありきのツールの使用なので
個人情報をこんどはどうやって手にいれられてしまうようなところが
あるのかについて考える。

