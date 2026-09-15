## category
General skills
## probrem
I accidentally wrote the flag down. Good thing I deleted it!

You download the challenge files here:

challenge.zip
## 難しさ
簡単
## 解法
まずはgitの履歴を確認する。
```
git log
```
```
a6dca68 HEAD@{8}: commit: remove sensitive info
e720dc2 (HEAD -> master) HEAD@{9}: commit (initial): create flag
```
flagが作られた痕跡があるのでそこに移動。
```
git reset --hard HEAD@{9}
HEAD is now at e720dc2 create flag
```
あとはファイルを出力したらフラグをゲット。
## 使用コマンド
### gitのログへの移動方法
```
git reset --hard 番号
```
**soft**はコミットのみ削除。
**hard**はコミットも変更も削除。
### headの移動履歴
```
git reflog
```
## 答え
```picoCTF{nEtCat_Mast3ry_0d33dA2C}```
## ここから学んだこと
gitで情報が簡単に手に入る。
## つぎに考えること
gitの履歴がセキュリティ的にとてもおいしい情報。
