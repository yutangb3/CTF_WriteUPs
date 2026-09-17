## category
General skills
## probrem
If you want to hash with the best, beat this test!

nc saturn.picoctf.net 52961
## 難しさ
簡単
## 解法
ncで接続してみると次のものが出てくる。
```
nc saturn.picoctf.net 52961
Please md5 hash the text between quotes, excluding the quotes: 'Andy Warhol'
Answer:
```
なのでmd5ハッシュ化してその値を送っていけばよい。
```
echo -n "Andy Warhol" | md5sum
```
同じことを繰り返していくとフラグをゲット。
```
nc saturn.picoctf.net 52961
Please md5 hash the text between quotes, excluding the quotes: 'Andy Warhol'
Answer:
024e803352db3cd645a396423ac12c31
024e803352db3cd645a396423ac12c31
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'Cleopatra'
Answer:
Cleopatra
Cleopatra
Incorrect. Try again?
Answer:
f8cbe5a99675fff11ed4d83fc16e2071
f8cbe5a99675fff11ed4d83fc16e2071
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'Helen Keller'
Answer:
c0aac1554fe46e67f218df124c318054
c0aac1554fe46e67f218df124c318054
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}
```
## 使用コマンド
### md5ハッシュ化
```
echo -n "文字列"　| md5sum
```
## 答え
```picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}```
## ここから学んだこと
linuxのハッシュ化の方法
## つぎに考えること
ハッシュの解読など。
