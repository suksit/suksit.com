---
title: "Using SDN May Help Improve ICS Security"
date: 2018-05-29T23:17:51+07:00
tags: ["cybersecurity", "network", "sdn", "ics", "cloud"]
---

พอดีช่วงนี้เริ่มอ่านข้อมูลเกี่ยวกับ OT/ICS Security มากขึ้น และมีเรื่องน่าสนใจหลายอย่าง เลยคิดว่าทำเป็นโน้ตไว้ให้หาง่ายๆ และคอยอัพเดตเรื่อยๆ น่าจะเข้าท่าดี 🤔

เรื่อง SDN (Software-Defined Network) อันนี้น่าสนใจเพราะด้วยแนวโน้มของเทคโนโลยี องค์กรส่วนใหญ่น่าจะมีแผนการย้ายระบบขึ้นคลาวด์กันแล้ว ซึ่งโดยปกติมันก็จะมาพร้อม SDN ด้วย

**Disclaimer:** ณ เวลาที่เขียนโน้ตนี้ ความรู้เกี่ยวกับ SDN ของผมมีน้อยมาก ดังนั้นข้อความข้างล่างคือการสรุปจาก [discussion](https://ics-community.sans.org/t/80zpwc/nerc-cip-and-ics-virtualization-vlans-versus-sdn) ตามความเข้าใจของผมเอง อาจจะมีผิดพลาดหรือมั่วบ้าง ต้องขออภัยไว้ล่วงหน้า 😆

<!--more-->

การใช้ SDN ในระบบเครือข่ายของ ICS น่าจะดีกว่าการแบ่ง VLAN ด้วยเหตุผลต่อไปนี้

SDN สามารถติดตั้งได้ในสภาพแวดล้อมของระบบ ICS ที่ใช้กันในปัจจุบัน

> SDN can be installed on an industrial network with little to no changes needed in the overall cabling topology and can work with most network topologies that are in use within industrial networks today.

การใช้ SDN จะช่วยเพิ่ม Visibility ของอุปกรณ์ทุกอย่างที่ต่ออยู่ในระบบเครือข่าย

> An industrial SDN can solve the visibility problem in a way we have not seen before. A device sending a single frame is known to the controller. Focusing efforts on uniquely identifying devices connected to the switches can help to significantly reduce the capabilities of a MiM attack.

นอกจากนี้เรายังสามารถมองได้ว่าการใช้ SDN มีผลเทียบเท่ากับการแยกเครือข่ายแบบ Physical เลยทีเดียว

> If a software defined networking Ethernet switch does not have any flow rules programmed into the switch, then there is no physical connectivity (deny by default) with devices attached to the same switch.

อย่างไรก็ตามการใช้ SDN อาจจะเป็นการเพิ่มช่องทางการโจมตีแบบใหม่ให้แก่ผู้สงค์ร้ายเช่นกัน โดยถ้าตัว Management Controller โดน Compromise ก็อาจจะพูดได้ว่า ลาก่อย…

> In the case of SDN the API management controller plane if not properly secured could potentially allow an attacker to control data forwarding tables, insert policies and perform a Denial of Service attack by exhausting resources.

แต่… เค้าก็บอกอีกว่า จริงๆ แล้วมันก็พอจะป้องกันได้ไม่ยากนัก แค่แยก traffic ของระบบ management ออกมา และเข้ารหัสด้วย ก็น่าจะโอเค 😗

> Most of these threats are easily mitigated by simply separating and encrypting data from management traffic using FIPS compliant algorithms

ระหว่างที่อ่านๆ ไปก็ได้คีย์เวิร์ดมาอีกหลายตัว จดไว้ก่อนเดี๋ยวจะกลับมาศึกษา

- [OpenFlow](https://en.wikipedia.org/wiki/OpenFlow)
- [SEL Switch](https://selinc.com/products/2740S/)
