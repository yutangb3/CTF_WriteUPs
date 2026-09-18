## category
General skills
## probrem
Run the Python script and convert the given number from decimal to binary to get the flag.
## 難しさ
簡単
## 解法
pythonファイルを実行する。
```
 python .\convertme.py
If 42 is in decimal base, what is it in binary base?
Answer:
```
ここでlinuxで42を二進数で表す。
```
echo "ibase=10;obase=2;42" |  bc
101010
```
後は答えを入力してフラグをゲット。
## 使用コマンド
### 基数変換
二進数から十進数へ変換
```
echo "ibase=2;obase=10;数字" | bc
```
## 答え
```picoCTF{4ll_y0ur_b4535_722f6b39}```
## ここから学んだこと
基数変換
## つぎに考えること
コードをいじれたらどこをいじってフラグをゲットするかを考える。
