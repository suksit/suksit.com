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

ช่วงที่ผ่านมา มีโอกาสได้ร่วมทำ risk assessment ตาม พ.ร.บ. ไซเบอร์ สำหรับระบบ OT หลายๆ ระบบ โดยได้ทีมประเมินความเสี่ยงจากฝั่ง IT มาเป็นพี่เลี้ยง มีจุดตั้งต้นเป็นแบบฟอร์มการประเมินความเสี่ยงตาม ISO 27001&hellip; ทำไปทำมา ก็พบว่าความแตกต่างระหว่าง IT/OT ยังเป็นประเด็นที่ต้องคุยกันอีกเยอะ 🤔

อย่างแรกคือ แนวทางการทำ risk assessment ของ IT จะเป็นแบบ asset based คือลิสต์ asset ออกมาทุกสิ่งอย่าง เอามาจัดกลุ่ม แล้วประเมินความเสี่ยงของ asset แต่ละกลุ่ม ซึ่งในมุมของระบบ OT การทำแบบนี้จะทำให้ประเมินความเสี่ยงได้ลำบาก เพราะระบบ OT ส่วนใหญ่จะประกอบด้วยหลายๆ asset ที่ทำงานร่วมกันเป็นระบบใหญ่ การประเมินความเสี่ยงแยกแต่ละ asset จะทำให้ไม่เห็นภาพรวมความเสี่ยงที่แท้จริง (ยังไม่นับเรื่อง vulnerability ของ asset ที่ส่วนใหญ่ patch ไม่ได้ อาจจะทำให้เขวในการประเมินไปอีก) แนวทางที่ผมใช้คือทำเป็น scenario based แทน แล้วค่อยมาระบุ asset ทีหลัง เพื่อให้เข้ากับแบบฟอร์มที่ใช้

อย่างที่สองคือการประเมิน impact ของแต่ละ scenario&hellip; แน่นอนว่าในแบบฟอร์มที่ได้จาก IT จะให้ประเมิน impact 3 ด้านคือ CIA (confidentiality, integrity, availability) ตามแนวคิดของ information security แต่พอมันเป็นระบบ OT การประเมินด้วย CIA จะทำให้ไม่เห็นผลกระทบที่แท้จริง เพราะ primary concern ของระบบ OT ไม่ใช่เรื่อง information แต่เป็น physical process 🏗️

ดังนั้นในการประเมิน impact ของระบบ OT ผมเลยเพิ่ม SR (safety, reliability) เข้าไปใน impact ด้วย รวมเป็น CIASR ทีแรกเพิ่มเข้าไปเพราะรู้สึกว่าเป็นสิ่งที่ต้องเพิ่ม เพื่อให้ประเมิน impact ได้ใกล้เคียงความเป็นจริงเฉยๆ แต่พอโดน internal auditor ถามว่า มีมาตรฐานหรือ guidelines อะไรอ้างอิงไหม ก็อึ้งๆ ไปเหมือนกัน เพราะตอบไม่ได้ 😂

ลอง Google ดูก็พบว่ามีคนนิยาม security triad สำหรับระบบ OT/ICS คล้ายๆ กับที่ผมทำอยู่ โดยเปลี่ยนจาก CIA เป็น SRP (safety, reliability, productivity) เช่น [Verve Industrial](https://verveindustrial.com/resources/blog/the-ultimate-guide-to-understanding-ot-security/), [CISA](https://www.cisa.gov/uscert/sites/default/files/ICSJWG-Archive/QNL_JUN_21/Understanding%20ICS%20Cyber-Attacks%20and%20Defense%20Measures_S508C.pdf), [Schneider Electric](https://blog.se.com/industry/machine-and-process-management/2020/04/01/it-vs-ot-cybersecurity-why-process-industries-must-recognize-the-important-differences/) เลยคิดว่าตัวเองน่าจะมาถูกทางแล้ว ถึงจะไม่มีมาตรฐานหรือ guidelines แบบเป็นทางการก็ตาม 🙄

> เอาจริงๆ ตามเนื้อหาของ CISSP ปี 2021 security concepts จะเป็น CIANA+PS (confidentiality, integrity, availability, nonrepudiation, authenticity, privacy, safety)
>
> &hellip; อย่างน้อยทั้ง IT/OT ก็ยังเห็นตรงกันว่า safety เป็นสิ่งที่สำคัญ

อย่างที่สาม ผมเคยพูดตอนแนะนำตัว ในช่วงที่เรียน Official (ISC)² Training Seminar for CISSP ว่ามาสอบ CISSP เพื่อจะได้เข้าใจแนวคิดของทีม IT มากขึ้น ซึ่งก็พบว่าช่วยได้มากจริงๆ เพราะทำให้เข้าใจ และสามารถอธิบายได้ว่าทำไมแนวคิดหรือ best practice หลายๆ อย่างของระบบ IT ถึงไม่ควรเอามาใช้กับระบบ OT (เถียงได้แบบดูน่าเชื่อถือ เพราะมี World's Premier Cybersecurity Certification นะครัช) 555+

> สิ่งหนึ่งที่รู้สึกว่าเรียน CISSP มาแล้วไม่เสียเปล่าแน่ๆ คือเรื่องของ process ต่างๆ เช่น incident response, change management, ฯลฯ ซึ่งเอามาประยุกต์ใช้กับฝั่ง OT ได้ด้วย

อย่างที่สี่ เนื่องจากระบบ OT ส่วนใหญ่จะ sensitive ต่อการเปลี่ยนแปลง ดังนั้นเมื่อประเมินความเสี่ยงแล้วเจอประเด็นความเสี่ยงระดับสูงที่ต้องมีการแก้ไข อาจจะทำไม่ได้ตามกรอบเวลาที่กำหนดมาสำหรับระบบ IT (เช่น ภายใน 3-6 เดือน) เป็นสิ่งที่น่าจะต้องทำความเข้าใจร่วมกันกับทั้ง auditor และ regulator 🫤

และอย่างสุดท้าย&hellip; เพิ่งรู้สึกว่าการทำงานด้าน OT cybersecurity อยู่ในจุดที่น่าสนใจและท้าทายมาก เหมือนเป็นคนที่อยู่ตรงกลางระหว่างโลก cyber กับโลก physical เป็นคนที่ต้องเข้าใจคอนเซปต์เกี่ยวกับ information security ให้รอบด้านที่สุด เพื่อให้สื่อสารกับทีม IT ได้เข้าใจตรงกัน และในขณะเดียวกัน ก็ต้องเข้าใจการทำงานของระบบ OT คุณสมบัติเฉพาะ รวมทั้งข้อจำกัดต่างๆ ของแต่ละระบบ เพื่อให้สามารถสื่อสารกับเจ้าของระบบ รวมทั้งเพื่อให้สามารถวิเคราะห์และให้คำแนะนำด้าน cybersecurity ได้อย่างถูกต้อง 🙃
