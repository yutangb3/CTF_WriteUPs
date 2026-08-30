## category
General skills
## probrem
Download this image file and find the flag.

Download image file
## 難しさ
普通
## 解法
htmlファイルなのでも検証ツールを使ってしらべていく。
この時に  svg要素なのでtextに怪しいところがないかを調べてみる。
すると以下の部分を発見
```
<text xmlns="http://www.w3.org/2000/svg" xml:space="preserve" style="font-style:normal;font-weight:normal;font-size: 150px;line-height: 1;font-family:sans-serif;letter-spacing: 1;word-spacing: 1;fill: red;fill-opacity:1;stroke:none;stroke-width:0.26458332;" x="800" y="132.08501" id="text3723"><tspan xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd" sodipodi:role="line" x="107.43014" y="132.08501" style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;" id="tspan3748">**p** </tspan><tspan xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd" sodipodi:role="line" x="107.43014" y="132.08942" style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;" id="tspan3754">**i** </tspan><tspan xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd" sodipodi:role="line" x="107.43014" y="132.09383" style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;" id="tspan3756">**c** </tspan><tspan xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd" sodipodi:role="line" x="107.43014" y="132.09824" style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;" id="tspan3758">**o** </tspan><tspan xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd" sodipodi:role="line" x="107.43014" y="132.10265" style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;" id="tspan3760">**C** </tspan><tspan xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd" sodipodi:role="line" x="107.43014" y="132.10706" style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;" id="tspan3762">**T** </tspan><tspan xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd" sodipodi:role="line" x="107.43014" y="132.11147" style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;" id="tspan3764">**F { 3 n h 4 n **</tspan><tspan xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd" sodipodi:role="line" x="107.43014" y="132.11588" style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;" id="tspan3752">**c 3 d _ d 0 a 7 5 7 b f }**</tspan></text>
```
## 使用コマンド
## 答え
```
picoCTF{3nh4nc3d_24374675}
```
## ここから学んだこと
検証ツールでみていく。flagがバラバラになっているものもある。
## つぎに考えること
今回の意図をあまり組めなかったので解けてよしで終わるのではなく
しっかりその意図を考えて
本質を見抜く習慣を徹底したい。
