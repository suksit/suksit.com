---
title: "Let’s Encrypt Wildcard Certificate"
date: 2018-03-14T13:35:46+07:00
tags: [ "letsencrypt", "wildcard", "certificate", "devops", "certbot" ]
---

วันนี้เพิ่งเห็นว่า [Let's Encrypt](https://letsencrypt.org/) เปิดให้ใช้งาน [Certificate แบบ Wildcard](https://community.letsencrypt.org/t/acme-v2-and-wildcard-certificate-support-is-live/55579) แล้ว เลยบ้าเห่อรีบเปลี่ยนอย่างไว (จริงๆ suksit.com ยังไม่มี subdomain จะเปลี่ยนทำไม 🤣)

{{< x user="letsencrypt" id="973607502188195840" >}}

การใช้ Wildcard Certificate มีเงื่อนไขนิดหน่อย คือต้องใช้ [Client ที่รองรับ ACME v2](https://letsencrypt.org/docs/client-options/#acme-v2-compatible-clients) และจะเปลี่ยนจากการ validate แบบเดิม ไปใช้ DNS-01 Challenge แทน อย่างผมใช้ [Certbot](https://certbot.eff.org/) คำสั่งที่ใช้ในการสร้าง Wildcard Certificate จะเป็นประมาณนี้

<!--more-->

```bash
certbot certonly --server https://acme-v02.api.letsencrypt.org/directory --manual --preferred-challenges dns -d suksit.com -d *.suksit.com
```

หลังจากยอมรับเงื่อนไขการใช้งานแล้ว Certbot จะให้เราสร้าง DNS TXT Record ชื่อ `_acme-challenge` แล้วใส่ Value เป็นค่าที่มันกำหนด พอสร้างแล้วก็รอสักพักให้ DNS อัพเดต สามารถเช็คว่า TXT Record ที่เราสร้างนั้นโอเคแล้วหรือยัง โดยใช้คำสั่ง

```bash
nslookup
> set type=txt
> _acme-challenge.suksit.com
```

ถ้าเห็น TXT Value ตามที่เราสร้างไว้ก็เป็นอันใช้ได้ จากนั้นก็กลับมาหน้า Certbot แล้วกด Enter เพื่อให้มันตรวจสอบ DNS Challenge และสร้าง Certificate ให้เรา เป็นอันเสร็จพิธี 😙
