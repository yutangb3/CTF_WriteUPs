## category
General skills
## probrem
Can you crack the password to get the flag?

Download the password checker here
 and you'll need the encrypted flag
 and the hash
 in the same directory too. Here's a dictionary
 with all possible passwords based on the password conventions we've seen so far.
## 難しさ
簡単
## 解法
とりあえずpythonのコードを読んでみる。
```
import hashlib

### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level5.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level5.hash.bin', 'rb').read()


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_5_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_5_pw_check()


```
ここでpw crack4と同様にパスワードがほかのファイルに約６万個ある。
なのでpythonのテキストファイルをよみこみ、リスト化するコードを書く。
```
with open('dictionary.txt') as f:
    new_list=[s.rstrip() for s in f.readlines()]
```
newlistで内包的な書き方をしてリストとして読み込むのはいいが末尾の**/n**が邪魔なので
rstripで右端の文字を消す操作を挟む。
```
with open('dictionary.txt') as f:
    new_list=[s.rstrip() for s in f.readlines()]
```
そしてfor文で入れていく。このときにパスワードが間違っているというprint文を消す。
そうすることにより正しいフラグのみが出現。
```
def level_5_pw_check(i):
    user_pw = i
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
```
すると一つだけフラグが出現。
## 使用コマンド
### ファイルを開く。
```
with open(ファイル名) as f:
```
### リストとして読み込む。
```
f.readlines()
```
### 末尾の文字を削除。
```
rstrip()
```
### リストにある操作をして新しいリストを作る。
```
new_list=[操作　for i in リスト]
```
## 答え
```
picoCTF{h45h_sl1ng1ng_fffcda23}
```
## ここから学んだこと
総当たりや数が多いものはfor文などのループで処理。
いかにして無駄を省くか
## つぎに考えること
md5だけではないsha1などのものも触れていきたい。
