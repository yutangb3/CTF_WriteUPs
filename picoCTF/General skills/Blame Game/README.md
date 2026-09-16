## category
General skills
## probrem
Someone's commits seems to be preventing the program from working. Who is it?

You can download the challenge files here:

challenge.zip
## 難しさ
簡単
## 解法
まずはgitの履歴を確認。
長いのでひたすら見ていくと下のほうに何やら発見。
```
commit 9ae3e1bc67ad0143c611c5f65399b79850d20983
Author: picoCTF{@sk_th3_1nt3rn_b64c4705} <ops@picoctf.com>
Date:   Sat Mar 9 21:09:01 2024 +0000

    optimize file size of prod code

commit f3cec26cf7f80f91b5c3d1972f14dd4e9f97ec83
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:01 2024 +0000

    create top secret project

```
フラグをゲット。
## 使用コマンド
### gitの差分ファイルのコマンド
今回、これを打っても何も表示されなかったためファイルを実行しても<br>
意味がないとはんだんできる。<br>
AからBまでのコミットの差分表示。<br>
D 削除ファイル<br>
A 追加ファイル<br>
M 変更ファイル<br>
```
git diff --name-status 'A..B'
```
## 答え
```picoCTF{@sk_th3_1nt3rn_b64c4705}```
## ここから学んだこと
頭を固くしすぎない。灯台元暮らし。
## つぎに考えること
git関連のコマンドをもっと習得する。
