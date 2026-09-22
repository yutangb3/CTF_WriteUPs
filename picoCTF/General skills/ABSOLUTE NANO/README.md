## category
General skills
## probrem
You have complete power with nano.

Think you can get the flag?
## 難しさ
普通
## 解法
まずはsshに接続する。
そしてファイルを確認。
```
ctf-player@challenge:~$ ls
flag.txt
```
読んでみる。
```
ctf-player@challenge:~$ file flag.txt
flag.txt: regular file, no read permission
```
権限がないみたいなのでまずは権限周りを調べる。
```
ctf-player@challenge:~$ ls -l flag.txt
-r--r----- 1 root root 35 Feb  4  2026 flag.txt
```
次にsudoで権限を昇格してできることがないかを探していく。
```
ctf-player@challenge:~$ sudo -l
Matching Defaults entries for ctf-player on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User ctf-player may run the following commands on challenge:
    (ALL) NOPASSWD: /bin/nano /etc/sudoers
```
**/bin/nano /etc/sudoers**だけが許可されているので実行してみる。
```
ctf-player@challenge:~$ sudo /bin/nano /etc/sudoers
```
すると以下の文が出現。
```
# User privilege specification
root    ALL=(ALL:ALL) ALL
```
ここにctf-playerを追加して権限を昇格。そしてフラグのファイルが見れるようになるのでゲット。
## 使用コマンド
## 答え
```picoCTF{n4n0_411_7h3_w4y_aae4aa32}```
## ここから学んだこと
sudo権限で奪うという大体の解法。
## つぎに考えること
sudoersについての深い理解

