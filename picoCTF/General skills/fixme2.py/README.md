## category
General skills
## probrem
Fix the syntax error in the Python script to print the flag.
## 難しさ
簡単
## 解法
pythonファイルの中身を見ていく。
```
if flag = "":
  print('String XOR encountered a problem, quitting.')
else:
  print('That is correct! Here\'s your flag: ' + flag)

```
同値条件は　**=**　ではなく　**==**　なのでそこを修正してフラグをゲット。
## 使用コマンド
## 答え
```picoCTF{3qu4l1ty_n0t_4551gnm3nt_4863e11b}```
## ここから学んだこと
pythonの比較演算子
## つぎに考えること
今回は文法の間違いだったがロジックなどになったらどう対処していくか
