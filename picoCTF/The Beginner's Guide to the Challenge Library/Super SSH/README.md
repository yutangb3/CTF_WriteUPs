## category
General skills
## probrem
Using a Secure Shell (SSH) is going to be pretty important.<br>
Can you ssh as ctf-player to titan.picoctf.net at port 52148 to get the flag?<br>
You'll also need the password f3b61b38. If asked, accept the fingerprint with yes.<br>
If your device doesn't have a shell, you can use: <br>
https://webshell.picoctf.org<br>
If you're not sure what a shell is, check out our Primer: <br>
https://primer.picoctf.com/#_the_shell<br>
Instance
## 難しさ
簡単
## 解法
ターミナルでsshを使用するのでまずは指示通りにポート番号で接続をする。<br>
```ssh -p 52148 ctf-player@titan.picoctf.net ```<br>
すると接続をするか聞かれるのでyesと入力してパスワードを入れる。<br>
するとフラグが出現。
## 使用コマンド
**sshを起動してポート番号とユーザー名を指定するコマンド**<br>
```ssh -p ポート番号 ユーザー名@接続先URL```
## 答え
picoCTF{s3cur3_c0nn3ct10n_3e293eea}
## ここから学んだこと
sshとはSecure shellのことを指している。<br>
これは遠隔で離れたサーバーと**安全に通信するためにプロトコルを利用して**ファイルの転送などをする。<br>
ここで大切なのは鍵を交換しあい、通信を暗号化している。  <br>
**sshの基本構文**<br>
```ssh [オプション] [ユーザー名]@[ホスト名] [コマンド]```
## つぎに考えること
他にもipアドレスで指定したりできるのでそれらを活用してsshに対する解像度を上げたい。
