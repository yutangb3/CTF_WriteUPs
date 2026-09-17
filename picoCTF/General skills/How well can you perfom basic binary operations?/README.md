## category
General skills
## probrem
How well can you perfom basic binary operations?
## 難しさ
簡単
## 解法
ncで接続して二進数の計算をひたすら行う。
```
Binary Number 1: 00001101
Binary Number 2: 01011100


Question 1/6:
Operation 1: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 0
Incorrect. Try again
Enter the binary result: 
```
別のシェルで計算する。
```
 echo "obase=2; $((2#01011100 >> 1))" | bc
101110
```
後は同じように6回正解するとフラグをゲット。
## 使用コマンド
### linuxで算術演算
```
$((計算式)))
```
### n進数表記。
```
n#数字
```
### 基数変換表示
オプション<br>
obase = output なので出力後の基数を指定。<br>
ibase = input  なので入力時の基数を指定。<br>
```
echo "obase=m;ibase=n;数字" | bc
```
## 答え
```picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_aeaf4b09}```
## ここから学んだこと
二進数の演算子とlinuxの記号の対応関係。<br>
& はANDで論理積<br>
| はORで論理和<br>
^ はxorで排他的論理和<br>
~ はnotで否定<br>
**>>** は右シフト.。<br>
<< は左シフト。<br>
## つぎに考えること
いかにはやくコマンドなどを駆使して時間短縮を目指す。
