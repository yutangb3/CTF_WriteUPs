## category
General skills
## probrem
Our flag printing service has started glitching!
## 難しさ
簡単
## 解法
まずはncでつないでみる。
```
 nc saturn.picoctf.net 53579
'picoCTF{gl17ch_m3_n07_' + chr(0x39) + chr(0x63) + chr(0x34) + chr(0x32) + chr(0x61) + chr(0x34) + chr(0x35) + chr(0x64) + '}'
```
chr関数なのでpythonでもじれつに変換する。
```
print(f"picoCTFgl17ch_m3_n07_' + {chr(0x39) + chr(0x63) + chr(0x34) + chr(0x32) + chr(0x61) + chr(0x34) + chr(0x35) + chr(0x64)} + '")

```
じっこうすると
```
picoCTFgl17ch_m3_n07_' + 9c42a45d + '
```
フラグの形に直したらフラグをゲット。
## 使用コマンド
## 答え
```picoCTF{gl17ch_m3_n07_9c42a45d}```
## ここから学んだこと
chr関数
## つぎに考えること
ほかにスマートなやり方を考える。

