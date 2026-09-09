## category
General skills
## probrem
Can you crack the password to get the flag?
Download the password checker here
and you'll need the encrypted flag
in the same directory too.Python scripts are invoked kind of like programs in the Terminal...
Can you run ende.py using password.txt to get flag.txt.en?
## 難しさ
簡単
## 解法
とりあえずpythonのコードを読んでみる。
すると以下のコードを発見。
```
 user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "691d"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
```
つまりinputに691dを入れるとflagがゲットできる。
pythonファイルを実行する。
そして691dを入力するとflagをゲット。
## 使用コマンド
## 答え
```
picoCTF{545h_r1ng1ng_56891419}
```
## ここから学んだこと
pwを探すのも大事だが初めから書かれていることもある。
## つぎに考えること
難易度としては本当に低いので
前の問題のようにコードを理解したうえで溶けるようになりたい。
