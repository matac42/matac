---
title: "RTX1100のセグメント間の通信"
date: 2022-11-14T22:47:36+09:00
draft: false
tags: [infra, network]
categories: [tec]
---

LAN1, LAN2, LAN3があるが、これら同士の通信はなかなか難しそう。
方法はないこともなさそうだが、それぞれをNATで接続するとか。
あとでもう少し詳しく調べてみる。

とりあえず、FortiGateでどうにかする感じ。
今のところこのネットワークにアクセスする方法はRTX1100とかFortiGateとかの空いてるポートにさして設定するか、FortiGateのVPNでアクセスする。

![](figs/rtx1100_lan.png)

RTX1100でLANを束ねるのが難しそうだったので、FortiGateのポリシーでLANを束ねた。
まだFortiGateのポート余ってるしまあいいかな。
FortiGateの処理を挟む分、通信速度は落ちそうだけどどれくらい落ちるのか計測してみたい。もっとRTX1100をうまく使えるようになりたい。