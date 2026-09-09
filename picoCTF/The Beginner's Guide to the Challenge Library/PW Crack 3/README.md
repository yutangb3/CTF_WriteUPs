## category
General skills
## probrem
Can you crack the password to get the flag?

Download the password checker here
 and you'll need the encrypted flag
 and the hash
 in the same directory too.

There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.
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

flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()
print(correct_pw_hash)


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_3_pw_check()


# The strings below are 7 possibilities for the correct password. 
#   (Only 1 is correct)
pos_pw_list = ["f09e", "4dcf", "87ab", "dba8", "752e", "3961", "f159"]


```
同じ階層のファイルがハッシュ値であり、それと入力したものをハッシュ化するとフラグが
出るようなプログラムになっている。７個しかないのでどんどんいれていく。

するとフラグが出現。
## 使用コマンド
**pythonファイル起動**
```
python file名
```
## 答え
```
picoCTF{m45h_fl1ng1ng_cd6ed2eb}
```
## ここから学んだこと
md5という暗号学的に破られている暗号化法。ハッシュ関数。
## つぎに考えること
総当たりできる数だったので次はmd5を生かして
ハッシュ値から平文を割り出す方法を活用したい。
