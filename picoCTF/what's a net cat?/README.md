## category
General skills
## probrem
Using netcat (nc) is going to be pretty important. Can you connect to **fickle-tempest.picoctf.net** at port **65210** to get the flag?
## 難しさ
簡単
## 解法
ターミナルでnc(netcat)を使う。のでubuntu起動する。<br>
```wsl```<br>
そして与えられたポート番号とIPアドレスでncのコマンドを入力<br>
```nc fickle-tempest.picoctf.net 65167```<br>
するとフラグが出現。
## 使用コマンド
ポート番号を利用してTCP接続を行うコマンド<br>
```nc　接続先IPアドレス ポート番号```
## 答え
```picoCTF{nEtCat_Mast3ry_0d33dA2C}```
## ここから学んだこと
ncとは**ファイル転送や接続ができるネットワークツール**であること。<br>
TCPやUDPの違い。<br>
**TCP**　正確さを重視。　メールやwebサイトに利用。<br>
**UDP**　速さを重視。　　ライブ配信やオンラインゲーム<br>
ポート番号やIPアドレス、サーバーの流れ。<br>
TCP/IP接続ではアプリケーション層から始まりトランスポート層、データリンク層、物理層を通っていく。<br>
ポート番号の役割はサービスの区別をすることとデバイス元を表したりする。<br>
よく使われるたとえでマンションの住所がIPアドレスでポート番号で部屋番号がポート番号である。<br>
話が逸れるがIPアドレスとMACアドレスの違いはゴールまでの途中で変わるか変わらないかである。<br>
MACアドレスは中継ごとにかわる。逆に言い換えると中継先を表すためにMACアドレスが必要である。<br>
IPアドレスのみだとゴールしかわからず途中の道順、中継経路が分からないのでたどり着けない。<br>
サーバーはパソコンと同じような中身を持っている。<br>
またパソコンをサーバーのようにしてポート番号を開くこともできる<br>
## つぎに考えること
sshやncの使い分け
