---
title: "Industrial Control Systems Security Checklist"
date: 2025-01-26T09:41:25+07:00
draft: false
toc: false
images:
tags:
  - ot security
  - guidance
---

เมื่อหลายวันก่อนมีคนแชร์ [Industrial Control Systems Security Checklist](https://www.sintef.no/contentassets/8fa5c7e3a81749b8952979000ee34c31/industrial-control-systems-security-checklist.pdf) ใน LinkedIn ลองอ่านแล้วรู้สึกว่าน่าจะมีประโยชน์ เลยขอจดไว้กันลืม

เอกสารนี้เขียนโดย SINTEF สำหรับให้ OT/ICS owner และ system integrator ไว้พิจารณาคร่าวๆ ว่าระบบที่ออกแบบติดตั้ง ควรมี non-functional requirements ด้าน cybersecurity อะไรบ้าง

{{<image src="/img/industrial-control-systems-security-checklist/cover.png" alt="SINTEF's Industrial Control Systems Security Checklist" position="center" style="box-shadow: 0 5px 10px 0 rgba(0,0,0,0.2); margin-bottom: 1.5em;">}}

เนื้อหาหลักจะเป็น checklist ในรูปแบบคำถาม จำนวน 40 ข้อ เอกสารทั้งหมดมี 12 หน้า อ่านง่ายมากๆ รายการใน checklist จะแบ่งออกเป็น 3 security levels โดยฟอร์แมตที่ว่านี้ได้รับแรงบันดาลใจมาจาก OWASP Application Security Verification Standard และ IEC 62443

🟥 **Level 1** เป็น security ระดับพื้นฐานที่ระบบ OT ทุกระบบควร Implement  
🟨 **Level 2** ควรพิจารณา implement เพื่อให้เหมาะสมกับ criticality ของระบบ และ threat ที่ต้องการรับมือ  
🟩 **Level 3** สำหรับ use case ที่ critical มากๆ หรือ threat ระดับ nation state  

ซึ่งใน checklist ก็จะจัดกลุ่มหัวข้อออกเป็นด้านต่างๆ และบอกว่าในด้านนั้นๆ ถ้าต้องการทำ security level 1-3 ควรมีเรื่องอะไรบ้าง โดยกลุ่มหัวข้อและจำนวน/ระดับ ของตัว checklist เป็นประมาณนี้

1. Overall Principles 🟥🟥🟥🟥🟨
2. Network 🟥🟥🟥🟥🟥🟥🟥🟥🟥🟥🟥🟨🟨🟨🟨🟩🟩🟩🟩🟩🟩
3. Authentication and Authorization of Users 🟥🟥🟨🟩
4. Monitoring and Auditing 🟨🟨🟨
5. Software 🟥🟥🟨
6. Hardware and Devices 🟥🟥🟨🟩

ความเห็นส่วนตัวคิดว่าเป็นเอกสารที่ดี สามารถใช้เป็นจุดเริ่มต้นในการพิจารณาการวางแผนด้าน cybersecurity ของระบบ OT/ICS ได้ เช่นอาจจะเริ่มจากดูว่า security level 1 ของ checklist แนะนำว่าเราควรมีอะไรบ้าง และนำมา map กับมาตรฐานด้าน cybersecuirty ที่องค์กรเลือกใช้ เพื่อดูว่าเค้าระบุว่าให้ทำยังไงกับเรื่องนั้นๆ เป็นต้น
