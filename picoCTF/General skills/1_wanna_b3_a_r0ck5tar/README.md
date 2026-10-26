## category
General skills
## probrem
I wrote you another song
. Put the flag in the academy{} flag format
## 難しさ
普通
## 解法
ファイルの中身がアスキーテキストなので表示してみる。
```
strings r0ck5tar-lyrics.txt
Rocknroll is right
Silence is wrong
A guitar is a six-string
Tommy's been down
Music is a billboard-burning razzmatazz!
Listen to the music
If the music is a guitar
Say "Keep on rocking!"
Listen to the rhythm
If the rhythm without Music is nothing
Tommy is rockin guitar
Shout Tommy!
Music is amazing sensation
Jamming is awesome presence
Scream Music!
Scream Jamming!
Tommy is playing rock
Scream Tommy!
They are dazzled audiences
Shout it!
Rock is electric heaven
Scream it!
Tommy is jukebox god
Say it!
Break it down
Shout "Bring on the rock!"
Else Whisper "That ain't it, Chief"
Break it down
```
今回まったく手がかりをつかめない。
調べてみるとrockstar言語という。
```
Listen to the music
If the music is a guitar
```
guitarは
```
A guitar is a six-string
```
コンパイルすると10と表示。
```
If the rhythm without Music is nothing
```
入力からmusicを引くと０になるようにrhythmに値を入れます。
今回musicは170なので入力は170にします。
ブラウザでrockstarを実行できるサイトがあるので実行すると
```
Reset
Parse
Keep on rocking!
66
79
78
74
79
86
73
```
後はアスキーに直したらフラグをゲット。
## 使用コマンド
## 答え
```
academy{BONJOVI}
```
## ここから学んだこと
ただのテキストに見えても処理が隠されている。
## つぎに考えること
他にもただの写真や動画などでもいろいろ隠せたりできそうなのでそこらへんの
方法をよりキャッチアップしていきたい。
