---
title: "OT vs IIoT"
date: 2025-04-26T20:03:33+07:00
draft: false
toc: false
images:
tags:
  - rant
  - cybersecurity
  - operational technology
  - industrial internet of things
  - nist sp 800-82r3
---

ช่วงนี้ที่ทำงานเริ่มมีการนำพวก sensor แนวๆ IIoT (Industrial Internet of Things) ที่มาพร้อมกับ platform/dashboard มาติดตั้งใช้งานมากขึ้น โดยผมมีหน้าที่ศึกษา system architecture และให้ความเห็น/ข้อเสนอแนะด้านไซเบอร์ ร่วมกับทีม security ฝั่ง IT

สิ่งหนึ่งที่รู้สึกได้หลังจากดูมา 2-3 ระบบก็คือ การเอาระบบ IIoT พวกนี้มาวางในเน็ตเวิร์ก หรือเชื่อมต่อกับระบบ OT ที่มีอยู่เดิม มันทำได้ค่อนข้างยาก เพราะผมไม่แน่ใจว่าอุปกรณ์แต่ละตัวมันควรจะอยู่ใน level ไหนตาม Purdue Model

จนครั้งล่าสุดพอจะเริ่มจับทางได้ว่า อ้อ... เพราะตัว server/platform ของระบบ IIoT พวกนี้ มันทำหน้าที่เป็นทั้งระบบ OT และ IT ในตัวเดียวกัน 🤔

> พอจะเอาระบบไปวางในเครือข่าย OT ก็จะเห็นความเสี่ยงว่ามีการ access ข้ามหลาย level ตาม Purdue Model แต่พอคิดว่าจะเอาไปวางในเครือข่าย IT ทั้งหมดเลย ก็จะเห็นความเสี่ยงอีกว่ามันมีการสั่ง control หรือแก้ไข config ของ physical device ด้วย

เป็นประเด็นที่ติดอยู่ในหัวมา 2-3 สัปดาห์ จนกระทั่งได้มาอ่าน [NIST SP 800-82r3](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-82r3.pdf) (เป็นสิ่งที่ควรอ่านนานแล้ว แต่ดองไว้ประมาณ 2 ปี 🤣) เลยเพิ่งเข้าใจว่า เออเราไม่ได้คิดไปเองแฮะ แต่เป็นเพราะธรรมชาติของระบบ OT กับ IIoT มันต่างกันจริงๆ

NIST SP 800-82r3 ระบุว่าระบบ OT ทั่วไป เช่น DCS (Distributed Control System) จะมีโครงสร้างที่สอดคล้องตามแนวคิดของ Purdue Model ที่แบ่งเป็น level ได้ประมาณนี้

<div align="center">

![DCS System Architecture Example](/img/ot-vs-iiot/NIST.SP.800-82r3_P85.png)

</div>

แต่ถ้าเป็นระบบ IIoT ตาม NIST SP 800-82r3 บอกว่า Industry IoT Consortium แนะนำให้โมเดลเป็น three-tier system architecture โดยมีโครงสร้างประมาณนี้

<div align="center">

![IIoT System Architecture Example](/img/ot-vs-iiot/NIST.SP.800-82r3_P27.png)

</div>

ซึ่งก็เป็นอย่างที่ผมตะหงิดๆ ว่า tier กลางหรือ Platform Tier มันเป็นลูกผสมระหว่าง OT และ IT ทำให้งงๆ และไม่แน่ใจว่าควรแบ่งแยกเครือข่ายของระบบ IIoT พวกนี้แบบไหนดี

แต่ถ้าอ่านไปเรื่อยๆ ก็จะพบว่า NIST SP 800-82r3 ได้แนะนำแนวทางการเชื่อมต่อระบบ OT กับ IIoT ไว้ด้วย โดยแนะนำให้แยกเครือข่ายสำหรับ IIoT ออกจากระบบ OT แล้วให้เชื่อมต่อกับ border firewall ที่ป้องกัน DMZ ของระบบ OT อาจจะเพื่อส่งข้อมูลเข้าระบบ OT หรือส่งข้อมูลออกไปยัง enterprise network ก็ได้

<div align="center">

![DCS System with IIoT Devices System Architecture Example](/img/ot-vs-iiot/NIST.SP.800-82r3_P87.png)

</div>

สำหรับผมคิดว่าแนวทางการเชื่อมต่อระบบ IIoT เข้ากับเครือข่ายขององค์กร น่าจะมีตัวเลือกอย่างน้อย 3 แนวทาง

1. แยกเครือข่ายสำหรับ IIoT ทั้ง 3 tier ออกมา โดยไม่ไปเกาะกับทั้งระบบ OT และ IT แล้วคุยกันผ่านทาง DMZ ของแต่ละระบบ
2. ใช้แนวทางตามที่ NIST SP 800-82r3 แนะนำด้านบน
3. แยก platform tier ของระบบ IIoT ออกเป็นฝั่ง OT และ IT แล้วติดตั้งในเครือข่าย OT และ IT ตามฟังก์ชันที่ควรจะเป็น

ถ้ามีความรู้มากกว่านี้อาจจะมีไอเดียเพิ่ม ไว้กลับมาอัปเดตอีกที 🧠
