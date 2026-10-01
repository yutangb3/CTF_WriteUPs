## category
General skills
## probrem
Dear Threat Intelligence Analyst,

Quick heads up - we stumbled upon a shady executable file on one of our employee's Windows PCs. Good news: the employee didn't take the bait and flagged it to our InfoSec crew.

Seems like this file sneaked past our Intrusion Detection Systems, indicating a fresh threat with no matching signatures in our database.

Can you dive into this file and whip up some YARA rules? We need to make sure we catch this thing if it pops up again.

Thanks a bunch!

The suspicious file can be downloaded here
. Unzip the archive with the password picoctf Once you have created the YARA rule/signature, submit your rule file as follows:

socat -t60 - TCP:chatelaine.cylabacademy.net:45244 < sample.txt

(In the above command, modify "sample.txt" to whatever filename you use).

When you submit your rule, it will undergo testing with various test cases. If it successfully passes all the test cases, you'll receive your flag.
## 難しさ
普通
## 解法
まずはヒントにパックとアンパックのすべて場合をテストするとあるので一旦**UPX0**で検索してみる。
```
rule picoctf{
	strings:
		$a = "UPX0" wide ascii
	condition:
		$a 
}
```
すると
```
socat -t60 - TCP:chatelaine.cylabacademy.net:45244 < yara.txt
:::::

Status: Failed
False Negatives Check: Testcase failed. Your rule generated a false negative.
False Positives Check: Testcases passed!
Stats: 62 testcase(s) passed. 1 failed. 1 testcase(s) unchecked. 64 total testcases.
Pass all the testcases to get the flag.

:::::
```
UPX0で調べた限りは誤検知がない。
UPX0を持たない悪性。つまりアンパックされたほうで悪性のものを見逃してしまっている可能性が考えられる。
なので一旦unpackしてその中でみてみる。
```
upx -d suspicious/suspicious.exe
```
次にwindowsAPIのセキュリティに関するもので絞りこむ。
なぜなら今回windowsの実行ファイルであるから。権限周りなどが怪しい。
```
rule picoctf{
	strings:
		$a = "UPX0" wide ascii
		$b = "AdjustTokenPrivileges" wide ascii
	condition:
		$a or $b
}
```
すると
```
 socat -t60 - TCP:chatelaine.cylabacademy.net:45244 < yara.txt
:::::

Status: Failed
False Negatives Check: Testcases passed!
False Positives Check: Testcase failed. Your rule generated a false positive.
Stats: 25 testcase(s) passed. 1 failed. 38 testcase(s) unchecked. 64 total testcases.
Pass all the testcases to get the flag.

:::::
```
今度は悪性を完全に検知できたものの良性を悪性と判断してしまっている。
つまり悪性を絞るための条件をもっと絞る。
```
rule picoctf{
	strings:
		$a = "UPX0" wide ascii
		$b = "AdjustTokenPrivileges" wide ascii
		$c = "LookupPrivilegeValueW" wide ascii
	condition:
		$a or ($b and $c)
}
```
するとフラグをゲット。
## 使用コマンド
### アンパック化
```
upx -d ファイル名
```
## 答え
```academy{yara_rul35_r0ckzzz_790c7af6}```
## ここから学んだこと
### yara RUle
**yara Rule**とは危ないファイルを中身の特徴的な文字列などで事前に設定したrulesで
パターンマッチングで検出するツールです。
### asciiとwideについて
**ascii**と**wide**という指定方法があります。簡単に言うと文字列をバイナリ表示するときに文字単位の区切りの**00**が入るか入らないかです。そして
今回両方とも指定しないといけない理由はwindowsのプログラムでは同じhelloでも用途やプログラムで違うので今回のように
二つの種類のどちらの両方の可能性があるということです。
### パックとは
これは元のプログラムや文字列を圧縮、変換したりするものです。目的はおもにサイズを小さくするためであったりセキュリティではプログラムを解析する人が分析しよう
としたときに分からなくするためです。
## つぎに考えること
今回は偶然が多い。もっと論理的に絞り込めるように知識をつける。


