## category
General skills
## probrem
Unzip this archive and find the file named 'uber-secret.txt'

Download zip file
## 難しさ
簡単
## 解法
問題文にuber-secret.txtを見つけてとあるのでfindコマンドでファイル名を検索する。
```
find ./ -name uber-secret.txt
./adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
```
するとパスが表示されたので後は中身をみればflagをゲット。
## 使用コマンド
### ファイル名検索
```
find ./ -name ファイル名
```

## 答え
```picoCTF{f1nd_15_f457_ab443fd1}```
## ここから学んだこと
findコマンドの使い方
## つぎに考えること
ファイルの検索の絞り方のレパートリーを増やす。
サイズや所有者など
