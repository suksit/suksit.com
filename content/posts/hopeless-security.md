---
title: "Hopeless Security"
date: 2024-11-09T08:56:49+07:00
draft: false
toc: false
images:
tags:
  - cybersecurity
  - rant
---

เมื่อสองสัปดาห์ก่อนได้ไปอบรมหลักสูตร OT Security ภาคปฏิบัติของ สกมช. ได้คำใหม่จากวิทยากรมาคำนึง นั่นคือ "Hopeless Security" 🥹

อธิบาย context เพิ่มเติมว่าตอนนั้นกำลังเรียนเรื่อง built-in security controls ของอุปกรณ์ PLC (Programmable Logic Controller) ก็จะมีพวกการกำหนด password ของอุปกรณ์, การเข้ารหัสตอนทำ data transfer อะไรทำนองนี้

วิทยากรบอกว่า เวลาออกแบบ OT/ICS security เราไม่ควรหวังพึ่งฟีเจอร์ "Hopeless Security" พวกนี้เป็นหลัก เพราะอุปกรณ์ในระบบ OT/ICS ถึงตอนซื้อมาจะเป็นเทคโนโลยีล่าสุด แต่พอติดตั้งใช้งานไปแล้ว ด้วยธรรมชาติของ operational technology ที่จะไม่มีการเปลี่ยนอุปกรณ์บ่อยๆ สุดท้ายมันจะกลายเป็นของโบราณที่มี security technology ของเมื่อ 10-15 ปีที่แล้ว และอาจมีช่องโหว่ที่ไม่เคยได้รับแพตช์จาก vendor 🤣

ดังนั้นการ secure ระบบ OT/ICS จึงควรเน้นที่การสร้าง security controls ขึ้นมาครอบตัวระบบอีกที ซึ่งจริงๆ ก็เป็น concept เดียวกับ defense in depth หรือ [swiss chesse model](https://en.wikipedia.org/wiki/Swiss_cheese_model) 🧀 และก็น่าจะเป็นแนวคิดที่สอดคล้องกับเรื่อง [CIP Security](/posts/cip-security/) ด้วย

แต่ยังไงก็ตาม ถ้า attacker สามารถทะลุผ่านการป้องกันอื่นๆ เข้ามาได้หมด สุดท้ายเราอาจจะยังมี security controls ที่อยู่ในตัวอุปกรณ์คอยช่วยได้บ้าง ดังนั้นก็ควร enable ฟีเจอร์พวกนี้ไว้ แต่ไม่ควรเอาอุปกรณ์พวกนี้ไป expose ให้สามารถเข้าถึงจากภายนอก (intranet, internet, physical) ได้แบบง่ายๆ 💀
