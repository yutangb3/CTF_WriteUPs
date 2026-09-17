## category
General skills
## probrem
Can you make sense of this file?

Download the file here

## 難しさ
簡単
## 解法
まずはファイルの種類を確認する。
```
file enc_flag
enc_flag: ASCII text
```
なので中身を見てみる。
```
 cat enc_flag
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbHBWV0VKVVZGWm9RMlZzV2tWUmJFNVNDbUpXV25wWmExSmhWMGRHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==

```
英数字の大文字小文字が続き最後に==があるのでこれはbase64で符号化された可能性が高い。
上記の特徴がなくなるまで繰り返していくとフラグが出現。
```
base64 -d enc_flag | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d
picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_dfe803c6}
```
## 使用コマンド
### base64のデコード
```
base64 -d
```
## 答え
```picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_dfe803c6}```
## ここから学んだこと
ただむやみにいろいろな方法を試すのではなくしっかり規則や特徴を洗い出す。
## つぎに考えること
様々な符号化や暗号化を理解する。
