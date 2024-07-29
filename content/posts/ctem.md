---
title: "CTEM"
date: 2024-07-29T15:41:05+07:00
draft: false
toc: true
images:
tags:
  - ctem
  - gartner
  - framework
---

## Overview
เมื่อวันพฤหัสฯ ที่ผ่านมา ได้ไปร่วมงาน OT-ISAC Roundtable Bangkok โดยทางทีม OT-ISAC จากสิงคโปร์ ร่วมกับ สกมช. มาพูดเรื่อง [Continuous Threat Exposure Management (CTEM)](https://www.gartner.com/en/articles/how-to-manage-cybersecurity-threats-not-episodes)

CTEM เป็นคอนเซปต์/เฟรมเวิร์กที่พัฒนาโดย Gartner โดยมีเป้าหมายเพื่อช่วยให้องค์กรสามารถค้นพบและจัดลำดับความสำคัญของความเสี่ยงด้านไซเบอร์ที่ต้องจัดการ  ประกอบด้วย 5 ขั้นตอน ที่ทำวนเป็นรอบๆ วนไปเรื่อยๆ ตามนี้

{{< figure src="/img/ctem/5-steps-in-ctem.png" attr="(Source: Gartner) 5 Steps in the Cycle of Continuous Threat Exposure Management" >}}

### 1. Scoping
เริ่มโดยการพิจารณา "attack surface" ขององค์กร โดยต้องดูให้ครอบคลุมมากกว่าแค่การสแกน vulnerability ตัวอย่างเช่น traditional devices, applications, social media account, online code repository, supply chain ฯลฯ ซึ่งในขั้นตอนนี้น่าจะต้องการข้อมูลจากทุกส่วนเกี่ยวข้องในองค์กร

ถ้าไม่รู้จะเริ่มต้นยังไง Gartner แนะนำให้เริ่มจาก external attack surface กับ SaaS security posture

### 2. Discovery
เริ่มจากการระบุ assets ที่เกี่ยวข้องตาม scope ในข้อ 1 จากนั้นพยายามระบุ exposure หรือความเสี่ยงที่เกิดจาก vulnerability, misconfiguration, supply chain, และความเสี่ยงอื่นๆ

### 3. Prioritization
เป้าหมายของ CTEM ไม่ใช่การจัดการความเสี่ยงทั้งหมด แต่ให้จัดการความเสี่ยงที่สำคัญกว่าก่อน โดยเน้นที่การจัดการ exposure ของ "crown jewel asset" โดยปัจจัยที่ Gartner แนะนำในการพิจารณาคือ urgency, security, compensating controls, residual attack surface, และ risk tolerance ขององค์กร

จากนั้นก็จัดทำแผนเพื่อจัดการความเสี่ยงโดยไล่ตามลำดับความสำคัญที่เราเรียงได้

### 4. Validation
ขั้นตอนนี้ทำหน้าที่สองอย่าง อย่างแรกคือพิสูจน์ว่าความเสี่ยงที่เราระบุไว้ในข้อ 2 มันเป็นความเสี่ยง/exposure ที่ถูก exploit ได้จริง เพื่อให้ส่วนที่เกี่ยวข้องเห็นความจำเป็นในการดำเนินการจัดการความเสี่ยง

อย่างที่สองคือเอาไว้ทดสอบ/monitor ว่าการดำเนินการตามแผนในข้อ 3 สามารถจัดการ exposure/ความเสี่ยง นั้นๆ ได้จริง

### 5. Mobilization
คือการดำเนินการตามแผนที่วางไว้ สิ่งสำคัญคือการสื่อสารแผนให้ส่วนที่เกี่ยวข้องทั้งหมดรับทราบ (security team, IT team, business stakeholders, ฯลฯ) และเข้าใจบทบาทของตัวเอง ว่าต้องทำอะไรบ้าง

## Communicating Results
ผลลัพธ์ที่คาดหวังคือ attack surface ในส่วนที่เราค้นพบควรจะลดลงหรือหายไป โดยอาจมีการจัดทำรายงาน หรืออาจจะเป็น dashboard / trend / KPI เพื่อให้เห็นผลของการลดความเสี่ยง/exposure จากการดำเนินการของทีมงาน

อันนี้เป็นอีกมุมมองนึงของ CTEM ที่ผมรู้สึกว่าทำให้เห็นภาพรวมได้ดีกว่าวงกลมๆ ข้างบน ว่ามันเป็นโปรแกรมที่ต้องอาศัยทั้ง automated tools, manual inspection, GRC, ฯลฯ

{{< figure src="/img/ctem/continuous-threat-exposure-management.svg" attr="(Source: Kroll) CTEM in Action" width="760px">}}

## My Two Cents
เท่าที่ฟังรู้สึกว่าเป็นเฟรมเวิร์กสำหรับจัดการ attack surface ของระบบ IT ขององค์กรมากกว่าระบบ OT เพราะดูจะเน้นไปที่ threat exposure ที่มาจากอินเทอร์เน็ตเป็นหลัก ซึ่งโดยปกติระบบ OT ควรจะถูก protect โดย IT security ขององค์กรเป็นชั้นแรกอยู่แล้ว และไม่ควรมีส่วนที่เชื่อมต่ออินเทอร์เน็ตโดยตรง

## References
* [How to Manage Cybersecurity Threats, Not Episodes](https://www.gartner.com/en/articles/how-to-manage-cybersecurity-threats-not-episodes)
* [Continuous Threat Exposure Management](https://xmcyber.com/ctem/)
* [What is Continuous Threat Exposure Management?](https://www.kroll.com/en/insights/publications/cyber/what-is-continuous-threat-exposure-management)
