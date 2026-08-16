## category
General skills
## probrem
Kishor Balan tipped us off that the following code may need inspection
## 難しさ
簡単
## 解法
まずサイトを見るとhtml,css,javaを使って作りました。と表示される。<br>
この時点でflagがhtml,css,javaのどこかにあると予想。<br>
なのでブラウザの検証ツールF12を使ってファイルの中身を見ていく。<br>
するとそれぞれのファイルのコメントににflagの一部分が埋められていた。<br>
**html**
```
<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->
```
**css**
```
/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */
```
**java**
```
/* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?302945a7} */
```
## 使用コマンド
## 答え
```picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?302945a7}```
## ここから学んだこと
## つぎに考えること
これを応用させてjsのコードを修正すると仕掛けでflagが出現<br>
する問題が出るかもしれないと考えた。<br>
そこまで行くとctfの域を超えてしまうかもしれないが<br>
作問するならどうするかという風に考えるのも<br>
大切だなと感じた。<br>
