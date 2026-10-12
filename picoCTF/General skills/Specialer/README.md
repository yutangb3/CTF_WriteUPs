## category
General skills
## probrem
Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer. ssh -p 24959 ctf-player@xebec.cylabacademy.net. The password is 6313d317
## 難しさ
普通
## 解法
今回もsshにつないでいくと組み込みコマンドしか使えません。
なのでまずはファイルを検索していきます。
```
Specialer$ echo *
abra ala sim
```
ファイルの下に何があるかも見ていきます。
```
Specialer$ echo */*
abra/cadabra.txt abra/cadaniel.txt ala/kazam.txt ala/mode.txt sim/city.txt sim/salabim.txt
```
これらを読むためにcatコマンドを実行したいところですが、
ファイルがないので自分で再構築していきます。
```
Specialer$  alias cat='while IFS= read -r line || [[ -n $line ]]; do echo "$line" ; done <'
```
後はひたすら読んでいけばフラグをゲット。
```
Specialer$ cat ala/mode.txt
Yummy! Ice cream!
Specialer$ cat sim/salabim.txt
#He was so kind, such a gentleman tied to the oceanside#
Specialer$ cat ala/kazam.txt
return 0 academy{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_08b4adf4}
```
## 使用コマンド
### lsの代用
```
echo *
```
本来は　
```
echo *.txt
```
のように文字列にヒットしたファイル名を吐き出すbashのワイルドカードです。
今回何も指定していないためファイル名が出現し、それをechoに引き渡しa結果として
ファイル名が表示される理由です。
### ディレクトリの下まで確認する方法
```
echo */*
```
## 答え
```academy{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_08b4adf4}```
## ここから学んだこと
### aliasコマンド
コマンドに別名をつけて実行できるようになります。
この本質は別名を呼び出したときに
コマンド内容をbash内で文字列として展開して実行されるためです。
```
alias 別名='コマンド内容'
```
### IFS
``` IFS= ```とつけることで区切り文字などの
余白を確保できます。
### whileの基本形
while 条件 ; do 処理 ;　done
;の位置は次のように改行の代わりに書いているようなものです
```
while [[ $x -le 3 ]]
do
    echo "$x"
done
```
### read lineの使い方
```read line```でキーボードやファイルから読み取った
**一行**をlineに保存します。またreadの性質として
一度読んだ後にまた呼ばれると一度読んだ行の次の行を読み始めます。
```-r```オプションではバックスラッシュもそのまま文字として読みます。
### -n
```[[-n ]]```
で文字列の中の文字数が0でないかを調べます。
今回、条件判定式をつけることで
最後に改行文字がない場合でも
読み取れるようにしています。
## つぎに考えること
組み込みコマンドでできることをもっと増やしていったりターミナルについて深くしる。
