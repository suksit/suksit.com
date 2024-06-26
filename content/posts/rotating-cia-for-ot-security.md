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

หนึ่งในแนวคิดหลักเวลาพูดถึง cybersecurity principles ระหว่างระบบ IT (Information Technology) และระบบ OT (Operational Technology) ก็คือ

> IT จะให้ความสำคัญกับ CIA แต่ OT จะให้ความสำคัญกับ AIC + Safety

{{< figure src="/img/rotating-cia-for-ot-security/cia-aic.jpg" attr="Source: https://netaworldjournal.org/advancements-in-the-industry-operational-technology-cyber-threats-are-on-the-rise/" >}}

โดยส่วนตัวผมไม่ค่อยเห็นด้วยกับแนวคิดนี้ เพราะอาจทำให้เกิดความเข้าใจผิดได้ง่าย&hellip;

เรื่องของเรื่องคือ ตามความเข้าใจของผม context ของ CIA ในมุมของ IT และ AIC ในมุมของ OT มันแทบจะเป็นคนละเรื่องกัน 😑

## CIA ในมุมมองของ IT

แน่นอนว่าเน้นไปที่การรักษาคุณสมบัติของ data / information ตามที่เราเรียนกันมา

* **Confidentiality** = ความลับของ<ins>ข้อมูล</ins>
* **Integrity** = ความครบถ้วนถูกต้องของ<ins>ข้อมูล</ins>
* **Availability** = ความพร้อมใช้ของ<ins>ข้อมูล</ins>

## AIC + Safety ในมุมมองของ OT

แต่ถ้าเป็นในมุม OT เราจะเน้นที่ operation หรือ physical process เป็นหลัก (สมมติเปรียบเทียบกับระบบ OT ด้านพลังงาน)

* **Availability** = การคงอยู่ของ<ins>กระบวนการ</ins>ที่เป็น mission ของระบบ เช่น ยังสามารถผลิตและจ่ายกระแสไฟฟ้าให้ลูกค้าได้
* **Integrity** = ความครบถ้วนถูกต้องของ<ins>กระบวนการ</ins>ตาม mission ของระบบ เช่น ระบบผลิต จำหน่าย รวมถึงโครงข่ายไฟฟ้ามีความเสถียรและมั่นคง
* **Confidentiality** = อันนี้เหมือนของ IT คือเรื่องความลับของข้อมูล ซึ่งปกติข้อมูลที่วิ่งในระบบ OT เป็น operational data ที่อัปเดตตลอดเวลา ไว้ใช้งานแค่ชั่วระยะเวลาหนึ่งเท่านั้น ข้อมูลที่เป็นความลับจริงๆ มีน้อยมาก
* **Safety** = <ins>ความปลอดภัย</ins>ของ stakeholders และอุปกรณ์ที่เกี่ยวข้องตาม mission ของระบบ เช่น พนักงานที่ปฏิบัติงานกับระบบไฟฟ้า อุปกรณ์ในสถานีไฟฟ้า และลูกค้า

จะเห็นว่าปัจจัยที่เกี่ยวข้องกับ Availability และ Integrity ของระบบ OT มีมากกว่าแค่ data / information และการใช้คำเดียวกันกับนิยามของระบบ IT ทั้งที่ความหมายต่างกัน อาจจะทำให้คนฟังเข้าใจผิดได้ง่าย

## Suggestion

ดังนั้นการจัดทำนโยบาย / กรอบการดำเนินงานด้านไซเบอร์ของระบบ OT ควรคำนึงความแตกต่างในจุดนี้ด้วย ไม่งั้นอาจจะกลายเป็นมองแค่เรื่อง data / information เพียงอย่างเดียว เช่น พอบอกว่าระบบ OT นี้เป็น critical ปุ๊บ ก็จะมุ่งไปที่การทำ encryption ข้อมูลกันหมด อะไรทำนองนี้ 🤪

แต่ทั้งนี้ทั้งนั้น ด้วยความรู้เท่าที่มีตอนนี้ ผมอาจจะเข้าใจผิดไปเองก็ได้ 555+
