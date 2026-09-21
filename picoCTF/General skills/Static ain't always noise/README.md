## category
General skills
## probrem
Can you look at the data in this binary? The bash script might help!
## 難しさ
簡単
## 解法
まずはそれぞれのファイルを確認する。
```
file static
static: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=9a00d4dca6b92d22aa0cd1fceffa4ed7495b8534, for GNU/Linux 3.2.0, not stripped
```
```
file ltdis.sh
ltdis.sh: Bourne-Again shell script, ASCII text executable

```
catコマンドでltdis.shの中のバイナリを読む。
```
cat ltdis.sh
#!/bin/bash



echo "Attempting disassembly of $1 ..."


#This usage of "objdump" disassembles all (-D) of the first file given by
#invoker, but only prints out the ".text" section (-j .text) (only section
#that matters in almost any compiled program...

objdump -Dj .text $1 > $1.ltdis.x86_64.txt


#Check that $1.ltdis.x86_64.txt is non-empty
#Continue if it is, otherwise print error and eject

if [ -s "$1.ltdis.x86_64.txt" ]
then
        echo "Disassembly successful! Available at: $1.ltdis.x86_64.txt"

        echo "Ripping strings from binary with file offsets..."
        strings -a -t x $1 > $1.ltdis.strings.txt
        echo "Any strings found in $1 have been written to $1.ltdis.strings.txt with file offset"



else
        echo "Disassembly failed!"
        echo "Usage: ltdis.sh <program-file>"
        echo "Bye!"
fi
```
いまあるファイルはstaticしかないのでこれを第一引数として渡す。
すると$1.ltdis.strings.txtがでてきて見てみるとフラグが出現。
## 使用コマンド
### objdump 
**-j**オプションがセクション指定。<br>
**-D**オプションが逆アセンブル。<br>
```
objdump -Dj セクション　ファイル
```
### strings
**-a**オプションがすべてのファイルを調べる。<br>
**-t  x**が文字列の位置を16進数で表記。<br>
```
strings -a -t x ファイル
```
## 答え
```picoCTF{d15a5m_t34s3r_20335e41}```
## ここから学んだこと
objdumpの使い方と$1が引数を表すということ。
## つぎに考えること
objdumpの使いどころ。


