## category
General skills
## probrem
Oops! Someone accidentally sent an important file to a network printer—can you retrieve it from the print server?
## 難しさ
簡単
## 解法
まずはインスタンスを立ち上げてncでつないでいく。
```
nc -vz mysterious-sea.picoctf.net 62882
```
するとポート番号があいていることが
分かったが何のサービスかはわからない。
nmapを使って調べる
```
nmap -sV -p 61270 mysterious-sea.picoctf.net
```
すると以下のことが判明。
```
PORT      STATE SERVICE     VERSION
61270/tcp open  netbios-ssn Samba smbd 4
```
なのでsmbclientをつかってファイルを探していく。
```
smbclient -L //mysterious-sea.picoctf.net/shares/ -p 62882 -N
```
すると以下のことがでてきた
```

        Sharename       Type      Comment
        ---------       ----      -------
        shares          Disk      Public Share With Guests
        IPC$            IPC       IPC Service (Samba 4.19.5-Ubuntu)
Reconnecting with SMB1 for workgroup listing.
do_connect: Connection to mysterious-sea.picoctf.net failed (Error NT_STATUS_IO_TIMEOUT)
Unable to connect with SMB1 -- no workgroup available

```
公開されているshareに注目してlsコマンドで中身を見てみる。
```
smbclient //mysterious-sea.picoctf.net/shares -p 62882 -N
smb: \> ls
```
すると
```
smb: \> ls
  .                                   D        0  Sat Mar  7 05:25:41 2026
  ..                                  D        0  Sat Mar  7 05:25:41 2026
  dummy.txt                           N     1142  Thu Feb  5 06:22:17 2026
  flag.txt                            N       37  Sat Mar  7 05:25:41 2026

                65536 blocks of size 1024. 58680 blocks available
```
flag.txtに答えがありそうなのでダウンロードする。
```
smb: \> get flag.txt
getting file \flag.txt of size 37 as flag.txt (0.0 KiloBytes/sec) (average 0.0 KiloBytes/sec)
smb: \> exit
```
ファイルをilnuxで確認するとフラグが出現。

## 使用コマンド
### nmapコマンドの使い方
-sVオプションでサービスについて調べる。
-pでポート番号を指定。
```
nmap オプション　IPアドレス
```
### smbclientコマンドの使い方
-Lで共有ファイル一覧
-pでポート番号指定
-Nで匿名アクセス(パスワードなし)
```
nmap -L ipアドレス　オプション
```
**ファイルをダウンロード**
```
smb: \> get ファイル名
```

## 答え
```picoCTF{5mb_pr1nter_5h4re5_2f61915b}```
## ここから学んだこと
smbclientとはファイルを共有できるもの
ncでポート接続をしてどんなサービスかを調べるときはnmap
ncの初めはホスト。
## つぎに考えること
smbclientのセキュリティ面について考える。
