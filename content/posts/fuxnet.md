---
title: "Fuxnet"
date: 2024-04-24T23:23:39+07:00
draft: false
toc: true
images:
tags:
  - cybersecurity
  - fuxnet
  - malware
  - ics
  - operational technology
---

## Overview

เมื่อช่วงวันหยุดสงกรานต์ มีการแจ้งเตือนเรื่องมัลแวร์ที่โจมตีระบบ ICS/OT ตัวใหม่ชื่อ "Fuxnet" เป็น[ข่าวในเว็บ SecurityWeek](https://www.securityweek.com/destructive-ics-malware-fuxnet-used-by-ukraine-against-russian-infrastructure/) และ [Dark Reading](https://www.darkreading.com/ics-ot-security/dangerous-new-ics-malware-targets-orgs-in-russia-and-ukraine) โดยในข่าวจะมีลิงก์ไปยัง[รายงานวิจัยของ Claroty](https://claroty.com/team82/research/unpacking-the-blackjack-groups-fuxnet-malware) ที่ผมอ่านแล้วรู้สึกว่าวิเคราะห์ได้ดี 🧐

ในตัวรายงานจะมีลิงก์ไปที่[เว็บของกลุ่ม Blackjack](https://ruexfil.com/mos/) ที่เป็นกลุ่มแฮกเกอร์ของยูเครน ซึ่งเป็นผู้พัฒนามัลแวร์ดังกล่าวเพื่อใช้โจมตีอุปกรณ์ sensor ประมาณ 87,000 ตัว และ gateway อีก 1,700 ตัว ของบริษัท Moscollector ที่เป็นผู้ดูแลระบบ critical infrastructure monitoring system ของรัสเซีย 💥

กลุ่ม Blackjack อ้างว่าได้โจมตีบริษัท Moscollector โดยมีเหตุการณ์สำคัญดังนี้

* เข้าถึงครั้งแรก (initial access) ตั้งแต่เดือนมิถุนายน 2023
* สามารถเข้าถึงระบบ 112 Emergency Service
* หยุดการทำงานของอุปกรณ์ sensor และ gateway ทั้งหมดของโครงสร้างพื้นฐานสำคัญ เช่น สนามบิน รถไฟใต้ดิน ท่อส่งก๊าซ ฯลฯ
* หยุดการทำงานของอุปกรณ์เราเตอร์และไฟร์วอลล์
* ลบข้อมูลจากเซิร์ฟเวอร์ เวิร์กสเตชัน ฐานข้อมูล และทำลายข้อมูลไป 30 TB รวมทั้งข้อมูลที่สำรองไว้
* ทำให้ keycard ที่ใช้เข้าออกอาคารของบริษัท Moscollector ใช้งานไม่ได้ทั้งหมด (invalidated)
* เปลี่ยนแปลงหน้าเว็บไซต์ (defaced) ของบริษัท Moscollector

## How Fuxnet Works

ทาง Claroty วิเคราะห์ว่าระบบ monitoring system ของบริษัท Moscollector น่าจะมีรูปแบบการเชื่อมต่อประมาณนี้

{{< figure src="/img/fuxnet/moscollector-monitoring-system.png" attr="Moscollector's Monitoring System" >}}

ในรายงานต้นทางจะวิเคราะห์ลึกลงไปถึงตัว sensor และ gateway แต่ผมขี้เกียจอธิบาย ไปดูในเว็บของ Claroty น่าจะได้รายละเอียดครบถ้วนกว่า 😂

สรุปคร่าวๆ คืออุปกรณ์ sensors และ gateways เป็นผลิตภัณฑ์ของบริษัท AO SBK โดยอุปกรณ์ทั้งสองจะสื่อสารกันด้วยโปรโตคอล M-Bus หรือ Meter-Bus ซึ่งเป็นโปรโตคอลมาตรฐานของยุโรปที่ใช้ในการอ่านค่าจากมิเตอร์น้ำ ก๊าซ หรือไฟฟ้า

sensor แต่ละตัวจะเชื่อมต่อกับ gateway โดยใช้อินเทอร์เฟซ RS485 และบนอุปกรณ์ gateway จะมี IoT router หรือ 3G/4G modem เพื่อเชื่อมต่ออินเทอร์เน็ตและส่งข้อมูลที่ได้จาก sensors ไปยังระบบ monitoring system

ทาง Claroty ได้วิเคราะห์ต้วอย่างโค้ดของมัลแวร์ Fuxnet และ screenshots ที่กลุ่ม Blackjack เผยแพร่ไว้ในเว็บของตัวเอง และสันนิษฐานว่ามัลแวร์น่าจะถูกติดตั้งลงบนอุปกรณ์ gateway แต่ละตัว โดยน่าจะทำผ่าน remote access protocol เช่น SSH หรืออาจเป็นโปรโตคอลเฉพาะของ SBK ที่ใช้โดยซอฟต์แวร์ SBKManager

* เมื่อถูกติดตั้งแล้วมัลแวร์จะเริ่มทำงาน โดยพยายามลบไฟล์และไดเร็กทอรีสำคัญ, ปิดเซอร์วิสสำหรับการ remote access ทั้งหมด, รวมทั้งลบ routing table, ลบ file system, และเขียนข้อมูลทับ flash memory ของอุปกรณ์ gateway
* จากนั้นมัลแวร์จะทำลาย NAND memory chip ของอุปกรณ์ gateway โดยการเขียนข้อมูลทับไปเรื่อยๆ จนกว่าจะไม่สามารถเขียนข้อมูลได้อีก นอกจากนี้ยังมีการทำลาย UBI volume เพื่อให้ไม่สามารถบูตอุปกรณ์ขึ้นมาได้
* นอกเหนือจากการทำลายอุปกรณ์ gateway แล้ว มัลแวร์ Fuxnet ยังพยายามทำ Denial-of-Sevice (DOS) โดยส่งข้อมูลโปรโตคอล M-Bus จำนวนมากไปยัง sensor ทุกตัวอย่างต่อเนื่อง อาจจะเพื่อให้ sensor และ gateway ไม่สามารถคุยกันได้ หรืออาจต้องการ trigger condition บางอย่างที่ทำให้ sensor พัง

กระบวนการข้างต้นทั้งหมด มีตัวอย่างโค้ดประกอบอยู่ในรายงานของ Claroty

## Fuxnet vs Stuxnet

ในเว็บไซต์ของกลุ่ม Blackjack ระบุว่ามัลแวร์ตัวนี้ชื่อ Fuxnet และมีวงเล็บต่อท้ายว่า (Stuxnet on steroids) ผมเลยลองเปรียบเทียบมัลแวร์ทั้งสองตัวดูว่า มันเหมือนหรือต่างกันยังไงบ้าง ด้วยความรู้เท่าที่มี ผมมองว่าน่าจะเป็นประมาณนี้

| Topic | Fuxnet | Stuxnet |
| ----- | ------ | ------- |
| Developed by | Ukraine | (Supposedly) USA & Israel |
| Operation Mode | Human-operated malware | Autonomous worm |
| Development Cost | (Should be) Relatively lower | (Should be) Very high |
| Target | Moscollector industrial sensor and monitoring infrastructure (Russia) | Natanz nuclear enrichment lab (Iran) |
| Scale of Damage | Widespread<br>(number of damaged devices and affecfed stakeholders -- airports, subways, gas, water, etc.) | Site-specific<br>(only Iran's nuclear lab) |
| Cost of Damage | (Should be) Relatively lower | (Should be) Very high |
| Stealthiness | Loud<br>(directly disables IoT gateways and performs DOS on sensors) | Silent<br>(modifies PLC's settings and reports normal values back to HMI) |

## Summary

สรุปว่า Fuxnet เป็น ICS malware ที่น่าสนใจศึกษา เพราะสามารถโจมตีอุปกรณ์ IoT ที่เป็นผลิตภัณฑ์ COTS (Commercial off-the-shelf) ที่ใช้โปรโตคอลมาตรฐานในการสื่อสาร และน่าจะถูกใช้งานในหลายองค์กร 🤔

อย่างไรก็ตาม ประเด็นที่น่าสนใจอีกอย่างที่ไม่มีระบุไว้ในรายงานของ Claroty และในเว็บไซต์ของกลุ่ม Blackjack ก็คือ initial access มาจากทางไหนก่อนที่ผู้โจมตีจะเข้าถึงระบบ monitoring system ได้ ถ้าให้เดาเล่นๆ ก็น่าจะมาจาก IT network ก่อน แล้วค่อยทำ lateral movement เข้ามาที่ระบบ OT/ICS อีกที 💀

สรุปของสรุป Cybersecurity is a team sport ไม่ว่าระบบ IT หรือ OT ผู้เกี่ยวข้องก็ควรพยายามทำความเข้าใจ แลกเปลี่ยนความรู้และแนวคิด ช่วยกันออกแบบ เฝ้าระวัง ตอบสนองต่อการโจมตี และปรับปรุงแก้ไข เพราะสุดท้ายเมื่อโดนโจมตีก็เป็นความเสียหายของทั้งองค์กร (และอาจถึงระดับประเทศ) อยู่ดี
