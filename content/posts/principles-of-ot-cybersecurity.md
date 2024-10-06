---
title: "Principles of OT Cybersecurity"
date: 2024-10-06T09:40:09+07:00
draft: false
toc: true
images:
tags:
  - cybersecurity
  - operational technology
  - guideline
  - acsc
  - cisa
---

## Overview

เมื่อวันที่ 1 ต.ค. ทาง Australian Signals Directorate’s Australian Cyber Security Centre (ASD's ACSC) ได้เผยแพร่เอกสารแนะนำแนวทางด้าน Cybersecurity สำหรับระบบ Operational Technology (OT) ชื่อ "Principles of Operational Technology Cyber Security"

[{{< image src="/img/principles-of-ot-cybersecurity/cover.png" alt="Principles of OT Cybersecurity" position="center" style="box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px; width:600px;" >}}](https://www.cyber.gov.au/sites/default/files/2024-10/principles_of_operational_technology_cyber_security.pdf)

เอกสารนี้พัฒนาโดย ASD's ACSC ร่วมกับ U.S. Cybersecurity and Infrastructure Security Agency (CISA) และหน่วยงานด้าน cybersecurity ที่เป็น partner จากทั่วโลกอีก 10 กว่าหน่วยงาน

เนื้อหาโดยสรุปพูดถึงความจำเป็นและความสำคัญของการดูแล cybersecurity ของระบบ OT และอธิบายหลักการด้าน cybersecurity สำหรับระบบ OT โดยมีทั้งหมด 6 ข้อ ดังนี้

## Principle 1: Safety is Paramount

> In contrast to corporate IT systems, where leaders prioritize innovation and rapid development without concern of threat to life, operational cyber-physical systems’ leaders must account for threat to life in daily decision making.

สิ่งสำคัญที่ทำให้ระบบ OT ต่างจากระบบ IT คือเมื่อเกิดเหตุภัยคุกคามทางไซเบอร์ในระบบ OT อาจส่งผลกระทบโดยตรงต่อชีวิตมนุษย์ ความปลอดภัยของสิ่งแวดล้อม และการให้บริการที่สำคัญต่างๆ หลักการข้อนี้ต้องการเน้นว่าเวลาพิจารณาเรื่อง cybersecurity ต้องคำนึงถึงประเด็นด้าน safety ด้วย

ในการทำ incident response ต้องรวม safety protocols เข้าไปด้วย เช่น ถ้าโดน ransomware แล้วเราจะรู้ได้ยังไงว่าถ้าจ่ายค่าไถ่ และได้ key มา decrypt แล้ว ระบบ OT จะยังทำงานได้อย่าง ปกติ/ปลอดภัย เหมือนเดิม (ผู้โจมตีอาจเปลี่ยนค่าในไฟล์ config ก่อนรัน ransomware... เราจะตรวจสอบและยืนยันว่าเป็น config ที่ปลอดภัยได้ไหม)

## Principle 2: Knowledge of the Business is Crucial

> The more knowledge a business has about itself, the better that business can protect against, prepare for and respond to a cyber incident.

อันนี้ค่อนข้างตรงไปตรงมา คือในการจะป้องกันระบบใดๆ เราควรมีความรู้เกี่ยวกับระบบนั้นให้มากที่สุด ทั้งตัวอุปกรณ์ กระบวนการ การขึ้นต่อกัน และจุดอ่อนต่างๆ ของระบบ

ควรรู้ว่า asset ไหนเป็นสิ่งที่ขาดไม่ได้ในระบบ การเชื่อมต่อกับส่วนอื่นๆ และผลกระทบหาก asset นั้นไม่ทำงาน หรือทำงานผิดปกติ

เนื่องจากความรู้ในส่วนนี้ จะเป็นจุดตั้งต้นของกิจกรรมด้าน cybersecurity ทั้งหลาย ตั้งแต่การทำ risk assessment, การ implement security controls, การทำแผน incident response, และการทำแผน recovery เป็นต้น

## Principle 3: OT Data is Extremely Valuable and Needs to be Protected

> From an adversary’s point of view, knowing how a system is configured, including devices and protocols used, is valuable since an OT environment rarely changes.

ข้อมูลเกี่ยวกับ engineering configuration ของระบบ OT ถือเป็นข้อมูลสำคัญสำหรับผู้โจมตี เนื่องจากเป็นสิ่งที่ไม่ค่อยเปลี่ยนแปลง ทำให้ผู้โจมตีสามารถออกแบบการโจมตีที่เฉพาะเจาะจงกับระบบนั้นๆ ได้

เราควรป้องกันการรั่วไหลของข้อมูลในส่วนนี้โดยการทำ access control หรือ data loss prevention รวมทั้งทำ proactive monitoring ว่ามี unauthorized access เกิดขึ้นหรือเปล่า

## Principle 4: Segment and Segregate OT from All Other Networks

> Organisations cannot presume that other organisations have the same cyber risk appetite, cyber hygiene and cyber security standards as their own.

ระบบ OT ควรทำ network segmentation และ segregation โดยควรดูไปถึงการเชื่อมต่อกับ vendor และการเชื่อมต่อกับระบบอื่นๆ ทั้งภายในและภายนอกหน่วยงาน

อีกส่วนที่สำคัญคือ management network ที่ควรแยกออกมาต่างหาก และแยกจาก management network ของระบบ IT ด้วย เพื่อให้มั่นใจได้มากขึ้นว่าถึงระบบ IT จะโดน compromise ก็จะไม่ส่งผลกระทบต่อระบบ OT

## Principle 5: The Supply Chain Must be Secure

> A shift in thinking is required regarding criticality and risk exposure presented by vendors. Organisations should re-evaluate the scope of systems that require oversight, as historically often only large vendors or vendors that are the most significant from an engineering point of view were scrutinised.

การทำ supply chain security ในระบบ OT ควรพิจารณาทุกอุปกรณ์ที่เชื่อมต่อกับระบบ ไม่ใช่เน้นเฉพาะ vendor เจ้าใหญ่เท่านั้น

ปัจจัยที่ควรคำนึงถึงก็เช่น ที่มาของอุปกรณ์, โอกาสที่ firmware จะถูกเปลี่ยนแปลง รวมไปถึงกระบวนการทำงานของ vendor ที่อาจทำให้เกิดช่องโหว่ในระบบ OT ได้ (ขอให้ยกเว้นกระบวนการนี้, ขอเสียบอุปกรณ์นี้หน่อย, ขอต่อเน็ตแป๊บนึงเพื่อ activate license, ฯลฯ)

## Principle 6: People are Essential for OT Cyber Security

> A strong safety-based cyber security culture is critical to the on-going cyber resiliency of OT systems.

ควรสร้างวัฒนธรรมด้าน cybersecurity ที่ยั่งยืนในระบบ OT โดยเน้นที่ความร่วมมือระหว่างบุคลากร IT และ OT รวมถึงจัดการฝึกอบรมที่เหมาะสมให้กับ field technicians และส่งเสริมให้ทุกคนสามารถระบุและรายงานสิ่งที่คิดว่าอาจจะเป็นการโจมตีทางไซเบอร์

หลักการข้อนี้เน้นว่า human element เป็นองค์ประกอบสำคัญของ OT cybersecurity โดยควรมีกระบวนการสร้าง awareness, collaboration, และ proactive threat identification ของผู้เกี่ยวข้องกับระบบ OT ทั้งหมด

## Summary

ในความเห็นส่วนตัวของผม รู้สึกว่าเอกสารนี้เป็น guidelines ที่ดีมากๆ เล่มหนึ่ง เนื้อหาสั้น กระชับ ตรงประเด็น และเขียนโดยกลุ่มผู้เชี่ยวชาญที่เข้าใจด้าน operational technology cybersecurity จริงๆ... เหมาะกับทั้งทีม IT security และ OT security / OT engineer แนะนำให้อ่านฉบับเต็มอีกที (ทั้งหมดแค่ 14 หน้า) เพื่อความรู้และความเข้าใจที่ครบถ้วนครับ

ปล. blog นี้เขียนโดยใช้ [NotebookLM](https://notebooklm.google/) ช่วยสรุปให้ 🧠
