---
title: "CISA's Secure by Demand Guidance"
date: 2025-01-23T21:28:47+07:00
draft: false
toc: true
images:
tags:
  - cisa
  - guidance
  - ot security
  - rant
  - secure by demand
---

## Introduction
เมื่อสัปดาห์ก่อน CISA และกลุ่มพันธมิตรจากหลายประเทศ ได้ออกเอกสารแนะนำสิ่งที่ควรคำนึงถึงเมื่อจัดหาผลิตภัณฑ์ดิจิทัลสำหรับระบบ OT (Operational Technology) ชื่อเอกสารเต็มๆ คือ [Secure by Demand: Priority Considerations for Operational Technology Owners and Operators when Selecting Digital Products](https://www.cisa.gov/sites/default/files/2025-01/joint-guide-secure-by-demand-priority-considerations-for-ot-owners-and-operators-508c_0.pdf) ความยาว 22 หน้า

{{<image src="/img/cisas-secure-by-demand-guidance/cover.png" alt="CISA's Secure by Demand Guidance" position="center" style="box-shadow: 0 5px 10px 0 rgba(0,0,0,0.2); margin-bottom: 1.5em;">}}

ประเด็นน่าสนใจที่เป็นเหตุผลในการจัดทำเอกสารฉบับนี้คือ CISA บอกว่าเวลา attacker จะโจมตีระบบ OT จะเน้นไปที่ตัวผลิตภัณฑ์มากกว่าเน้นที่องค์กร ตามที่ผมเข้าใจก็คือไม่ว่าจะเป็นองค์กรที่อยู่ใน sector ไหนก็มีโอกาสโดนโจมตีไม่ต่างกัน ถ้าใช้ผลิตภัณฑ์ระบบ OT แบบเดียวกัน

และเนื่องจากผลิตภัณฑ์ระบบ OT ส่วนใหญ่ ไม่ได้พัฒนาตามหลักการ Secure by Design จึงทำให้มีช่องโหว่หรือจุดอ่อนมากมาย ดังนั้นเจ้าของระบบ OT หรือผู้จัดหาระบบ/อุปกรณ์ จึงควรกำหนด requirements ด้าน security เข้าไปในกระบวนการจัดซื้อจัดจ้าง โดยแนะนำให้มี requirements 12 เรื่องหลักๆ ดังต่อไปนี้

### 1. Configuration Management
ผลิตภัณฑ์ต้องรองรับการควบคุมและบันทึกการแก้ไข config และ engineering logic และควรมีกระบวนการ backup และ deploy system configuration ที่ปลอดภัยและใช้งานง่าย

### 2. Logging in the Baseline Product
ผลิตภัณฑ์ต้องรองรับการจัดเก็บ log ของทุกกิจกรรม เช่น การเปลี่ยน configuration, security events, safety events โดยใช้ฟอร์แมต log ที่เป็นมาตรฐานเปิด เพื่อให้ทีม security มีข้อมูลในการทำ incident response ได้

### 3. Open Standards
ผลิตภัณฑ์ต้องใช้มาตรฐานเปิดในฟังก์ชันการทำงานและ services รวมไปถึงการ migrate configuration settings และ engineering logic เพื่อให้การเปลี่ยนหรือเพิ่มอุปกรณ์ในอนาคตทำได้ง่าย

### 4. Ownership
ผลิตภัณฑ์ต้องอนุญาตให้ผู้ซื้อหรือผู้ใช้งานทำการบำรุงรักษาหรือแก้ไขได้เอง โดยควรลดการพึ่งพา vendor ให้น้อยที่สุด ไม่ใช่ว่าเราซื้อมาใช้แต่ทำอะไรเองไม่ได้เลย ไม่มีแม้กระทั่งรหัสผ่านเข้าอุปกรณ์ ต้องรอ vendor มาทำให้ตลอด

### 5. Protection of Data
ผลิตภัณฑ์ต้องมีกระบวนการปกป้อง integrity และ confidentiality ของ data รวมไปถึง configuration settings และ engineering logic โดยมีการ protect ทั้ง data at rest และ data in transit

### 6. Secure by Default
ผลิตภัณฑ์ต้องมี security มาตั้งแต่แรก เช่น ไม่มี default password, กำหนด password complexity ได้, ใช้โปรโตคอลที่มีความปลอดภัยและ disable โปรโตคอลต่างๆ ที่ไม่ควรใช้แล้ว (เช่น SNMP v1/2, Telnet, ฯลฯ) และไม่เปิด interface ให้เข้าถึงจากภายนอกได้โดยไม่จำเป็น

### 7. Secure Communications
ผลิตภัณฑ์ต้องรองรับการเชื่อมต่อแบบ secure authenticated โดยใช้ digital certificates ควรเลือกผลิตภัณฑ์ที่มีกระบวนการ deploy และ renew digital certificates ที่ง่าย แบบที่ไม่ต้องเป็น security expert ก็ทำได้

### 8. Secure Controls
ผลิตภัณฑ์ต้องสามารถรับมือกับการส่ง message ประเภท emergency, safety, หรือ diagnostic commands จาก attacker ได้ รวมทั้งต้องทนการทำ active scanning ได้ ควรมีกระบวนการตรวจสอบ safety-critical controls ที่ผู้ใช้งานสามารถทดสอบได้เองเมื่่อต้องการความมั่นใจ

### 9. Strong Authentication
ผลิตภัณฑ์ต้องป้องกัน unauthorized access ได้ โดยใช้การควบคุมที่เหมาะสม เช่น role-based access control และ multifactor authentication ไม่ควรเลือกผลิตภัณฑ์ที่ใช้ shared password

### 10. Threat Modeling
ผลิตภัณฑ์ต้องมีรายละเอียด threat model ที่ครอบคลุมและครบถ้วน โดยคำนึงถึงการโจมตีที่อาจเกิดขึ้นกับผลิตภัณฑ์ และ security measures ที่ผู้พัฒนาออกแบบเพื่อป้องกัน threat นั้นๆ

### 11. Vulnerability Management
ผู้ผลิตต้องมีกระบวนการ vulnerability management ที่ชัดเจน เช่น ระยะเวลาของ support period ที่จะมีการอัปเดต patch ให้โดยไม่มีค่าใช้จ่าย ควรเลือกผลิตภัณฑ์ที่มี hardware และ software BOM (bill of materials) และมีระยะเวลาการแก้ไข vulnerability โดยผู้ผลิตอย่างทันท่วงที ผ่าน vulnerability disclosure program

### 12. Upgrade and Patch Tooling
ผลิตภัณฑ์มีคู่มือการติดตั้ง patch และการ upgrade ที่ชัดเจน สามารถ migrate ไปใช้ OS ที่ใหม่กว่าได้หาก OS เดิมกำลังจะหมดการ support ควรเลือกผลิตภัณฑ์ที่รองรับการทำ patch management ที่ควบคุมโดยผู้ซื้อ/ผู้ใช้งาน

## Summary
ถ้าเจ้าของระบบ OT และผู้จัดหาระบบ/อุปกรณ์ พร้อมใจกันกำหนดเงื่อนไขการจัดซื้อจัดจ้างที่คำนึงถึง cybersecurity แต่แรก ก็น่าจะเป็นการกระตุ้นให้มีการพัฒนาผลิตภัณฑ์ที่ Secure by Design มากขึ้น อย่างไรก็ตามควรดูกฎหมายที่เกี่ยวข้องด้วย อย่างถ้าเป็นหน่วยงานราชการของไทยคงกำหนดเงื่อนไขอะไรแบบนี้ในกระบวนการจัดซื้อจัดจ้างได้ยาก 🤣
