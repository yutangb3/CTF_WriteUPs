## category
General skills
## probrem
Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...
## 難しさ
簡単
## 解法
まずファイル名が与えられているのでlinuxを立ち上げて調べていく。<br>
```wsl```<br>
そしてファイルの種類を検索<br>
```file warm```<br>
すると以下のようにでる<br>
```warm: ELF 64-bit LSB pie executable, x86-64,```<br>
これはlinuxの実行ファイルと判明。ひとますstringsコマンドでflagがないかを探す<br>
```strings warm```<br>
すると以下のように出てきた。<br>
```text
Hello user! Pass me a -h to learn what I can do!
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_ac5832c}<br>
I don't know what '%s' means! I do know what -h means though!
```
なので実際に-hオプションをつけて実行する。<br>
```./warm -h```<br>
するとフラグが出現<br>
```Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_ac5832c}```<br>
## 使用コマンド
linuxファイルの中身を文字列化<br>
```strings ファイル名```<br>
linuxファイルを実行するコマンド<br>
```./ファイル名```<br>
linuxファイルをヘルプオプションで実行<br>
```./ファイル名　-h```<br>
## 答え
```picoCTF{b1scu1ts_4nd_gr4vy_ac5832c}```<br>
## ここから学んだこと
この```-h```はそのファイルの使い方<br>
などを実際に表してくれる。ちなみにファイル作成者が任意でつけている。<br>
## つぎに考えること
```-h```以外のコマンドなどももっと深堀りしていきたい。<br>

