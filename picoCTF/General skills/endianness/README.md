## category
General skills
## probrem
Know of little and big endian?
## 難しさ
簡単
## 解法
まずはインスタンスを立ち上げてみる。
```
nc titan.picoctf.net 61093
Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: xzovf
Enter the Little Endian representation:
```
なのでまずは単語の　xzovf を16進数表記を行う。
```
echo -n 'xzovf' | hexdump -C
00000000  78 7a 6f 76 66                                    |xzovf|
00000005
```
あとはビッグエンディアンとリトルエンディアンに並べなおせばふらぐをゲット
## 使用コマンド
### 最後の空白をなくすecho 
```
echo -n '文字列'
```
### 文字列を16進数表記
オプション<br>
**-c 数字**で一行あたりに何バイト表示するかを指定。<br>
**-C**　でアスキーコード表と一文字ずつ照らし合わしながら表示
```
hexdump
```
## 答え
```picoCTF{3ndi4n_sw4p_su33ess_d58517b6}```
## ここから学んだこと
リトルエンディアンはバイト列を逆順で表したもの
ビッグエンディアンはバイト列をそのまま先頭から表したもの。
コンピューターが扱いやすいように16進数で表記。
アスキーコードの一文字は2byteである。
## つぎに考えること
これがどうセキュリティにかかわってくるのかをしっかり考える。

