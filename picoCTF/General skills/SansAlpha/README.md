## category
General skills
## probrem
The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols.
## 難しさ
普通
## 解法
文字は使えない。そこでグロブ展開を用いてみる。
```
SansAlpha$ *
\x1b[?2004h\x1b[?2004l
bash: blargh: command not found
\x1b[?2004h
SansAlpha$ */*
\x1b[?2004l
bash: blargh/flag.txt: Permission denied
\x1b[?2004h
```
今回は文字列が使えない。つまり記号のみで操作しなければいけない。
ここで変数をアンダースコアで使える。???で文字数一致により
文字列を取得できることから文字を集めてcatコマンドを作り出せばよい。
```
SansAlpha$ /???/????/???
\x1b[?2004l
bash: /etc/perl/Net: Is a directory
\x1b[?2004h
SansAlpha$ /???/?????/???
\x1b[?2004l
bash: /sys/class/bdi: Is a directory
\x1b[?2004h
```
それぞれc a t の文字が含まれているので変数化して取り出してみる。
```
SansAlpha$ __=(/???/????/???)
\x1b[?2004l
\x1b[?2004h
SansAlpha$ ___=(/???/?????/???)
\x1b[?2004l
\x1b[?2004h
SansAlpha$ ${__:3:1}
\x1b[?2004l
bash: c: command not found
\x1b[?2004h
SansAlpha$ ${___:7:1}
\x1b[?2004l
bash: a: command not found
\x1b[?2004h
SansAlpha$ ${__:2:1}
\x1b[?2004l
bash: t: command not found
\x1b[?2004h
```
したがってあとは実行するとフラグをゲット
```
SansAlpha$ ${__:3:1}${___:7:1}${__:2:1} */*
\x1b[?2004l
```
## 使用コマンド
### ??の検索
?????なら五文字にヒットするように検索をかけることができる。
文字数に一致するワイルドカードです。
### _の変数の利用
```${}```を変数を展開するコマンドなので
```
${変数:取り出す開始位置:取り出す文字数}
```
### bashにおける()の役割
配列代入を指しているらしい。つまり今回であれば文字列を配列に入れている。
### ワイルドカードとは
ファイル名を特殊な記号に置き換えて指定できるもの。
## 答え
```academy{7h15_mu171v3r53_15_m4dn355_2bf65e09}```
## ここから学んだこと
アンダーバーを活用することでbashは変数化することができる。
## つぎに考えること
bashについての深い理解や自分でコマンドなどを作れるようにしたい。

