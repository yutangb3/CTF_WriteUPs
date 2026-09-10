## category
General skills
## probrem
Can you conjure the right bytes? The program's source code can be downloaded here
.
## 難しさ
簡単
## 解法
wslでlinuxを起動してncで接続する。
すると以下の文が出てくる。
```
⊹──────[ BYTEMANCY-0 ]──────⊹
☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐

Send me ASCII DECIMAL 101, 101, 101, side-by-side, no space.

☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐☉⟊☽☈⟁⧋⟡☍⟐
⊹─────────────⟡─────────────⊹
==> 
```
つまりアスキーコード表の10進数で101を指しているのは
'e'なのでeを三回入力すればよい。
するとフラグをゲット。

## 使用コマンド
## 答え
```picoCTF{pr1n74813_ch4r5_2f7a75e5}```
## ここから学んだこと
decimalは10進数ということ。
## つぎに考えること
繰り返しの入力で100回以上あったらどうするか
