---
title: "IT/OT and Cybersecurity Act"
date: 2022-12-21T22:49:30+07:00
toc: false
images:
tags:
  - cybersecurity
  - operational technology
  - cissp
  - cybersecurity act
  - rant
  - risk assessment
---

ช่วงที่ผ่านมา มีโอกาสได้ร่วมทำ risk assessment ตาม พ.ร.บ. ไซเบอร์ สำหรับระบบ OT หลายๆ ระบบ โดยได้ทีมประเมินความเสี่ยงจากฝั่ง IT มาให้คำแนะนำ มีจุดตั้งต้นเป็นฟอร์มการประเมินความเสี่ยงตาม ISO 27001&hellip; ทำไปทำมา ก็พบว่าความแตกต่างระหว่างระบบ IT/OT ยังเป็นประเด็นที่ต้องคุยกันอีกเยอะ 🤔

### 1.

อย่างแรกคือ แนวทางการทำ risk assessment ของ IT จะเป็นแบบ asset based คือลิสต์ asset ออกมาทุกสิ่งอย่าง เอามาจัดกลุ่ม แล้วประเมินความเสี่ยงของ asset แต่ละกลุ่ม ซึ่งในมุมของระบบ OT การทำแบบนี้จะทำให้ประเมินความเสี่ยงได้ลำบาก เพราะระบบ OT ส่วนใหญ่จะประกอบด้วยหลายๆ asset ที่ทำงานร่วมกันเป็นระบบใหญ่ การประเมินความเสี่ยงแยกแต่ละ asset จะทำให้ไม่เห็นภาพรวมความเสี่ยงที่แท้จริง

> ยังไม่นับเรื่อง vulnerability ของ asset ที่ส่วนใหญ่ patch ไม่ได้ อาจจะทำให้เกิดความสับสน หลงประเด็นในการประเมินความเสี่ยงไปอีก

แนวทางที่ผมใช้คือทำเป็น scenario based แล้วค่อยมาระบุ asset ทีหลัง เพื่อให้เข้ากับแบบฟอร์มที่ใช้

### 2.

อย่างที่สองคือการประเมิน impact ของแต่ละ scenario&hellip; แน่นอนว่าในแบบฟอร์มที่ได้จาก IT จะให้ประเมิน impact 3 ด้านคือ CIA (confidentiality, integrity, availability) ตามแนวคิดของ information security แต่พอเป็นระบบ OT การประเมินด้วย CIA จะทำให้ไม่เห็นผลกระทบที่อาจเกิดขึ้นจริง เพราะ primary concern ของระบบ OT ไม่ใช่เรื่อง information แต่เป็น physical process 🏗️

ดังนั้นในการประเมิน impact ของระบบ OT ผมเลยเพิ่ม SR (safety, reliability) เข้าไปด้วย รวมเป็น CIASR&hellip; ทีแรกเพิ่มเข้าไปเพราะรู้สึกว่าเป็นสิ่งที่ต้องเพิ่ม เพื่อให้สามารถประเมิน impact ได้ใกล้เคียงความเป็นจริงเฉยๆ แต่พอโดน internal auditor ถามว่า มีมาตรฐานหรือ guidelines อะไรอ้างอิงไหม ก็อึ้งๆ ไปเหมือนกัน เพราะไม่มีคำตอบที่ชัดเจนกับเรื่องนี้ 😂

