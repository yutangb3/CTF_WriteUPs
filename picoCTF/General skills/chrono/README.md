## category
General skills
## probrem
How to automate tasks to run at intervals on linux servers? Use ssh to connect to this server:
## 難しさ
普通
## 解法
sshで接続してルートディレクトリに移動してchallengeファイルを開いてみる。  
```
picoplayer@challenge:/$ cd challenge/
-bash: cd: challenge/: Permission denied
```
sudoで権限を更新した状態で使えないかを調べてみる。
```
picoplayer@challenge:/$ sudo -l
[sudo] password for picoplayer:
Sorry, user picoplayer may not run sudo on challenge.
```
今回は使えないみたいです。
```
picoplayer@challenge:/etc$ cat etc/crontab
cat: etc/crontab: No such file or directory
```
次に全体のcronジョブを見ていきます。
```
picoplayer@challenge:/etc$ cat /etc/crontab
# academy{Sch3DUL7NG_T45K3_L1NUX_5ea693bf}
```
フラグゲット。
## 使用コマンド
### 自分のcronジョブを検索
```
crontab -l
```
## 答え
```
academy{Sch3DUL7NG_T45K3_L1NUX_5ea693bf}
```
## ここから学んだこと
### cronとは
時間単位で自動処理を行うコマンドです。
## つぎに考えること
次はファイルを変更してroot権限で実行を試してみます。
