---
title: "Gartner's Magic Quadrant for CPS Protection Platforms"
date: 2025-03-09T13:59:53+07:00
draft: false
toc: false
images:
tags:
  - gartner
  - rant
  - ot security
  - magic quadrant
---

ได้อ่านบล็อกของ Dale Peterson เรื่อง [Gartner’s OT Visibility Magic Quadrant](https://dale-peterson.com/2025/03/04/gartners-ot-visibility-magic-quadrant/) คิดว่าน่าจะมีประโยชน์ในอนาคตเลยขอจดไว้หน่อย

เค้าพูดถึงเอกสาร [Magic Quadrant for CPS Protection Platforms](https://www.gartner.com/doc/reprints?id=1-2KAV7A6A&ct=250218&st=sb) ของ Gartner ที่เพิ่งออกเมื่อกลางเดือนกุมภาพันธ์ 2025 เป็นการวางตำแหน่งบริษัทที่มีผลิตภัณฑ์เกี่ยวกับ Cyber-Physical System Protection

ประเด็นแรกที่ Dale ยกขึ้นมาคือ ชื่อเอกสารมันไม่ค่อยสื่อถึงฟีเจอร์ของผลิตภัณฑ์พวกนี้เท่าไร เพราะวัตถุประสงค์หลักของระบบพวกนี้คือ

1. **Identify** (creating and maintaining an asset inventory for asset management, risk management, vulnerability management)
2. **Detect** (detecting cyber attacks) หรือถ้าจะขยายขอบเขตไปอีกหน่อยก็น่าจะช่วยในเรื่อง
3. **Respond** (could be assisting with incident response, threat hunting)

ซึ่งจะเห็นว่าแทบจะไม่เกี่ยวกับเรื่อง Protection ตามหัวข้อเอกสารเลย

อีกประเด็นคือ ไม่ต้องพยายามใช้คำว่า CPS ก็ได้ เพราะปัจจุบันคำที่เป็น common term ที่สุดน่าจะเป็นคำว่า OT (Operational Technology) 🤣

ผมเห็นด้วยกับ Dale ที่บอกว่ากลุ่ม Leader จริงๆ น่าจะมีแค่ 4 เจ้า คือ Claroty, Nozomi, Dragos, และ Armis ส่วน Microsoft เท่าที่ผมติดตามข่าวมาก็จะไม่ค่อยเห็นบทบาทในด้าน OT Security ซักเท่าไร

Dale ยังมองลึกลงไปอีกว่าในกลุ่ม Leader นี้ ไม่ควรเอา Dragos มาเทียบกับผลิตภัณฑ์อื่นๆ เพราะ Dragos จะเน้นขาย service แบบครบวงจร ในขณะที่อีก 3 เจ้าที่เหลือ จะเน้นในเรื่อง discovery & monitoring เป็นหลัก

> If having a world class team supporting your OT detection, threat intel, and incident response, then you select Dragos combo of product and services. If you want visibility to what is on your system (asset inventory) and what is going on in your system you choose between Nozomi/Claroty/Armis

คือถึงผลิตภัณฑ์ของทั้ง 4 เจ้าจะมีฟีเจอร์บางอย่างเหมือนๆ กัน แต่ถ้ามองในแง่ capability แล้ว Dragos จะทำได้ครอบคลุมกว่าอย่างเห็นได้ชัด (All will do all of these functions, but the differences in capabilities is stark.)

คหสต. ทั้งนี้องค์กรจะเลือกใช้ผลิตภัณฑ์/บริการแบบไหนก็ขึ้นอยู่กับกฎหมาย นโยบายผู้บริหาร งบประมาณ และความสามารถของทีม security ขององค์กรด้วย

ที่น่าสนใจคือผลิตภัณฑ์ที่ SI ในประเทศไทยหยิบมานำเสนอ จะอยู่ในกลุ่ม Niche Players เป็นส่วนใหญ่ เท่าที่เคยฟังและพอจะจำได้ก็จะมี Fortinet, TXOne, Tenable, OPSWAT อะไรพวกนี้ แต่ที่แปลกใจหน่อยๆ คือไม่มี Siemens อยู่ใน Magic Quadrant ด้วย 🤔
