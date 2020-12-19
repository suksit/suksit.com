---
title: "Changing Docker Bridge Network IP"
date: 2017-10-19T21:16:53+07:00
tags: [ "docker", "networking", "devops", "code" ]
---

ตอนนี้เริ่มใช้งาน Docker แบบจริงจัง โดยตั้งเซิร์ฟเวอร์ [Gogs](https://gogs.io/) สำหรับเก็บซอร์สโค้ดของทีมงาน แต่ปรากฏว่ามีบางหน่วยงานที่ไม่สามารถเรียกหน้าเว็บได้ ทีแรกนึกว่าเป็นที่ระบบเน็ตเวิร์ก แต่เช็คไปเช็คมาปรากฏว่าเป็นเพราะ Docker มันไปสร้าง bridge network interface เป็น IP วงเดียวกับที่ใช้ในอินทราเน็ตของที่ทำงาน 😑

จากที่ Google มาได้ความประมาณว่า default bridge network interface ของ Docker ในลินุกซ์ จะใช้ชื่อ `docker0` และจะเป็นวง private IP ที่เริ่มจาก 172.17.0.0 (เดาว่าน่าจะกำหนดให้อยู่ใน [private IPv4 address space](https://en.wikipedia.org/wiki/Private_network)) ซึ่งถ้ามีเครื่องจากภายนอกที่ใช้ IP วง 172.17.x.x พยายามติดต่อเข้ามา เซิร์ฟเวอร์จะงงและไม่ตอบกลับ

<!--more-->

วิธีแก้คือ เปลี่ยน config ของ Docker daemon ในไฟล์ `/etc/docker/daemon.json` (ถ้าไม่มีไฟล์นี้ให้สร้างใหม่ได้เลย) ถ้าอยากรู้ว่าสามารถตั้งค่าอะไรได้บ้าง ดูได้จาก [options ของ dockerd](https://docs.docker.com/engine/reference/commandline/dockerd/) ที่ผมทำคือเปลี่ยนแค่ค่าเดียว ถ้าเปิดไฟล์ `daemon.json` จะเห็นข้อมูลหน้าตาแบบนี้

```json
{
  "bip": "192.168.1.1/24"
}
```

เท่านี้ default bridge network ของ Docker ก็จะกลายเป็น IP ที่เราตั้ง&hellip; แต่ปัญหาต่อมาคือตัว bridge network interface ที่สร้างโดย Docker Compose แทนที่จะรันต่อจาก 192.168.1.0 มันดันไปเริ่มที่ 172.17.0.0 ใหม่อีก 🤣 ลอง Google อีกรอบก็พบว่า[มีคนประสบปัญหาเดียวกันอยู่ไม่น้อย](https://github.com/moby/moby/pull/29376)

ถ้าอ่านคอมเมนต์ใน pull request ข้างบนจะพบว่าตอนนี้มี workaround แค่อย่างเดียวคือต้อง hard code network ไว้ในไฟล์ `docker-compose.yml` ไปก่อน โดยใส่ข้อมูลประมาณนี้

```yaml
version: "3"

services:
  ... <service definitions>

volumes:
  ... <volume definitions>

networks:
  default:
    ipam:
      config:
        - subnet: 192.168.2.0/24
```

เท่านี้ bridge network interface ที่สร้างโดย Docker Compose ก็จะมี IP อยู่ในวงที่เราต้องการ 😁
