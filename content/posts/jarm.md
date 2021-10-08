---
title: "JARM"
date: 2021-10-08T17:20:16+07:00
images:
tags:
  - jarm
  - threat hunting
  - fingerprinting
  - cybersecurity
---

เมื่อคืนได้ฟัง session นึงใน [SANS Threat Hunting Summit and Training 2021](https://www.sans.org/cyber-security-training-events/threat-hunting-and-incident-response-summit-2021/) วิทยากรพูดเรื่อง "Mining the Shadows with ZoidbergStrike" เป็นเรื่องเกี่ยวกับการสแกนหา C2 Server บนอินเทอร์เน็ตโดยใช้เครื่องมือต่างๆ

ได้ยินเค้าพูดถึง JARM โดยบอกว่าเป็น TLS server fingerprinting tool ที่พัฒนาโดย Salesforce ฟังแล้วก็งงๆ เพราะไม่เคยได้ยินมาก่อน 🤨 เลยไปหาข้อมูลเพิ่มเติมมา

กูเกิลเจอ [บล็อกของ Salesforce](https://engineering.salesforce.com/easily-identify-malicious-servers-on-the-internet-with-jarm-e095edac525a) บอกว่า

> JARM is an active Transport Layer Security (TLS) server fingerprinting tool. Scanning with JARM provides the ability to identify and group malicious servers on the Internet.

เข้าไปอ่านแล้วก็พอสรุปความได้ว่า [JARM](https://github.com/salesforce/jarm) เป็นเครื่องมือที่จะส่ง TCP packet "client hello" ที่ทำขึ้นมาเป็นพิเศษ จำนวน 10 packet ไปยัง server ที่เป็นเป้าหมาย และจะเอาสิ่งที่ server ตอบกลับ มาสรุปทำเป็น fingerprint ขนาด 62 ตัวอักษร ซึ่งมันแบ่งเป็นสองส่วนอีกคือ 30|32 ตัวอักษร ครึ่งหน้าเป็นรายการ cipher และ TLS version ที่ server เลือกเวลาได้รับ "client hello" ส่วนครึ่งหลังเป็น SHA256 hash ของ "server hello" ที่ server ตอบกลับมา

ซึ่ง fingerprint ที่ได้ สามารถเอามาจัดกลุ่ม server ที่กระจายอยู่ทั่วโลกได้ เช่น fingerprint แบบนี้เป็นของ Google, Apple, หรือ Facebook โดยอาจระบุได้ถึง application infrastructure stack ที่ server นั้นๆ ใช้

ในทำนองเดียวกัน เราเลยสามารถเอา JARM มาใช้ระบุ server ที่มีแนวโน้มจะเป็น C2 server ได้ด้วย เพราะถ้าใช้ C2 Server ตระกูลเดียวกัน มันก็น่าจะมี application infrastructure คล้ายๆ กัน อะไรทำนองนี้

ตัวอย่าง fingerprint แบบต่างๆ ดูได้ในบล็อกของ Salesforce ตามลิงก์ข้างบน คิดว่าเป็นเครื่องมือที่น่าสนใจ อาจจะได้ใช้งานในอนาคต 😛

ปล. นั่งหาอยู่พักนึงว่า JARM ย่อมาจากอะไร สรุปว่าน่าจะเป็นตัวย่อจาก[ชื่อของทีมผู้พัฒนา](https://github.com/salesforce/jarm#jarm-team) 🙃
