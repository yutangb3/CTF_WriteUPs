## category
General skills
## probrem
## 難しさ
普通
## 解法
まずはkubectlで設定ファイルを確認する。
```
 kubectl --kubeconfig=./kubeconfig.yaml config get-contexts
```
するとdefaultが選択されているので接続してみる。一旦namespaceから探す
```
kubectl --kubeconfig=./kubeconfig.yaml get namespaces
```
そしたら証明書のエラーが出る。なのでtlsの証明を無視してつないでみる。
```
kubectl --kubeconfig=./kubeconfig.yaml --insecure-skip-tls-verify=true get namespaces
NAME              STATUS   AGE
academy           Active   3m24s
default           Active   3m37s
kube-node-lease   Active   3m37s
kube-public       Active   3m37s
kube-system       Active   3m37s
```
ここから問題文にある通りsecretを探す。
```
 kubectl --kubeconfig=./kubeconfig.yaml --insecure-skip-tls-verify=true get secrets -A
NAMESPACE     NAME                           TYPE                               DATA   AGE
academy       ctf-secret                     Opaque                             1      5m41s
kube-system   chart-values-gateway-api-crd   helmcharts.helm.cattle.io/values   0      5m48s
kube-system   chart-values-traefik           helmcharts.helm.cattle.io/values   1      5m46s
kube-system   chart-values-traefik-crd       helmcharts.helm.cattle.io/values   0      5m46s
kube-system   k3s-serving                    kubernetes.io/tls                  2      5m51s
```
academyのところが怪しそうなので検索。
```
kubectl --kubeconfig=./kubeconfig.yaml --insecure-skip-tls-verify=true get secrets ctf-secret -n academy -o yaml
apiVersion: v1
data:
  flag: YWNhZGVteXtrczNjcjM3NV80MW43X3M0ZjNfYzQxMzQ1MjB9Cg==
kind: Secret
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"v1","data":{"flag":"YWNhZGVteXtrczNjcjM3NV80MW43X3M0ZjNfYzQxMzQ1MjB9Cg=="},"kind":"Secret","metadata":{"annotations":{},"name":"ctf-secret","namespace":"academy"},"type":"Opaque"}
  creationTimestamp: "2026-09-27T14:12:40Z"
  name: ctf-secret
  namespace: academy
  resourceVersion: "432"
  uid: 7d636dd6-9932-4130-a6f5-8e82c27f778f
type: Opaque
```
flagはbase64で符号化されているのでもとに戻してフラグが出現。
## 使用コマンド
### 現在選択しているconfigファイルを見る。
```
kubectl --kubeconfig=ファイルのパス　config get-contexts
```
### リソースのファイルを検索
-Aですべてから検索。
```
kubectl --kubeconfig=ファイルのパス　get リソース名　-A
```
### 証明書(TLS)を無視して接続。
```
--insecue-skip-tls-verify=treu
```
### yaml形式で中身を表示する。
-n namespace指定。
```
get リソース名　-n namespace -o yaml
```
## 答え
```academy{ks3cr375_41n7_s4f3_c4134520}```
## ここから学んだこと
### コンテナとは
**コンテナ**とはアプリ本体とアプリの環境やバージョンなどをひとまとまりにしたパッケージ。
これのメリットはちがう端末でも動くということ。同じpyhtonでも入っているpythonのバージョンが異なることがある。
ちなみに仮想マシンとの違いはosを利用しているかしていないかの違いです。コンテナは移動先のosを利用することにより軽量化を図っています。
### Dockerとは
**Docker**とはコンテナを創ったり削除したりするものです。では実際にコンテナをどうやってほかのパソコンで共有するかというと
docker imageというものがあります。これはコンテナのレシピみたいなものです。コンテナを共有するのではなくイメージを共有することで各パソコンは
共有されたイメージからコンテナを作り出して実際にコンテナを利用します。
### kubernetesとは
kubernetesの役割はコンテナをまとめて管理することです。
イメージ的にはどっかーが集まったイメージです。
ではなぜ必要になるか。それは大規模サービスになった時にコンテナにアクセスが集中する。
結果的に上のサーバーが限界を迎えるのでサーバーとコンテナを増やしていく必要があります。
そうすると今度はコンテナの管理が大変です。そこでkubernetesです。
まずサーバーを増やしたりしないといけないのでサーバーの役目を果たしているNode、そしてコンテナがあります。
ですが実はログの解析などでネットワークを共有したりしたいときにコンテナの補助的なコンテナを一緒に置きたいときがあります。
そういう時にpodというコンテナの管理単位があります。podの特徴としてはデータを共有、ネットワークを共有したりなどです。
### namespaceとは
kubernetesの目次みたいなもんです。ここから探していきます。
## つぎに考えること
自分の知らない知識がいっぱい増えていくのでもっと頑張りたい。
tlsをなぜ飛ばせるのか。そうじゃないと証明書で認証の意味がない？＝＞ctfの特別仕様　or 暗号化されないだけ？
つまり本来は接続してる側の安全を保障してるだけであって今回はそのセーフティーバーを外したという意味ぽい。
証明書の検証をスキップ。
