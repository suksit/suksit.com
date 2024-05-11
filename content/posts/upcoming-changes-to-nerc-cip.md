---
title: "Upcoming Changes to NERC CIP"
date: 2024-05-11T21:42:30+07:00
draft: false
toc: false
images:
tags:
  - nerc cip
  - cybersecurity
  - standard
  - ot security
---

วันก่อนได้อ่าน newsletter ฉบับที่ 8 ของ SANS ในชื่อหัวข้อ [Virtual Sharing is Caring for NERC CIP](https://www.linkedin.com/pulse/virtual-sharing-caring-nerc-cip-sans-ics-0fn4c/) มีสาระสำคัญโดยสรุป 3 หัวข้อใหญ่ๆ คือ

1. มาตรฐาน NERC CIP เกือบทุกตัวมีการอัปเดตเป็นเวอร์ชันใหม่
2. มีมาตรฐานตัวใหม่ที่ร่างขึ้นมาตามคำสั่งของ FERC เมื่อปี 2023
3. มีการปรับปรุง NERC Glossary of Terms

## การอัปเดตมาตรฐาน NERC CIP

ส่วนใหญ่เป็นการอัปเดตเพื่อรองรับการใช้งาน virtualization กับระบบ OT/ICS ของหน่วยงานที่รับผิดชอบ (responsible entity) โดยมาตรฐานที่ผ่านการโหวต เทียบกับปัจจุบัน เป็นดังนี้

| Current CIP Standards | Upcoming CIP Standards |
| --------------------- | ---------------------- |
| CIP-002-5.1a          | CIP-002-7              |
| CIP-003-8             | CIP-003-10             |
| CIP-004-7             | CIP-004-8              |
| CIP-005-7             | CIP-005-8              |
| CIP-006-6             | CIP-006-7              |
| CIP-007-6             | CIP-007-7              |
| CIP-008-6             | CIP-008-7              |
| CIP-009-6             | CIP-009-7              |
| CIP-010-4             | CIP-010-5              |
| CIP-011-3             | CIP-011-4              |
| CIP-012-1             | (no changes)           |
| CIP-013-2             | CIP-013-3              |
| CIP-014-3             | (no changes)           |

## มาตรฐานตัวใหม่ CIP-015-1

เป็นมาตรฐานที่พูดถึง Internal Network Security Monitoring (INSM) ตามคำสั่งของ FERC (Federal Energy Regulatory Commission) [Order No. 887](https://www.federalregister.gov/documents/2023/02/09/2023-01453/internal-network-security-monitoring-for-high-and-medium-impact-bulk-electric-system-cyber-systems) โดยมีวัตถุประสงค์หลักๆ 3 เรื่อง ได้แก่

1. ให้หน่วยงานที่รับผิดชอบจัดทำ baseline ของ network traffic ในระบบเครือข่ายที่อยู่ในขอบเขต NERC CIP
2. ให้หน่วยงานที่รับผิดชอบเฝ้าดูและตรวจจับกิจกรรม การเชื่อมต่อ อุปกรณ์ และซอฟต์แวร์ ที่ไม่ได้รับอนุญาต ในระบบเครือข่ายที่อยู่ในขอบเขต NERC CIP
3. ให้หน่วยงานที่รับผิดชอบ ระบุกิจกรรมที่ผิดปกติ โดยมีความเชื่อถือได้ในระดับสูง

## คำนิยามใหม่ 2 ตัว เพื่อรองรับ Virtualized Assets

อันนี้ผมอ่านแล้วยังไม่ค่อยเก็ตเท่าไร ขอยกทั้งก้อนมาแปะเก็บไว้ก่อน

> **1. Shared Cyber Infrastructure (SCI):** One or more programmable electronic devices, including the software that shares the devices’ resources, that:
>
> * Hosts one or more Virtual Cyber Assets (VCA) included in a BES Cyber Systems (BCS) or their associated Electronic Access Control or Monitoring Systems (EACMS) or Physical Access Control Systems (PACS); and hosts one or more VCAs that are not included in, or associated with, BCS of the same impact categorization; or
> * Provides storage resources required for system functionality of one or more Cyber Assets or VCAs included in a BCS or their associated EACMS or PACS; and also for one or more Cyber Assets or VCAs that are not included in, or associated with, BCS of the same impact categorization
>
> SCI does not include the supported VCAs or Cyber Assets with which it shares its resources.

> **2. Virtual Cyber Asset (VCA):** A logical instance of an operating system or firmware, currently executing on a virtual machine hosted on a BES Cyber Asset; Electronic Access Control or Monitoring System; Physical Access Control System; Protected Cyber Asset; or Shared Cyber Infrastructure (SCI).
>
> Virtual Cyber Assets (VCAs) do not include:
>
> * Logical instances that are being actively remediated in an environment that isolates routable connectivity from BES Cyber Systems;
> * Dormant file-based images that contain operating systems or firmware; or
> * SCI or Cyber Assets that host VCAs.
>
> Application containers are considered software of VCAs or Cyber Assets.

สรุปคร่าวๆ คือตัว SCI น่าจะหมายถึง virtualization infrastructure หรือเครื่อง host ที่มีทั้ง VCA ที่อยู่ในขอบเขตของ NERC CIP อยู่ร่วมกับ VCA อื่นๆ

ส่วนตัว VCA ก็น่าจะเป็น VM (virtual machine) หรือ virtual appliances ที่รันอยู่บน SCI อีกที
