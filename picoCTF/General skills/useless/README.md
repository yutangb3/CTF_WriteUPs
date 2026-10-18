## category
General skills
## probrem
There's an interesting script in the user's home directory The work computer is running SSH. We've been given a script which performs some basic calculations, explore the script and find a flag.
## 難しさ
普通
## 解法
sshにつないてファイルを見てみる
```
picoplayer@challenge:~$ ls
useless
picoplayer@challenge:~$ cat useless
#!/bin/bash
# Basic mathematical operations via command-line arguments

if [ $# != 3 ]
then
  echo "Read the code first"
else
        if [[ "$1" == "add" ]]
        then
          sum=$(( $2 + $3 ))
          echo "The Sum is: $sum"

        elif [[ "$1" == "sub" ]]
        then
          sub=$(( $2 - $3 ))
          echo "The Substract is: $sub"

        elif [[ "$1" == "div" ]]
        then
          div=$(( $2 / $3 ))
          echo "The quotient is: $div"

        elif [[ "$1" == "mul" ]]
        then
          mul=$(( $2 * $3 ))
          echo "The product is: $mul"

        else
          echo "Read the manual"

        fi
fi
```
マニュアルを読めとあるのでマニュアルを読む。
```
picoplayer@challenge:~$ man useless

useless
       useless, — This is a simple calculator script

SYNOPSIS
       [add sub mul div] number1 number2

DESCRIPTION
       Use the macro to make simple calulations like addition,subtraction, multiplication and division.

Examples
       ./useless add 1 2
         This will add 1 and 2 and return 3

       ./useless mul 2 3
         This will return 6 as a product of 2 and 3

       ./useless div 6 3
         This will return 2 as a quotient of 6 and 3

       ./useless sub 6 5
         This will return 1 as a remainder of substraction of 5 from 6

Authors
       This script was designed and developed by Cylab Africa

       academy{us3l3ss_ch4ll3ng3_3xpl0it3d_4318}

```
するとフラグが出現。
## 使用コマンド
マニュアルを見るコマンド
```
man ファイル名
```
## 答え
```
academy{us3l3ss_ch4ll3ng3_3xpl0it3d_4318}

```
## ここから学んだこと
manコマンドの使い方やbash 実行ファイルで引数を指定して実行できるということ。
＄nでn番目の引数を用いる。
## つぎに考えること
manコマンドを知らなかったのでもっとコマンドに対して知識をつける。


