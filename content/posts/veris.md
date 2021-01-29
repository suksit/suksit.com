---
title: "VERIS"
date: 2021-01-29T20:12:22+07:00
toc: false
images:
tags: [ "cybersecurity", "cti", "veris", "incident", "classification", "taxonomy" ]
---

หลายวันก่อนได้ดูเซสชันนึงใน SANS Cyber Threat Intelligence Summit บรรยายโดย [David Thejl-Clayton](https://www.securitydistractions.com/) พูดเรื่องเกี่ยวกับการจัดเก็บรายละเอียด incident เพื่อให้สามารถตอบคำถามต่างๆ จากผู้บริหารได้ รวมทั้งเพื่อให้ทีมที่เกี่ยวข้องสามารถนำข้อมูลไปใช้ต่อได้สะดวก

![Graphic Recording](/img/veris/graphic-recording.jpg "Graphic Recording")

นอกเรื่องแป๊บ&hellip; สิ่งหนึ่งที่ผมชอบมากในงานนี้คือการที่มีคนมาวาดภาพสรุปเนื้อหาไปพร้อมๆ กับที่วิทยากรบรรยาย ([Graphic Recording](https://www.sans.org/blog/a-visual-summary-of-sans-cyber-threat-intelligence-summit/)) รู้สึกว่าคนที่ทำแบบนี้ได้ต้องมีสกิล lnw มาก 🤩

David เล่าว่าได้ research ข้อมูลแล้วก็พบว่า สิ่งที่เค้าค้นหาอยู่มันเรียกว่า Incidient Classification Taxonomy ซึ่งก็มีคนทำอยู่แล้วหลายเจ้า เช่น [CIRCL](https://www.circl.lu/pub/taxonomy/), [FIRST](https://www.first.org/resources/guides/csirt_case_classification.html), [Europol](https://www.europol.europa.eu/publications-documents/common-taxonomy-for-law-enforcement-and-csirts), หรือ [ENISA](https://www.enisa.europa.eu/publications/reference-incident-classification-taxonomy)

แต่พอลองใช้แล้วเค้าก็พบว่าเฟรมเวิร์กพวกนี้ออกแบบมาเพื่อใช้จัดหมวดหมู่ของ incident ก่อนการทำ investigation เป็นหลัก ถ้าต้องการใส่รายละเอียดที่ได้จากการทำ investigation เข้าไปด้วยก็จะทำได้ยากหรือไม่รองรับด้วยซ้ำ

จน David ได้ไปอ่าน [DBIR (Data Breach Investigations Report)](https://enterprise.verizon.com/resources/reports/dbir/) ของ Verizon และได้รู้จักเฟรมเวิร์กชื่อ VERIS ซึ่งเค้าให้นิยามว่าเป็น "Vocabulary for Event Recording and Incident Sharing" โดยรูปแบบการบันทึกข้อมูลจะอยู่บนหลักการของ 4A's

* Actor (who)
* Action (what)
* Asset (which)
* Attribute (how)

แต่ละหัวข้อก็จะมี field ให้ drilldown ลงไปเวลาจะบันทึกข้อมูล เช่น

`Action.Social.Variety = Phishing`  
`Action.Social.Vector = Email`  
`Action.Social.Target = HR`  
`Asset.Variety.Notes = WS01, Molly (User)`  
`Actor.External = True`

และเราสามารถ extend VERIS ด้วย "Plus" fields ได้ เช่น `Plus.Malware.Family = Qbot` หรือเอาไปโยงกับ MITRE ATT&CK เป็น `Plus.MITRE.TA0002 = Visual Basic` อะไรทำนองนี้

และด้วยความที่มันรองรับการบันทึก metric ได้หลากหลาย ทำให้เราสามารถเอาข้อมูลที่บันทึกไว้มาตอบคำถามต่างๆ ได้ดียิ่งขึ้น เช่น

> Where should we concentrate our user awareness training this year? (Governance team)

เราก็สามารถสร้าง chart มาโชว์ได้เลยว่า incident ทั้งหมดในปีนี้เกิดขึ้นกับ department ไหนมากที่สุด สมมติเป็น HR ก็อาจจะช่วยในการตัดสินใจได้ว่า ควรทำ awareness training สำหรับบุคลากรด้าน HR ให้เข้มข้นขึ้น หรือถ้าคำถามเป็น

> How many times have we seen Emotet malware in the last year? (CISO)

เราก็สามารถสร้าง chart เพื่อแสดงสถิติในภาพรวมของ malware แต่ละตระกูลออกมาได้โดยใช้ข้อมูลจาก field `Plus.Malware.Family` เป็นต้น

สรุปสั้นๆ ว่า VERIS เป็นเฟรมเวิร์กที่น่าสนใจ และผมคิดว่าน่าจะสามารถนำมาใช้เป็นมาตรฐานในการบันทึก incident ด้าน Cybersecurity ในส่วนที่รับผิดชอบอยู่ได้ 😙
