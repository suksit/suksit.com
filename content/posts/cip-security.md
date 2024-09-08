---
title: "CIP Security"
date: 2024-09-08T08:22:46+07:00
draft: false
toc: false
images:
tags:
  - cip security
  - odva
  - standards
  - cybersecurity
  - ot security
---

ปกติเวลาพูดถึงคำว่า CIP ผมจะนึกถึงแต่คำว่า "Critical Infrastructure Protection" ของ NERC CIP แต่เมื่อ 2-3 อาทิตย์ก่อน เพิ่งรู้ว่ามันมีอีก CIP ที่เกี่ยวข้องกับเรื่อง cybersecurity เหมือนกัน นั่นคือ CIP Security

คำว่า CIP ในที่นี้ ย่อมาจาก "Common Industrial Protocols" โดย CIP Security เป็นมาตรฐานที่พัฒนาโดย [ODVA](https://www.odva.org/) เพื่อให้ CIP-connected devices สามารถป้องกันต้วเองจาก CIP communication ที่มาจากผู้ไม่ประสงค์ดีได้

เป้าหมายของ CIP Security คือเพื่อเพิ่มความแข็งแกร่งใน layer สุดท้ายตามแนวคิด defense-in-depth ของระบบ industrial control system โดยมองว่าถ้า attacker สามารถทะลุผ่านแนวป้องกันใน layer อื่นๆ มาได้หมดแล้ว ปราการด่านสุดท้ายก็คือตัวอุปกรณ์ (Device) นั่นเอง

{{< figure src="/img/cip-security/defense-in-depth.png" attr="Defense-in-Depth Model" >}}

โดยอุปกรณ์ที่รองรับ CIP Security จะมีความสามารถในการ
* ปฏิเสธ data ที่ถูกเปลี่ยนแปลงระหว่างทาง **(integrity)**
* ปฏิเสธ message จาก untrusted people หรือ untrusted devices **(authenticity)**
* ปฏิเสธ message ที่สั่งให้ทำสิ่งที่ไม่ได้รับอนุญาต **(authorization)**

CIP Security ถูกออกแบบอยู่บนสมมติฐานต่อไปนี้
* เครือข่ายที่เชื่อมต่อกับอุปกรณ์ ถือเป็น untrusted network
* ผู้ใช้และอุปกรณ์อื่นๆ ที่อยู่ในเครือข่าย จะเป็น untrusted people หรือ untrusted devices จนกว่าจะผ่านการ authentication
* การเข้าถึง device ทางเครือข่าย จะทำได้ก็ต่อเมื่อผ่านการ authentication แล้ว
* การเข้าถึง device ทางกายภาพ จะทำได้เฉพาะคนที่เป็น trusted individuals (ส่วนนี้อยู่นอกขอบเขตของตัวมาตรฐาน)

อ่านไปอ่านมา ก็รู้สึกว่าน่าจะเป็นแนวคิดเดียวกับ [Zero-Trust Architecture](https://www.nist.gov/publications/zero-trust-architecture) (ZTA) สินะ 🤔

พยายามหาตัว specifications มาอ่าน แต่คิดว่าคงต้องเป็น ODVA member ก่อน ถึงจะดาวน์โหลดได้ ตอนนี้เห็นแค่ layout คร่าวๆ ประมาณนี้

* Chapter 1: Introduction to CIP Security
* Chapter 2: CIP Security
* Chapter 3: EtherNet/IP Security
* Chapter 4: Commissioning and Configuration
* Chapter 5: Object Library
* Chapter 6: Certificate Management
* Chapter 7: EDS Files
* Chapter 8: Security Profiles

## References
* [CIP Security&trade;](https://www.odva.org/technology-standards/distinct-cip-services/cip-security/)
* [Overview of CIP Security&trade;](https://www.odva.org/wp-content/uploads/2020/05/PUB00319R1_CIP-Security-At-a-Glance.pdf)
* [CIP Security with Rockwell Automation Products](https://literature.rockwellautomation.com/idc/groups/literature/documents/at/secure-at001_-en-p.pdf)
