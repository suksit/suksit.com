---
title: "How to Use Valid SSL Certificates in Local Network"
date: 2021-05-14T08:47:35+07:00
toc: false
images:
tags: [ "ssl", "certificate", "letsencrypt", "devops" ]
---

เคยพยายามหาวิธีอยู่นาน ว่าทำยังไงให้ใช้เว็บแบบ HTTPS ใน local network ได้โดยไม่ต้องใช้ self-signed certificate แต่จนแล้วจนรอดก็นึกไม่ออก จนกระทั่งวันก่อนได้อ่านเรื่อง [ตั้งใบรับรองให้เราท์เตอร์ MikroTik ในบ้านมี DNS และใบรับรองจาก Let's Encrypt](https://www.blognone.com/node/122609) ที่คุณ [lew](https://lewcpe.com/) เขียนไว้ใน Blognone

เลยถึงบางอ้อว่ามันทำแบบนี้ได้สินะ ถึงกับต้องรีบมาจดลงบล็อก 😆 สรุปแนวทางคร่าวๆ แบบไม่ลง detail ก็มีประมาณนี้

* ต้องมี domain name ที่เราสามารถจัดการ DNS เองได้
* สร้าง subdomain (A Record) ซักอัน สำหรับชี้ไปที่ IP เครื่องที่อยู่ใน local network
* ใช้เครื่องไหนก็ได้ สร้าง Let's Encrypt certificate สำหรับ subdomain ที่ว่า โดยใช้ท่า DNS-01
* เอา certificate ที่ได้มาลงบนเครื่องใน local network และ config HTTPS
* ลองเข้าเว็บใน local network โดยใช้ subdomain ที่ตั้งไว้

เท่านี้ก็เรียบร้อย 🎉
