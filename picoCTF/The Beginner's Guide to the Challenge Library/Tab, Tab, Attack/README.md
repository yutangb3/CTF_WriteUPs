## category
General skills
## probrem
Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames.
## 難しさ
簡単
## 解法
まずはzipファイルを解凍してファイルの中を確認する。<br>
その時に**Tabキー**を使うと簡単に次のファイル階層を見れる。<br>
```
./Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet<br>
fang-of-haynekhtnamet    fang-of-haynekhtnamet.c
```
全体を把握したのでファイルの種類を調べる<br>
```
file ./Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet<br>
./Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet: ELF 64-bit<br> LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, <br>BuildID[sha1]=4fdc1b4e898a0612ce5aa28e5012209f20bfc0ca, for GNU/Linux 3.2.0, not stripped<br>
```
これはlinuxの実行ファイルなので実行する<br>
```
./Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet
```
するとフラグが出現<br>
```
*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}
```
## 使用コマンド
ファイル階層を見ていくtabキー<br>
```
./ <tab><tab>.....
```
## 答え
```picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}```
## ここから学んだこと
tabキーの活用方法。<br>
こういう時間を少しでも短縮するということが大会で大事になってくると感じた。<br>
## つぎに考えること
ファイル名の部分検索するコマンドなどもあるので<br>
もっといろんな方法を身に着けていきたい。
