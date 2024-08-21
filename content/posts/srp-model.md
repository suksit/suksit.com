---
title: "SRP Model"
date: 2024-08-21T22:26:18+07:00
draft: false
toc: false
images:
tags:
  - operational technology
  - security model
  - srp model
---

จริงๆ ผมเคยบ่นเรื่อง[การพยายามเอา CIA triad มา apply กับ OT security](/posts/rotating-cia-for-ot-security) ไว้แล้วหลายครั้ง... ล่าสุดคือตามบล็อกด้านบน ส่วนปีก่อนๆ นู้นก็เคยบ่น[เรื่องเดียวกันนี้ ในมุมของ พ.ร.บ. ไซเบอร์ กับระบบ OT](/posts/ot-vs-cybersecurity-act) (่ประเด็นที่ 2) ว่าถ้าจะประเมินความเสี่ยงให้เข้ากับบริบทของระบบ OT ควรพิจารณา impact ด้านอื่นที่ไม่ใช่ CIA (Confidentiality, Integrity, Availability) ซึ่งเท่าที่พอหาข้อมูลได้ก็คือการพิจารณาในมุม SRP (Safety, Reliability, Productivity) แทน

ประเด็นนี้เป็นสิ่งที่พูดถึงบ่อยๆ ในวงคนทำงานด้าน OT security แต่ก็เหมือนเป็นการบ่นกันเองในกลุ่มมากกว่าจะเป็นการพยายามสื่อสารให้คนกลุ่มอื่นๆ เกิดความเข้าใจ หรือเพื่อทำให้เกิดความเปลี่ยนแปลงด้าน mindset ของผู้เกี่ยวข้อง 🙄

จนเมื่อซัก 2 อาทิตย์ที่ผ่านมา ผมเพิ่งได้อ่าน blog เรื่อง [Introducing the SRP Model](http://srpmodel.infracritical.com/srpmodel.php) ที่เขียนไว้ตั้งแต่เดือน ต.ค. 2023 รู้สึกว่ามีความพยายามอธิบายแบบจริงจังดี เลยมาแปะไว้เป็น reference หน่อย

{{< figure src="/img/srp-model/srpmodel-6oct2023.png" attr="The SRP Model" >}}

คิดว่าเป็นหัวข้อที่ยังคงต้อง<del>ทะเลาะ</del>พูดคุยกันอีกนานระหว่างทีม IT/OT security 😆
