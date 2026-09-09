## category
General skills
## probrem
Python scripts are invoked kind of like programs in the Terminal...
Can you run ende.py using password.txt to get flag.txt.en?
## 難しさ
簡単
## 解法
pythonのコードを読んでみる。
するとhelp_usageという使い方メッセージに
こうかかれている。
```
"'$ python "+ sys.argv[0] +" -d pole.txt'\n"
```
なので実際に入力してみる
```
python ende.py -d .\flag.txt.en
```
するとこう出力される
```
Please enter the password:
```
password.txtの中身を入力する。
するとフラグが得られる。
## 使用コマンド
## 答え
```
picoCTF{4p0110_1n_7h3_h0us3_9c5f9bcf}
```
## ここから学んだこと
pythonのsysについて。
これはpythonのインタープリンタに関する
機能や情報を加えるモジュール。
### 異常終了
```
sys.exit(1)
```
### コマンドラインに引数を渡す
```
sys.argv
```
通常```sys.argv(0)はスクリプト名。

bese64の再確認

## つぎに考えること
もし使い方のヘルプがなければ
どのように進めていけばよいのか。
これを一周したら自分で実装してみるのもいいなと思った。
