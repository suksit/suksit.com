---
title: "Rotating CIA for OT Security"
date: 2024-05-29T21:58:21+07:00
draft: false
toc: false
images:
tags:
  - rant
  - operational technology
  - information technology
  - cia triad
---

หนึ่งในแนวคิดหลักเวลาพูดถึง cybersecurity principles ระหว่าง IT/OT ก็คือ

> IT จะให้ความสำคัญกับ CIA แต่ OT จะให้ความสำคัญกับ AIC + Safety

{{< figure src="/img/rotating-cia-for-ot-security/cia-aic.jpg" attr="Source: https://netaworldjournal.org/advancements-in-the-industry-operational-technology-cyber-threats-are-on-the-rise/" >}}

โดยส่วนตัวผมไม่ค่อยเห็นด้วยกับแนวคิดนี้ เพราะทำให้เกิดความเข้าใจผิดได้ง่าย&hellip; (หรือผมอาจจะเข้าใจผิดไปเอง 🤣)

เพราะผมมองว่า context ของ CIA ในมุมของ IT และ AIC ในมุมของ OT มันเป็นคนละเรื่องกัน 😑

## CIA ในมุมมองของ IT

แน่นอนว่าเป็นเรื่องการรักษาคุณสมบัติของ data / information ตามที่เราเรียนกันมา

* **Confidentiality** = ความลับของ<ins>ข้อมูล</ins>
* **Integrity** = ความครบถ้วนถูกต้องของ<ins>ข้อมูล</ins>
* **Availability** = ความพร้อมใช้ของ<ins>ข้อมูล</ins>

## AIC + Safety ในมุมมองของ OT

ถ้าเป็นในมุม OT เราจะเน้นที่ operation หรือ physical process เป็นหลัก (สมมติเปรียบเทียบกับระบบ OT ด้านพลังงาน)

* **Availability** = การคงอยู่ของ<ins>กระบวนการ</ins>ที่เป็น mission ของระบบ เช่น ยังสามารถผลิตและจ่ายกระแสไฟฟ้าให้ลูกค้าได้
* **Integrity** = ความครบถ้วนถูกต้องของ<ins>กระบวนการ</ins>ตาม mission ของระบบ เช่น ระบบผลิต จำหน่าย รวมถึงโครงข่ายไฟฟ้ามีความเสถียรและมั่นคง
* **Confidentiality** = อันนี้เหมือนของ IT คือเรื่องความลับของข้อมูล
* **Safety** = <ins>ความปลอดภัย</ins>ของ stakeholders และอุปกรณ์ที่เกี่ยวข้องตาม mission ของระบบ เช่น พนักงานที่ปฏิบัติงานกับระบบไฟฟ้า อุปกรณ์ในสถานีไฟฟ้า และลูกค้า

จะเห็นว่าปัจจัยที่เกี่ยวข้องกับ Availability และ Integrity ของระบบ OT มีมากกว่าแค่ data / information การใช้คำที่เหมือนกับระบบ IT ทั้งที่ความหมายต่างกัน อาจจะทำให้คนฟังเข้าใจผิดได้ง่าย

ดังนั้นการจัดทำนโยบาย / กรอบการดำเนินงานด้านไซเบอร์ของระบบ OT ควรคำนึงความแตกต่างในจุดนี้ด้วย ไม่งั้นอาจจะกลายเป็นมองแค่เรื่อง data / information เพียงอย่างเดียว
