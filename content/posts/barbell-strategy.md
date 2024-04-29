---
title: "Barbell Strategy"
date: 2024-04-29T00:08:20+07:00
draft: false
toc: false
images:
tags:
  - operational technology, cybersecurity, barbell strategy
---

ได้อ่านบล็อก [A Barbell Strategy For OT Security](https://dale-peterson.com/2024/04/09/a-barbell-strategy-for-ot-security/) ของ Dale Peterson พบว่าเป็นแนวคิดที่น่าสนใจมาก

[Barbell Strategy](https://en.wikipedia.org/wiki/Barbell_strategy) เป็นกลยุทธ์ที่ใช้มานานแล้วในวงการการเงิน และเป็นที่รู้จักมากขึ้นเมื่อ Nassim Nicholas Taleb เอามาใช้ในหนังสือ [Antifragile](https://en.wikipedia.org/wiki/Antifragile_(book)) โดยเค้ามองว่าเป็นกลยุทธ์ที่สามารถปรับใช้ได้กับทุกโดเมน

> A dual strategy, a combination of two extremes, one safe and one speculative, deemed more robust than a "monomodal" strategy; often a necessary condition for antifragility.

และ Dale ก็มองว่าสามารถเอา Barbell Strategy มาปรับใช้กับ OT security ได้เช่นกัน แนวคิดของเค้าเป็นประมาณนี้

{{< figure src="/img/barbell-strategy/barbell-strategy.png" attr="Barbell Strategy for OT Security" >}}

## Left Side &ndash; Basic Attacks

ฝั่งซ้ายของ barbell จะเป็นเรื่องการโจมตีทั่วๆ ไป (reconnaissance, a spray and pray attempt, or even an unauthorized, but non-malicious communication attempt) ที่สามารถป้องกันได้โดยใช้ simple security controls คิดเป็น 99.999% ของการโจมตีทั้งหมดต่อระบบ OT

การป้องกันการโจมตีพวกนี้ ทำได้โดยใช้ best practices ของระบบ OT ง่ายๆ ตามที่ Dale แนะนำมีอยู่ 4 เรื่องหลักๆ คือ

* ไม่เชื่อมต่ออินเทอร์เน็ตโดยตรง
* ทำ OT security perimeter
* ควบคุมการใช้ USB drive
* และใช้ MFA ถ้าต้องมีการ remote access

## Right Side &ndash; APT or Nation-State Attacks

ฝั่งขวาของ Barbell จะเป็นอีกสุดขั้วนึงของการโจมตี คือเป็น targeted attack ที่ผู้โจมตีมีสกิลสูง มี resource ไม่จำกัด ซึ่งถ้าคิดเป็น % จำนวนการโจมตีแล้วจะน้อยมาก และแทบจะป้องกันไม่ได้เลย ไม่ว่าจะลงทุนกับ security controls มากแค่ไหน

สำหรับฝั่งขวาเราจะเน้นไปที่การ recovery แทน ซึ่งความหมายของ recovery ในมุม OT security ไม่ใช่การกู้คืนระบบคอมพิวเตอร์ แต่เป็นการทำให้กระบวนการผลิตหรือการให้บริการประชาชน/ลูกค้า สามารถดำเนินต่อไปได้

นอกจากเรื่อง recovery แล้ว การป้องกันเหตุการณ์ที่จะเกิดผลกระทบสูง (preventing other high consequence events) ก็จะอยู่ในฝั่งขวาเช่นกัน ซึ่งเราจะมองในแง่ความเสียหายของอุปกรณ์ ความปลอดภัยของผู้คน ผลกระทบต่อสิ่งแวดล้อม อะไรทำนองนี้

แนวทางการป้องกัน high consequence events ของระบบ OT ส่วนใหญ่จะใช้หลักการทางวิศวกรรม ที่เราสามารถบอกได้ด้วยความมั่นใจว่าการทำแบบนี้ ช่วยป้องกันการโจมตี/ผลกระทบในกรณีไหนได้บ้าง โดยไม่ขึ้นอยู่กับสกิลของ threat actor เช่น

* การใช้ unhackable protection measures (ระบบ protection ที่ไม่เชื่อมต่อกับเครือข่ายใดๆ หรือ analog protection)
* หลักการตามข้อข้างบน น่าจะเป็นเรื่องเดียวกับ [Consequence-Driven Cyber-Informed Engineering (CCE)](https://inl.gov/national-security/cce/) คือการออกแบบระบบเพื่อป้องกันการโจมตีทางไซเบอร์โดยใช้หลักการทางวิศวกรรม

## The Middle

ตามแนวคิด Barbell Strategy เราจะไม่สนใจเคสการโจมตีที่อยู่ตรงกลาง จนกว่าเราจะมั่นใจว่าเราสามารถดูแลทั้งสองฝั่งของ barbell ได้ดี เพราะการเพิ่ม security controls เข้าไปในส่วนนี้ จะช่วยอะไรเพิ่มไม่ได้มาก และอาจไม่คุ้มค่าในการลงทุน

## Summary

ทั้งนี้ทั้งนั้น แนวคิดแบบนี้จะดูขัดกับ มาตรฐาน/ข้อกำหนด/กฎหมาย ด้านความมั่นคงปลอดภัยไซเบอร์ส่วนใหญ่ และเราก็ยังคงต้อง implement security controls เพิ่มเติมเพื่อให้ comply กับมาตรฐานหรือสิ่งที่กฎหมายกำหนดอยู่ดี ซึ่ง Dale แนะนำว่าให้ลองเปรียบเทียบความเสี่ยงที่สามารถลดได้จากการใช้ Barbell Strategy เทียบกับความเสี่ยงที่ลดได้จาก controls ที่มาตรฐาน/กฎหมาย กำหนดให้ทำ
