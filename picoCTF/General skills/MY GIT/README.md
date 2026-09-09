## category
General skills
## probrem
I have built my own Git server with my own rules!
## 難しさ
簡単
## 解法
まずはインスタンスを立ち上げてlinuxで
問題文に表示されるgit cloneのsshコマンドを入力。
パスワードを求められるので入れるとローカルに
ファイルが保存される。
README.mdの中身を見てみる。
```
# MyGit

### If you want the flag, make sure to push the flag!

Only flag.txt pushed by ```root:root@picoctf``` will be updated with the flag.

GOOD LUCK!

```
これはユーザー名がroot
メールがroot@picoctf
によってflag.txtをプッシュされるとフラグが出現と書かれている。
なのでサーバーにユーザー名とメールを認識させる。
```
cd ./challenges
git config user.name "root"
git config user.mail "root@picoctf"
```
そして実際にflag.txtをpushしていく。
```
echo "give me" > flag.txt
git add flag.txt
git remote -m "add flag.txt"
git push origin master
```
パスワードが求められるので入力するとフラグが出現。
## 使用コマンド
### ユーザー名とメールの登録
```
git config user.name "ユーザー名"
git config user.mail "メアド"
```
### コマンド上でのテキストファイル作成
echoは文字列を出力するもの
```
echo "テキスト内容"　> ファイル名
```
### gitへのpushへの流れ
まずは変更したものを追加する。
```
git add 追加のもの
```
そして**変更履歴** を載せる。
```
git commit -m "メッセージ"
```
そしてpush
これでネット側に変更が送られる。
originは自動的にサーバーにつないだ時にoriginと認識して勝手に元のサーバー名を指しています。
masterはブランチです。
```
git push origin master
```

## 答え
```picoCTF{1mp3rs0n4t4_g17_345y_506743df}```
## ここから学んだこと
gitコマンドの使い方や表面上の理解<br>
gihubのログイン機能とは違い勝手にサーバーに認識させることができる。<br>
echo の使い方<br>
## つぎに考えること
gitのセキュリティ面
