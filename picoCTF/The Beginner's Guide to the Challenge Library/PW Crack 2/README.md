## category
General skills
## probrem
Can you crack the password to get the flag?

Download the password checker here
 and you'll need the encrypted flag
 in the same directory too.
## 難しさ
簡単
## 解法
とりあえずpythonのコードを読んでみる。
すると以下のコードを発見。
```
if( user_pw == chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
```
ここで0xAAはAAに16進数を入れる表記方法と気付く。
pythonでは実際に文字化しているので
コード内に実際に追加してみる。
```
print(chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36))
```
出力されたものがパスワードなので入力するとフラグをゲット。
## 使用コマンド
## 答え
```
picoCTF{tr45h_51ng1ng_489dea9a}
```
## ここから学んだこと
16進数の表記方法、そしてそれらに対応しているのがアスキーコード。
## つぎに考えること
今回はパスワードを合わせにいったがわざわざ合わせにいかなくても
条件分岐をうまく改造したほうが早いんじゃないかと考えた。
