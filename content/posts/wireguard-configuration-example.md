---
title: "Wireguard Configuration Example"
date: 2021-08-29T12:42:13+07:00
images:
tags: [ "wireguard" ]
---

ช่วงนี้ลองทำ VPN ด้วย [Wireguard](https://www.wireguard.com/) แทน OpenVPN แต่มีปัญหาตอน config เป็นประจำ อารมณ์เหมือนงงๆ จำไม่ได้ว่าต้องทำอะไรบ้าง เลยมาจดไว้หน่อย วันหลังจะได้ก๊อปแปะ 🙄

สมมติว่าวง network ที่เราต้องการใช้คือ 10.0.0.0/24 และ network interface ที่ต่อกับอินเทอร์เน็ตของเซิร์ฟเวอร์คือ `eth0`

### Server Wireguard Config

```
[Interface]
Address = 10.0.0.1/24
ListenPort = 51820
PrivateKey = <SERVER_PRIVATE_KEY>

# required UP rules
PostUp = iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o eth0 -j MASQUERADE
PostUp = iptables -A INPUT -i %i -j ACCEPT
# additional UP rules when using UFW
PostUp = iptables -A FORWARD -i eth0 -o %i -j ACCEPT
PostUp = iptables -A FORWARD -i %i -o eth0 -j ACCEPT
PostUp = iptables -A INPUT -i eth0 -p udp --dport 51820 -j ACCEPT

# required DOWN rules
PostDown = iptables -t nat -D POSTROUTING -s 10.0.0.0/24 -o eth0 -j MASQUERADE
PostDown = iptables -D INPUT -i %i -j ACCEPT
# additional DOWN rules when using UFW
PostDown = iptables -D FORWARD -i eth0 -o %i -j ACCEPT
PostDown = iptables -D FORWARD -i %i -o eth0 -j ACCEPT
PostDown = iptables -D INPUT -i eth0 -p udp --dport 51820 -j ACCEPT

[Peer]
PublicKey = <CLIENT_PUBLIC_KEY>
AllowedIPs = 10.0.0.8/32

[Peer]
PublicKey = <ANOTHER_CLIENT_PUBLIC_KEY>
AllowedIPs = 10.0.0.9/32
```

### Server `sysctl.conf`

```
net.ipv4.ip_forward = 1
```

### Client Wireguard Config

```
[Interface]
PrivateKey = <CLIENT_PRIVATE_KEY>
Address = 10.0.0.8/32
DNS = 8.8.8.8, 8.8.4.4

[Peer]
PublicKey = <SERVER_PUBLIC_KEY>
AllowedIPs = 0.0.0.0/0, ::/0
Endpoint = <SERVER_IP>:51820
```

ประมาณนี้ ถ้าไม่มีอะไรผิดพลาด ไคลเอนต์ควรจะ connect และ route traffic ผ่าน Wireguard ไปออกที่ขา Internet ของเซิร์ฟเวอร์ได้
