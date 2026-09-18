## category
General skills
## probrem
Do you know how to move between directories and read files in the shell? Start the container, ssh to it, and then ls once connected to begin.

Login via ssh as ctf-player with the password, 8c606eb1 on the host wily-courier.picoctf.net and port 53518.
## 難しさ
簡単
## 解法
まずはsshでつないでみる。
```
 ssh -p 53518 ctf-player@wily-courier.picoctf.net
```
その後にパスワードを入力。
そしてlsコマンドを実行。ファイルをすべて読む。
```
ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
ctf-player@pico-chall$ cat 1of3.flag.txt
picoCTF{xxsh_
ctf-player@pico-chall$ cat instructions-to-2of3.txt
Next, go to the root of all things, more succinctly `/`
```
指示通りにコマンドをうってみる。
```
ctf-player@pico-chall$ cd /
ctf-player@pico-chall$ ls
2of3.flag.txt  boot       dev  home                      lib    media  opt   root  sbin  sys  usr
bin            challenge  etc  instructions-to-3of3.txt  lib64  mnt    proc  run   srv   tmp  var
ctf-player@pico-chall$ cat 2of3.flag.txt
0ut_0f_//4t3r_
```
またそこでファイルを開く。
```
ctf-player@pico-chall$ cat instructions-to-3of3.txt
Lastly, ctf-player, go home... more succinctly `~`
ctf-player@pico-chall$ cd ~
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat 3of3.flag.txt
0b24fc4f}ctf-player@pico-chall$
```
指示にしたがったら三つのフラグの破片が出てきたのでフラグをゲット。
## 使用コマンド
### sshのポート指定
```
ssh -p ポート番号　ユーザー名@接続先URL
```

## 答え
```picoCTF{xxsh_0ut_0f_//4t3r_0b24fc4f}```
## ここから学んだこと
cd / で最上位ディレクトリに移動。
cd ~ でホームディレクトリに移動。
## つぎに考えること
linuxの知らないコマンドなどもしっかり調べる。

