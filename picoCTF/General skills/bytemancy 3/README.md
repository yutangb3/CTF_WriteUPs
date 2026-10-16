## category
General skills
## probrem
Can you conjure the right bytes? The program's source code can be downloaded here
 and the compiled spellbook binary can be downloaded here
. Connect to the program with netcat:
## 難しさ
簡単
## 解法
まずはファイルの中身を確認してNCにつないでみる。
```
SPELLBOOK_FUNCTIONS = [
    "ember_sigil",
    "glyph_conflux",
    "astral_spark",
    "binding_word",
]
```
この四つがカギになりそう。
ncでつないでみると
```
⊹──────[ BYTEMANCY-3 ]──────⊹
☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐

I will name four procedures hidden inside spellbook.
Each round, send me their *raw* 4-byte addresses in little-endian form. 3 correct answers unlock the flag.

☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐
⊹─────────────⟡─────────────⊹
[1/3] Send the 4-byte little-endian address for procedure 'ember_sigil'.
==>
```
生のデータをリトルエンディアン、つまり小さい下位バイトから並べてかつ生のバイナリを送りたいので
ターミナルでアドレスを調べてpythonで
pwntoolsを使用。
```
objdump -d -M intel  --endian=little spellbook > spellbook.log
```
```
from pwn import *

p=remote("xebec.cylabacademy.net",14290)

for i in range(3):
    data = p.recvuntil(b"==>")

    if b"astral_spark" in data:
        p.send(p32(0x08049199,endian="little"))
    elif b"ember_sigil" in data:
        p.send(p32(0x08049156,endian="little"))
    elif b"glyph_conflux" in data:
        p.send(p32(0x08049176,endian="little"))
    elif b"binding_word" in data:
        p.send(p32(0x080491b7,endian="little"))


p.interactive()
```
実行するとフラグをゲット。
## 使用コマンド
### pwnにおいてリトルエンディアン指定の方法
```
p32("b0x???????",endian="little)
```
### objdumpの使い方
-dで逆アセンブル、-M intel でインテル構文で表示。 --endian=little
```
objdump -d -M intel  --endian=little
```
## 答え
```academy{0bjdump_m4g1c_c79394e0}```
## ここから学んだこと
pwnで文字列が来るまで情報を待てるということ
## つぎに考えること
pythonコードをもっと自分のみで書いて理解できるように練習を積むこと
