# BGPを繋ごう

2つのルーターをBGPで繋いでください

## 使い方

### インストール

```sh
git clone https://github.com/Dodai-Dodai/problem1.git
cd problem1
sudo clab dep -t problem1.yaml
```

### ルータへの入り方

```sh
docker exec -it clab-problem1-vyos01 su vyos #vyos01
docker exec -it clab-problem1-vyos02 su vyos #vyos02
```

### ルータの終了のさせ方

```sh
sudo clab destroy -t problem1.yaml
```

## 問題

![Alt text](IMG_3829-1.jpg)

## 終了条件

- それぞれのルータから反対側の```lo```にpingが飛ぶ
- 経路情報に```lo```のネットワークがある(こんな感じで)
```
vyos@vyos02:/$ sh ip route
Codes: K - kernel route, C - connected, S - static, R - RIP,
       O - OSPF, I - IS-IS, B - BGP, E - EIGRP, N - NHRP,
       T - Table, v - VNC, V - VNC-Direct, A - Babel, F - PBR,
       f - OpenFabric,
       > - selected route, * - FIB route, q - queued, r - rejected, b - backup
       t - trapped, o - offload failure

K>* 0.0.0.0/0 [0/0] via 172.20.20.1, eth0, 00:18:53
C>* 10.0.0.0/30 is directly connected, eth1, 00:13:20
B>* 10.1.1.0/24 [20/0] via 10.0.0.1, eth1, weight 1, 00:00:28
C>* 172.20.20.0/24 is directly connected, eth0, 00:18:53
C>* 192.168.0.0/24 is directly connected, lo, 00:13:20
```