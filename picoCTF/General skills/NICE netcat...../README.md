## category
General skills
## probrem
There is a nice program that you can talk to by using this command in a shell:
## 難しさ
簡単
## 解法
まずはnetcatにつないで内容を見てみる。
```
nc wily-courier.picoctf.net 56028
112
105
99
111
67
84
70
123
103
48
48
100
95
107
49
116
116
121
33
95
110
49
99
51
95
107
49
116
116
121
33
95
100
57
52
55
54
125
10
```
ここで考えたのはすべて128以下の数字であるということ。
つまり8bit単位の二進数で表すことが可能。
16進数に直していくと文字列が得られるかもしれない。
改行コードを削除して文字列をxxdコマンドで出す。
```
  nc wily-courier.picoctf.net 56028  tr -d "\n" | xxd -p -r
```
するとフラグが出現
## 使用コマンド
### trコマンド
**-d**オプションは削除する文字を指定。
```
tr -d "文字"
```

## 答え
```picoCTF{g00d_k1tty!_n1c3_k1tty!_d9476}```
## ここから学んだこと
xxdコマンドは文字列と16進数を変換するのではない。バイナリデータ。
trコマンドは削除も可能。
## つぎに考えること
色々な数値からでも範囲や特徴からしぼっていく。
