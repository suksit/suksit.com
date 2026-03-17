---
title: "Richter Scale for OT Cyber Incidents"
date: 2026-03-17T09:13:04+07:00
draft: false
toc: false
images:
tags:
  - ot security, oti impact score, s4x26
---

ในงาน S4x26 ที่ผ่านมา มีการนำเสนอแนวคิดในการระบุระดับผลกระทบของ OT cyber incident โดยใช้หลักการเดียวกับการระบุระดับความรุนแรงของแผ่นดินไหว (Richter Scale) เป็นสเกลตั้งแต่ 0.0-10.0

ไอเดียนี้เรียกว่า [Operational Technology Incident (OTI) Impact Score](https://impact.icsadvisoryproject.com/) มีเป้าหมายคือเพื่อระบุระดับความรุนแรงของ incident แบบคร่าวๆ และรวดเร็ว ภายในเวลา 12 ชั่วโมงหลังเกิดเหตุการณ์

กลุ่มเป้าหมายสำหรับข้อมูลชุดนี้คือ สื่อมวลชน และผู้บริหารระดับสูง เพื่อให้เห็นภาพรวมของระดับความรุนแรงของผลกระทบ และนำไปสื่อสารต่อประชาชน หรือตัดสินใจในการดำเนินการได้อย่างสมเหตุสมผล

การคำนวณ OTI Impact Score จะใช้มุมมองใน 3 มิติคือ Severity, Reach, และ Duration โดยใช้สูตร

<div style="text-align: center;">
(Severity x Reach x Duration) / 100
</div>

<dl>
  <dt>Severity</dt>
  <dd>การหยุดชะงักในการให้บริการลูกค้าหรือในด้านความปลอดภัย โดย 0 คือแทบไม่มีผลกระทบ ไปจนถึง 10 คือเกิดความเสียหายแบบพังพินาศหรือมีผู้เสียชีวิตจำนวนมาก</dd>
  <dt>Reach</dt>
  <dd>ความกว้างของผลกระทบ ทั้งในด้านภูมิศาสตร์และสังคม เช่น 1 คือกระทบเฉพาะภายในหน่วยงาน ไปจนถึง 10 ส่งผลกระทบในระดับโลกหรือกระทบต่อทุกคน</dd>
  <dt>Duration</dt>
  <dd>ระยะเวลาที่ใช้ในการฟื้นฟู เช่น 2 คือสามารถฟื้นฟูได้ภายใน 1 ชั่วโมง ไปจนถึง 10 ถ้าต้องใช้เวลามากกว่า 6 เดือน</dd>
</dl>

{{< figure src="/img/richter-scale-for-ot-cyber-incidents/oti-impact-thresholds.png" >}}

มีรายละเอียดเกณฑ์ที่ใช้พิจารณา และตัวอย่างการคำนวณ impact score ของ incident ที่ผ่านๆ มาอยู่ในหน้า portal ตามลิงก์ด้านบน เช่น

* 2015 Ukraine Power Grid Attack จะมี impact score อยู่ที่ 2.9
* Oldsmar Water Treatment Plant (2021) จะมี impact score อยู่ที่ 0.4

เป็นต้น

เวลาเอาไปใช้จริง จะใช้การโหวตจาก OT security practitioners อย่างน้อย 20 คน เพื่อป้องกัน bias ของบุคคล หรือของ sector โดย impact score สามารถปรับเปลี่ยนไปได้ตามเวลา หรือเมื่อมีข้อมูลเกี่ยวกับ incident นั้นๆ เพิ่มเติมทีหลัง

ทั้งนี้การระบุ impact ของหน่วยงาน critical infrastructure ไม่ควรอ้างอิง scale นี้เป็นหลัก แต่ควรพิจารณาร่วมกับ regulator หรือ sectoral ISAC/CERT และผู้ที่เกี่ยวข้อง ตามที่ดำเนินการกันเป็นปกติอยู่แล้ว