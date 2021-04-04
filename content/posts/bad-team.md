---
title: "BAD Team"
date: 2021-04-04T11:32:07+07:00
toc: false
images:
tags: [ "rant", "cybersecurity", "red team", "blue team" ]
---

ช่วงปลายเดือนที่แล้วได้ทำ PowerPoint เกี่ยวกับเรื่อง Proactive Cybersecurity ใช้ประกอบการเสวนาในที่ทำงาน พอทำไปทำมาก็ตัดส่วนที่เป็นทฤษฎีออกหมด เหลือแค่ส่วนที่เป็นการดำเนินงานจริงๆ ของหน่วยงาน แต่ไหนๆ ก็เสียเวลาทำ diagram แล้วเลยคิดว่าเอามาแปะไว้ในบล็อกก็ยังดี 😅

อันนี้เป็นเนื้อหาที่สรุปมาจาก [The Difference Between Red, Blue, and Purple Teams]((https://danielmiessler.com/study/red-blue-purple-teams/)) ของ Daniel Miessler ซึ่งเข้าใจว่าเค้าต่อยอดจากเรื่องที่ April Wright พูดในงาน Black Hat ปี 2017 ที่ชื่อ [Orange is the New Purple](https://www.blackhat.com/docs/us-17/wednesday/us-17-Wright-Orange-Is-The-New-Purple.pdf) มาอีกที

{{< figure src="/img/bad-team/original-triads.png" attr="Orange is the New Purple" >}}

ในสไลด์ของ April Wright จะแบ่งทีมที่เกี่ยวข้องกับ Cybersecurity ออกเป็น 3 ทีม โดยใช้ชื่อว่า Breakers, Guardians, และ Builders ซึ่งย่อแล้วน่าจะจำยาก Daniel Miessler เลยเอามาปรับเป็น Builder, Attacker, Defender แล้วย่อว่า BAD ซึ่งผมรู้สึกว่ามันติดหู จำง่าย และเท่กว่า 😆

{{< figure src="/img/bad-team/bad-team.png" attr="BAD Team" >}}

ใจความสำคัญของ diagram นี้ก็คือแนวคิดเรื่องการพัฒนาทีมด้าน Cybersecurity

* Builder = Yellow Team = ผู้จัดหา/ผู้พัฒนา/ผู้ดูแลระบบ
* Attacker = Red Team = ผู้ทดสอบการโจมตีระบบ
* Defender = Blue Team = ผู้ป้องกันระบบ

ปกติเราจะได้ยินคำว่า Purple Team ซึ่งเป็นการร่วมมือระหว่าง Red Team กับ Blue Team เพื่อตรวจสอบและปรับปรุง/แก้ไขช่องโหว่ด้าน Cybersecurity

แต่หน่วยงานส่วนใหญ่ในที่ทำงานผมจะเป็น Yellow Team มากกว่า คือมีหน้าที่ จัดหา/พัฒนา/บำรุงรักษา ระบบต่างๆ ดังนั้นผมเลยคิดว่าถ้าเราพยายามสร้างความร่วมมือระหว่าง Builder กับทีม Cybersecurity ทั้งสองด้าน (Attacker และ Defender) เพื่อให้เกิดเป็น Orange Team และ Green Team น่าจะดี ซึ่งแนวคิดของสีที่เกิดจากการผสมกันระหว่างทีมก็คือ

* Green: Builder learns from Defender
* Orange: Builder learns from Attacker
* Purple: Defender learns from Attacker

เป้าหมายสุดท้าย คือ ต้องการให้ระบบต่างๆ มีการคำนึงถึง Cybersecurity ตั้งแต่ขั้นตอนการออกแบบ ติดตั้ง ไปจนถึงการใช้งานและบำรุงรักษา

ทั้งนี้ทั้งนั้น Builder อาจไม่มีกำลังคนหรือทักษะด้านไซเบอร์ที่จำเป็น แต่ก็สามารถดึง Attacker และ Defender เข้ามาร่วมรับรู้และให้ความเห็นในแต่ละกระบวนการ เพื่อให้ได้ระบบที่น่าจะมั่นคงปลอดภัยกว่าการรอให้พัฒนา/ติดตั้งเสร็จแล้วค่อยมาทำ VA/Pentest อะไรประมาณนั้น 😛
