---
title: "FrostyGoop"
date: 2024-08-03T18:18:51+07:00
draft: false
toc: false
images:
tags:
  - malware
  - operational technology
  - modbus
  - dragos
---

เมื่อช่วงปลายเดือน ก.ค. ทาง Dragos ได้ออก[รายงานเกี่ยวกับมัลแวร์ชื่อ FrostyGoop](https://hub.dragos.com/report/frostygoop-ics-malware-impacting-operational-technology) ที่คาดว่าถูกใช้ในการโจมตีบริษัทด้านพลังงานในเมือง Lviv ประเทศยูเครน

สรุปเนื้อหาในรายงานคร่าวๆ คือ FrostyGoop เป็นมัลแวร์ที่สามารถคุยกับอุปกรณ์ ICS/OT ด้วยโปรโตคอล Modbus TCP (port 502) และจากข้อมูลใน configuration file ของ FrostyGoop พบว่าอุปกรณ์ที่โดนโจมตีคือ ENCO control devices โดยผลกระทบจากการโจมตีทำให้ระบบทำความร้อนของอพาร์ตเมนต์กว่า 600 แห่งในเมือง Lviv หยุดทำงานเป็นเวลาเกือบ 48 ชั่วโมง 🥶

ในรายงานแนะนำให้แต่ละองค์กร implement [SANS Five ICS Cybersecurity Critical Controls](https://www.sans.org/white-papers/five-ics-cybersecurity-critical-controls/) ที่ประกอบด้วย

1. ICS-Specific Incident Response Plan
2. Defensible Architecture
3. ICS Network Visibility and Monitoring
4. Secure Remote Access
5. Risk-Based Vulnerability Management Program

รายงานนี้ทำให้เกิดการอภิปรายกันพอสมควร ตั้งแต่เรื่องความสมเหตุสมผลของข้อมูลในรายงาน ทั้งรูปแบบการโจมตี จำนวนผู้ได้รับผลกระทบ เวลาที่ใช้ในการแก้ไขให้กลับมาเป็นปกติ ฯลฯ ประเด็นที่ผมคิดว่าน่าสนใจและอยากจดไว้มีประมาณนี้

> The Dragos Report is another example of why we haven’t seen progress. What they have for remediation is not wrong, although unsurprisingly detection is emphasized, it’s incomplete. It’s missing the remediation that addresses the core problem: the ICS control protocol is unauthenticated.
>
> There’s a solution: [Modbus/TCP Security](https://modbus.org/docs/MB-TCP-Security-v21_2018-07-24.pdf). Where is the recommendation to upgrade to Modbus/TCP Secure or another secure control protocol?
>
>
> <cite>&ndash; Dale Peterson</cite>

[มุมมองของ Dale](https://dale-peterson.com/2024/07/23/frostygoop-2004-is-calling/) คือ การทำ SANS 5 ICS Critical Controls เป็นคำแนะนำที่ดี แต่ไม่ได้เป็นการแก้ปัญหาที่สาเหตุจริงๆ เพราะตาม Critical Controls จะเน้นให้ monitor traffic Modbus ที่ผิดปกติ ซึ่งเป็นคำแนะนำที่มีมาตั้งแต่ปี 2004 จะให้แก้ปัญหาให้ตรงจุด ก็ควรเปลี่ยนไปใช้โปรโตคอลที่มี authentication/built-in security แทน 😤

> The discovered sample is a generic modbus client capable of reading and writing analog outputs (basically 0-100% values). Full stop. It is not programmed to interact with the digital inputs/outputs (anything that is ON/OFF, etc.).
>
> <cite>&ndash; Marina Krotofil</cite>

[Marina บอกว่า](http://scadamag.infracritical.com/index.php/2024/08/02/follow-up-report-of-another-plc-compromised-using-cyber-means/)ตัวอย่างมัลแวร์จริงๆ แล้วก็คือ Modbus client ธรรมดา (ที่ทำงานตามสิ่งที่ระบุไว้ในไฟล์ JSON config) พออ่านแล้วก็ทำให้ "เอ๊ะ" เหมือนกัน ว่าเออแล้วเราจะแบ่งแยกระหว่างมัลแวร์กับ client ที่ตรงไหน

นอกจากนี้เธอยังวิเคราะห์เจาะลึกไปถึงเอกสารประกวดราคาของ LvivTeploEnergo ที่จัดซื้อ ENCO devices ว่าอุปกรณ์ดังกล่าวน่าจะเป็นแค่ sensor หรือ data logger ที่ไม่สามารถยุ่งกับ physical process ได้ ซึ่งก็ทำให้สงสัยต่อไปอีกว่า แล้วการโจมตีที่เกิดขึ้นจริงๆ มันเป็นยังไงกันแน่ อุปกรณ์ส่วนไหนโดนโจมตี เลยทำให้ระบบทำความร้อนหยุดทำงานไป 🤔

สรุปว่า FrostyGoop เป็นหัวข้อที่น่าสนใจติดตามเพิ่มเติม ว่าจริงๆ แล้วเกิดอะไรขึ้น และทำให้รู้ว่าการอ่าน report ด้านไซเบอร์ ต้องอ่านแบบมีสติ คิด วิเคราะห์ แยกแยะ และหาข้อมูลเพิ่มเติม จะเชื่อหมดเลยทันทีไม่ได้ 😔

### References
* [Intelligence Brief: Impact of FrostyGoop ICS Malware on Connected OT Systems](https://hub.dragos.com/report/frostygoop-ics-malware-impacting-operational-technology)
* [How Russia-Linked Malware Cut Heat to 600 Ukrainian Buildings in Deep Winter](https://www.wired.com/story/russia-ukraine-frostygoop-malware-heating-utility/)
* [Novel ICS Malware Sabotaged Water-Heating Services in Ukraine](https://www.darkreading.com/ics-ot-security/novel-ics-malware-sabotaged-water-heating-services-in-ukraine)
* [FrostyGoop: 2004 Is Calling](https://dale-peterson.com/2024/07/23/frostygoop-2004-is-calling/)
* [Follow-up: Report of another PLC compromised using cyber means](http://scadamag.infracritical.com/index.php/2024/08/02/follow-up-report-of-another-plc-compromised-using-cyber-means/)
