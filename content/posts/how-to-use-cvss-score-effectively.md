---
title: "How to Use CVSS Score Effectively"
date: 2025-01-18T09:08:20+07:00
draft: false
toc: false
images:
tags:
  - cybersecurity
  - cvss
  - risk assessment
---

เมื่อสองสามสัปดาห์ก่อน ได้อ่านบล็อกของคุณ Tom Alrich ที่ชี้ประเด็นว่าทำไมควรมีการปรับ requirements ในมาตรฐาน [CIP-007 R2](http://tomalrichblog.blogspot.com/2024/12/why-do-we-need-to-replace-nerc-cip-007.html) และ [CIP-010 R1](http://tomalrichblog.blogspot.com/2025/01/why-do-we-need-to-replace-nerc-cip-010.html) สรุปใจความสำคัญคือควรเปลี่ยน requirements ทั้งสองตัวให้เป็นแนว vulnerability risk management แทนที่จะเป็นการทำ patch management และ configuration management อย่างที่เป็นอยู่ในปัจจุบัน

แต่อันนั้นไม่ใช่ประเด็นที่จะกล่าวถึง 😝 สิ่งที่ผมได้จากการอ่านบล็อกทั้งสองด้านบน คือแนวทางการใช้งาน [CVSS Score](https://www.first.org/cvss/) ให้มีประสิทธิภาพ โดยเค้าแนะนำไว้พอสรุปได้ประมาณนี้

1. CVSS ไม่ได้สะท้อนความเสี่ยงที่แท้จริง เพราะ Risk = Impact &times; Likelihood แต่ CVSS assume ว่า likelihood = 100% และ impact = worst case ดังนั้นจึงไม่ควรใช้ CVSS เป็นเกณฑ์หลักหรือเกณฑ์แรกในการพิจารณาความเสี่ยงด้านไซเบอร์
2. วิธีที่ดีที่สุดในการดูว่า vulnerability นั้นๆ มีความเสี่ยงมากแค่ไหน ให้ดูที่สถานะการ exploit หรือความน่าจะเป็นที่จะถูก exploit โดยมีข้อมูลหลักอยู่ 2 แหล่ง คือ
    * vulnerability นั้นอยู่ใน [Known Exploited Vulnerabilities Catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) ของ CISA หรือเปล่า และ
    * ค่า [EPSS Score](https://www.first.org/epss/) ของ vulnerability หรือความน่าจะเป็นที่ vulnerability นั้นจะถูก exploit ใน 30 วันข้างหน้า
3. นอกจากนี้ยังมี criteria อื่นๆ ที่ควรนำมาพิจารณาร่วมด้วย ได้แก่
    * องค์ประกอบอื่นๆ ใน CVSS Score เช่น Temporal Score และ Environmental Score
    * ระดับความสำคัญของ asset
    * ระดับการ expose ของ asset เช่น เชื่อมต่อกับ internet หรืออยู่ใน DMZ หรืออยู่ด้านใน ESP

คิดว่าเป็นข้อแนะนำที่น่าจะเอาไปปรับใช้ในการประเมินความเสี่ยงด้านไซเบอร์ได้ทั้งระบบ IT และ OT 🤔
