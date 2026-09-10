## category
General skills
## probrem
After logging in, you will find multiple file parts in your home directory. These parts need to be combined and extracted to reveal the flag.
## 難しさ
簡単
## 解法
まずはsshで接続を試みる。
```
ssh ctf-player@dolphin-cove.picoctf.net -p 53166
```
するとサーバー側のlinuxのターミナルらしきものが表れたので
lsコマンドでファイル構造などを確認。
```
ctf-player@pico-chall$ ls
instructions.txt  part_aa  part_ab  part_ac  part_ad  part_ae
```
いったんinstructions.txtを見てみる。
```
ctf-player@pico-chall$ cat instructions.txt
Hint:

- The flag is split into multiple parts as a zipped file.
- Use Linux commands to combine the parts into one file.
- The zip file is password protected. Use this "supersecret" password to extract the zip file.
- After unzipping, check the extracted text file for the flag.
```
つまりファイルを結合して解凍する時にはパスワードを打つ必要があると判明。
なので今度はcatコマンドで結合して新しいファイルを作り出す。
```
ctf-player@pico-chall$ cat part_aa part_ab part_ac part_ad part_ae > flag1.txt
```
そしてもう一度確認すると
```
ctf-player@pico-chall$ ls
flag1.txt  instructions.txt  part_aa  part_ab  part_ac  part_ad  part_ae
```
なので今度は結合したファイルの情報を見てみる。
```
ctf-player@pico-chall$ file flag1.txt
flag1.txt: Zip archive data, at least v1.0 to extract
```
このことからzipファイルで圧縮されているので解凍する。
```
ctf-player@pico-chall$ unzip flag1.txt
```
パスワードを求められたので先ほどのパスワードを入力する。
そしてcatコマンドでフラグが出現。
## 使用コマンド
### sshでポート番号指定して接続
```
ssh user名@IPアドレス　-p ポート番号
```
### zipファイルを解凍する
```
unzip ファイル名
```
## 答え
```picoCTF{z1p_and_spl1t_f1l3s_4r3_fun_da494d2e}```
## ここから学んだこと
ファイルの解凍方法
catコマンドの本当の理解
## つぎに考えること
sshについての深い理解。
今回なぜターミナルみたいに使えたのか
