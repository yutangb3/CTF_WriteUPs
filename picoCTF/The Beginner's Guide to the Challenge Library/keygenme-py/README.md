## category
General skills
## probrem
keygenme-trial.py
## 難しさ
普通
## 解法
とりあえずコードで答えに近そうな部分を発見。
```
key_part_static1_trial = "picoCTF{1n_7h3_kk3y_of_"
key_part_dynamic1_trial = "xxxxxxxx"
key_part_static2_trial = "}"
key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial
```
コードを見ていくと以下を発見。
```

def enter_license():
    user_key = input("\nEnter your license key: ")
    user_key = user_key.strip()

    global bUsername_trial
    
    if check_key(user_key, bUsername_trial):
        decrypt_full_version(user_key)
    else:
        print("\nKey is NOT VALID. Check your data entry.\n\n")

```
つまりcheck_key関数をtrueにすればよい。
```
def check_key(key, username_trial):

    global key_full_template_trial

    if len(key) != len(key_full_template_trial):
        return False
    else:
        # Check static base key part --v
        i = 0
        for c in key_part_static1_trial:
            if key[i] != c:
                return False

            i += 1

        # TODO : test performance on toolbox container
        # Check dynamic part --v
        if key[i] != hashlib.sha256(username_trial).hexdigest()[4]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[5]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[3]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[6]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[2]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[7]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[1]:
            return False
        else:
            i += 1

        if key[i] != hashlib.sha256(username_trial).hexdigest()[8]:
            return False



        return True
```
文字数を同じにして初めの**picoctf**を一致させる。
そしてそのあとは順番にhexdigestを並べていけばよい。なので
順番にprintしてpicoCTF{1n_7h3_kk3y_of_xxxxxxxx}に当てはめる。
するとフラグが出現。
## 使用コマンド
## 答え
```picoCTF{1n_7h3_kk3y_of_08c46aa4}```
## ここから学んだこと
全てのコードを見る必要はない。
コードで見るべきところをしっかり取捨選択していくこと。
## つぎに考えること
時間がかかりすぎていたのでもっと何を求められているのかを
考えながらコードを解読していきたい。

