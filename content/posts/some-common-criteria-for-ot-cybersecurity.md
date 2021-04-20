---
title: "Some Common Criteria for OT Cybersecurity"
date: 2021-04-20T17:53:54+07:00
toc: false
images:
tags: [ "rant", "cybersecurity", "recommendations", "red team" ]
---

วันก่อนมีคนมาโพสต์เรื่อง [Hacking Operational Technology for Defense: Lessons Learned From OT Red Teaming Smart Meter Control Infrastructure](https://www.fireeye.com/blog/threat-research/2021/04/hacking-operational-technology-for-defense-lessons-learned.html) ไว้ใน SANS ICS Community อ่านแล้วรู้สึกมีประโยชน์มาก เลยขอจดไว้หน่อย

ใน research เค้าพูดถึง lessons learned ที่ได้จากการที่ทีม Mandiant ไปทำ red teaming กับระบบ Smart Meter Control Infrastucture (น่าจะความหมายเดียวกับระบบ AMI – Advanced Metering Infrastructure ในบ้านเรา)

แนวคิดหลักๆ ก็คือเค้าเข้าถึงระบบ OT ได้โดยการ compromise เครื่องที่อยู่ในวง IT ก่อน แล้วก็ใช้ช่องทางที่มันเชื่อมต่อถึงกันในการเจาะเข้าไปในระบบ OT ได้ โดยใช้ tools ที่มีให้ใช้ทั่วไป เช่น ldapsearch, PowerSploit, WMImplant, และ Mimikatz

สิ่งสำคัญคือการทำ internal recon ภายในเครือข่ายองค์กร ที่ทำให้เจอข้อมูลต่างๆ เกี่ยวกับระบบ OT ที่เค้าต้องการเจาะ เช่นพวกคู่มือการใช้งานที่ระบุ default credentials ต่างๆ รวมกับการทำ lateral movement ไปหาเครื่อง target ที่คิดว่าเป็นของคนที่ทำงานเกี่ยวข้องกับระบบ OT แล้วทำ keylogging หรือ screen monitoring, ฯลฯ

สิ่งที่ผมชอบมากในรายงานคือตารางนี้

{{< figure src="/img/some-common-criteria-for-ot-cybersecurity/it-ot-attack-vectors.jpg" attr="Most likely attack vectors for IT/OT propagation" >}}

สรุปง่ายๆ คือเป็นช่องทางที่เราใช้ในการปฏิบัติงานกับระบบ OT ตามปกตินี่แหละ 🙄 ซึ่งเป็นสิ่งที่ผมพยายามอยากให้ทีม admin เข้าใจ ว่ามันเสี่ยงจริงๆ นะ ไม่ใช่ว่า paranoid เกินเหตุ แต่ก็ดูเหมือนจะยังไม่ได้ผลเท่าที่ควร 😣

อ่านไปอ่านมาก็ทำให้นึกถึง [2020 ICS Cybersecurity Year in Review](https://www.dragos.com/blog/industry-news/2020-ics-cybersecurity-year-in-review/) ของ Dragos ที่ข้อ 4 กับ 5 สอดคล้องกับ lessons learned ของ Mandiant อยู่มาก

{{< figure src="/img/some-common-criteria-for-ot-cybersecurity/dragos-2020-ics-cybersecurity-yir-executive-summary.png" attr="Dragos ICS Cybersecurity Year in Review 2020 Executive Summary - Page 7" >}}

ข้อ 4 แนะนำว่า เราควรตรวจสอบให้แน่ใจว่าที่ "เค้าบอกว่า" ระบบเครือข่ายของ IT กับ OT แยกกันนั้น มันจริงหรือเปล่า เพราะอาจจะมีการเชื่อมต่อถึงกันไม่ทางใดก็ทางหนึ่ง โดยที่เราอาจจะตั้งใจหรือไม่ตั้งใจก็ได้ 😅

ส่วนข้อ 5 แนะนำว่าให้แยกระบบ authentication หรือ credential management ของ IT และ OT ออกจากกัน เพื่อที่ว่าถึง Active Directory ของ IT ถูก compromise คนโจมตีก็จะยังไม่สามารถเข้าถึงระบบ OT โดยใช้ credentials ที่ได้มาจากระบบ IT โดยตรง

กลับมาที่ research ในตอนแรก สรุปว่าทีม Mandiant ก็สามารถเจาะเข้าระบบ OT และปิดการทำงานของ Smart Meter ได้สำเร็จ... เป็นรายงานที่อ่านสนุกและได้ความรู้ดี แนะนำให้อ่านครับ 🙂