ลอง Google ดูก็พบว่ามีคนนิยาม security triad สำหรับระบบ OT/ICS คล้ายๆ กับที่ผมทำอยู่ โดยเปลี่ยนจาก CIA เป็น SRP (safety, reliability, productivity) เช่น [Verve Industrial](https://verveindustrial.com/resources/blog/the-ultimate-guide-to-understanding-ot-security/), [CISA](https://www.cisa.gov/uscert/sites/default/files/ICSJWG-Archive/QNL_JUN_21/Understanding%20ICS%20Cyber-Attacks%20and%20Defense%20Measures_S508C.pdf), [Schneider Electric](https://blog.se.com/industry/machine-and-process-management/2020/04/01/it-vs-ot-cybersecurity-why-process-industries-must-recognize-the-important-differences/) เลยคิดเข้าข้างตัวเองว่า น่าจะมาถูกทางแล้ว ถึงจะไม่มีมาตรฐานหรือ guidelines แบบเป็นทางการก็ตาม 🙄

> ตามเนื้อหาของ CISSP ปี 2021 security concepts จะมีมากกว่า CIA แล้ว โดยจะเป็น CIANA+PS (confidentiality, integrity, availability, nonrepudiation, authenticity, privacy, security)
>
> ตัว S (security) จริงๆ ก็จะเน้นไปที่ความปลอดภัยของชีวิตคน อย่างน้อยทั้ง IT/OT ก็ยังเห็นตรงกันว่า safety เป็นสิ่งที่สำคัญ

### 3.

อย่างที่สาม ผมเคยพูดตอนแนะนำตัว ในช่วงที่อบรม Official (ISC)² Training Seminar for CISSP ของ สกมช. ว่ามาลองสอบ CISSP เพื่อจะได้เข้าใจแนวคิดของคน IT มากขึ้น ซึ่งก็พบว่าช่วยได้มากจริงๆ เพราะทำให้เข้าใจ และสามารถอธิบายได้ว่าทำไมคำแนะนำหรือ best practice หลายๆ อย่างของระบบ IT ถึงไม่ควรเอามาใช้กับระบบ OT (คาดหวังว่าจะเถียงได้แบบดูน่าเชื่อถือ เพราะมี World's Premier Cybersecurity Certification นะครัช 555+)

> สิ่งหนึ่งที่รู้สึกว่าอ่าน CISSP มาแล้วไม่เสียเปล่าแน่ๆ คือเรื่องของ process ต่างๆ เช่น incident response, change management, user account provisioning ฯลฯ ซึ่งเอามาประยุกต์ใช้กับฝั่ง OT ได้ด้วย

### 4.

อย่างที่สี่ เนื่องจากระบบ OT ส่วนใหญ่จะ sensitive ต่อการเปลี่ยนแปลง ดังนั้นเมื่อประเมินความเสี่ยงแล้วเจอประเด็นความเสี่ยงระดับสูงที่ต้องมีการแก้ไข อาจจะทำไม่ได้ตามกรอบเวลาที่กำหนดมาสำหรับระบบ IT (เช่น ภายใน 3-6 เดือน) คือไม่ใช่ว่าตั้งใจจะทำช้า แต่ด้วยกระบวนการ change มันต้องทำแบบค่อยๆ เป็นค่อยๆ ไป&hellip; เป็นสิ่งที่น่าจะต้องทำความเข้าใจร่วมกันต่อไป ทั้งกับ auditor และ regulator 🫤

### 5.

และอย่างสุดท้าย&hellip; เพิ่งรู้สึกว่าการทำงานด้าน OT cybersecurity ทำให้ได้อยู่ในจุดที่น่าสนใจและน่าสนุกมาก เป็นคนที่อยู่ตรงกลางระหว่างโลก information และโลก cyber-physical ซึ่งต้องเข้าใจคอนเซปต์เกี่ยวกับ information security แบบรอบด้าน เพื่อให้สื่อสารกับทีม IT ได้เข้าใจ และในขณะเดียวกัน ก็ต้องเข้าใจการทำงานของระบบ OT รู้ถึงคุณสมบัติเฉพาะ รวมทั้งข้อจำกัดต่างๆ ของแต่ละระบบ เพื่อให้สามารถสื่อสารกับเจ้าของระบบ และสามารถวิเคราะห์/ให้คำแนะนำด้าน cybersecurity ได้อย่างถูกต้อง

แน่นอนว่าต่อจากนี้ก็จะมีอะไรให้ได้เรียนรู้อีกเยอะ 🙃
