## category
General skills
## probrem
Can you find the flag in file without running it?
## 難しさ
簡単
## 解法
実行せずにファイルからフラグを見つける。<br>
そのためにstringコマンドを用いてバイナリを文字化。<br>
でもすべて文字化してみていくのは大変なので<br>
ファイルをstrings化した後にgrepコマンドで検索をかける。<br>
```
strings strings|grep -ba pico
```
するとフラグが出現。
```
74143:picoCTF{5tRIng5_1T_dB2CEA76}
```
## 使用コマンド
ファイルを文字化。
```
strings ファイル名
```
grepコマンドの基本形
```
grep オプション　検索ワード　ファイル名
```
ファイルとgrep検索を繋げるパイプライン
```
strings ファイル名|grep 検索ワード
```
検索結果が先頭から何バイト目かを調べるgrepオプション
```
grep -o
```
テキスト表示かするgrepオプション
```
grep -a
```
## 答え
```
picoCTF{5tRIng5_1T_dB2CEA76}
```
## ここから学んだこと
grepコマンドの使い方。
## つぎに考えること
grepコマンド以外にもsedなど置換できたり<br>
状況に応じて使い分けて生きたい。

