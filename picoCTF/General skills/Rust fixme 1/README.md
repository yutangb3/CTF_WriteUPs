## category
General skills
## probrem
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!

Download the Rust code here
.
## 難しさ
簡単
## 解法
プログラミングコードの修正をしたらフラグをゲットできそう
```
 let key = String::from("CSUCKS") // How do we end statements in Rust?
```
文章は通常　**;**　で終わらせるのでそれをつける。
```
 let key = String::from("CSUCKS"); // How do we end statements in Rust?
```
次の修正箇所はこれです。
```
if res.is_err() {
        ret // How do we return in rust?
    }
```
retじゃなくてreturnで返す
```
if res.is_err() {
        return; // How do we return in rust?
    }
```
そして最後に見てみると
```
println!(
        ":?", // How do we print out a variable in the println function? 
        String::from_utf8_lossy(&decrypted_buffer)
    );
```
c言語みたいにprintで変数を表す時　**{}** をいれる。
そしてターミナルでcargo runするとflagをゲット。
## 使用コマンド
###　rustファイルの実行方法
```
cargo run
```
## 答え
```picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}```
## ここから学んだこと
プログラミング言語rustのこと
rustはメモリ管理を徹底しているためセキュリティが高い。
## つぎに考えること
rustならではの文法を身に着ける。

