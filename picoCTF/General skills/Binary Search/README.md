## category
General skills
## probrem
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.

Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!

You can download the challenge files here:

challenge.zip
ssh -p 50073 ctf-player@atlas.picoctf.net
Using the password 6dd28e9b. Accept the fingerprint with yes, and ls once connected to begin. Remember, in a shell, passwords are hidden!

## 難しさ
簡単
## 解法
問題文通りに接続すると二分探索の問題がでる。
それにこたえて効率よく答えていくとflagが出現。
```
The authenticity of host '[atlas.picoctf.net]:50073 ([18.217.83.136]:50073)' can't be established.
ED25519 key fingerprint is: SHA256:M8hXanE8l/Yzfs8iuxNsuFL4vCzCKEIlM/3hpO13tfQ
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[atlas.picoctf.net]:50073' (ED25519) to the list of known hosts.
** WARNING: connection is not using a post-quantum key exchange algorithm.
** This session may be vulnerable to "store now, decrypt later" attacks.
** The server may need to be upgraded. See https://openssh.com/pq.html
ctf-player@atlas.picoctf.net's password:
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 250
Higher! Try again.
Enter your guess: 375
Lower! Try again.
Enter your guess: 312
Higher! Try again.
Enter your guess: 345
Higher! Try again.
Enter your guess: 360
Higher! Try again.
Enter your guess: 367
Congratulations! You guessed the correct number: 367
Here's your flag: picoCTF{g00d_gu355_de9570b0}
Connection to atlas.picoctf.net closed.
```

## 使用コマンド
## 答え
```picoCTF{g00d_gu355_de9570b0}```
## ここから学んだこと
古典的だが調べる回数を圧倒的に減らすことができる。
## つぎに考えること
pythonで自動化
場合分けして中央値をとっていけばいけそう。

