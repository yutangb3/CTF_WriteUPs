## category
General skills
## probrem
Can you read the flag? I think you can!
## 難しさ
簡単
## 解法
まずはインスタンスを起動してsshで接続。
```
ssh -p 57007 ctf-player@green-hill.picoctf.net
```
パスワードを打って入れるので入ったらまずはlsでファイル一覧を確認。
```
ctf-player@challenge:~$ ls
flag.txt
```
なのでcatコマンドで中身を見ようとするが見れない。
どうやら権限がないらしい。実際に権限を確認するために
ファイルの権限を確認してみる。
```
ctf-player@challenge:~$ ls -l flag.txt
-r--r----- 1 root root 31 Mar  9  2026 flag.txt
```
rootが所有者でrootグループの両方に読み取りが許可されている。
なのでsudoコマンドでなんの権限が与えられているかを調べてみる。
```
sudo -l
Matching Defaults entries for ctf-player on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User ctf-player may run the following commands on challenge:
    (ALL) NOPASSWD: /bin/emacs
```
bin の後にあるのが権限を昇格した状態で使えるもの。
今回emacsが使える。またemacsではshellを起動できる。つまり
rootの状態でflag.txtの中身を見ることが可能となる。
emacsを起動してshellを開く。
```
ctf-player@challenge:~$ sudo emacs -nw
```
shellを入力してエンターでshellが起動。
あとは読みたいファイルのパスを入力してフラグをゲット。
## 使用コマンド
### ファイルに与えられている権限の確認
```
ls -l ファイル名
```
### 現在の位置の確認方法
```
pwd
```
### 自分がどこのグループに所属しているかなどの確認
```
groups
```
### sudoで何ができるかなどの確認
```
sudo -l
```
### emacsをターミナルで起動（not GUI)
```
emacs -nw
```
## 答え
```picoCTF{nEtCat_Mast3ry_0d33dA2C}```
## ここから学んだこと
linuxの権限の確認方法
sudoコマンドの意味や使い方
今回ファイルの権限や
sudoコマンドで権限を確認するところまでいけていたが
emacsの使い方や理解が足らず失敗。
大事なのはsudo -lで権限が上がっていてその時に使えるツールをフル活用すること。
## つぎに考えること
emacs以外の機能の使い方ををしっかり身に着けていくこと。
