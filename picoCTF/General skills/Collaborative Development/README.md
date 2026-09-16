## category
General skills
## probrem
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?

You can download the challenge files here:

challenge.zip
## 難しさ
簡単
## 解法
まずはgitのlogを確認。
```
git log
commit 54c7842e34d03976ddc080a9dd76742751024358 (HEAD -> main)
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:44 2024 +0000

    init flag printer

```
戻して実行してみたが何も変わらず。
なので今度はheadのログを確認。
```
git reflog
54c7842 (HEAD -> main) HEAD@{0}: reset: moving to 54c7842e34d03976ddc080a9dd76742751024358
54c7842 (HEAD -> main) HEAD@{1}: checkout: moving from feature/part-3 to main
5c00b43 (feature/part-3) HEAD@{2}: commit: add part 3
54c7842 (HEAD -> main) HEAD@{3}: checkout: moving from main to feature/part-3
54c7842 (HEAD -> main) HEAD@{4}: checkout: moving from feature/part-2 to main
d3563a2 (feature/part-2) HEAD@{5}: commit: add part 2
54c7842 (HEAD -> main) HEAD@{6}: checkout: moving from main to feature/part-2
54c7842 (HEAD -> main) HEAD@{7}: checkout: moving from feature/part-1 to main
f65544e (feature/part-1) HEAD@{8}: commit: add part 1
54c7842 (HEAD -> main) HEAD@{9}: checkout: moving from main to feature/part-1
54c7842 (HEAD -> main) HEAD@{10}: commit (initial): init flag printer

```
三つのパートに分かれてなにやらあるのでそれぞれに移動してpythonファイルを実行してつなげると
flagがゲット。
## 使用コマンド
```
git reflog
```
```
git reset --hard [番号]
```
## 答え
```picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_7ffa0077}```
## ここから学んだこと
reflogとlogの違い。
logはコミットの歴史。
reflogはブランチやヘッドの履歴。gitの**参照履歴** だからref
## つぎに考えること
gitのさらなる応用。
