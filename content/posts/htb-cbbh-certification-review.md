---
title: "HTB CBBH Certification Review"
date: 2025-02-21T00:00:24+07:00
draft: false
toc: true
images:
tags:
  - rant
  - certified-bug-bounty-hunter
  - cbbh
  - hack-the-box
  - certification
---

## TL;DR
ถ้าจะอ่านสาระล้วนๆ ข้ามไปที่ [CBBH Exam Tips & Resources](#cbbh-exam-tips--resources) ได้เลยครับ 🤣

## Preface
ผมเพิ่งผ่านการสอบ Certified Bug Bounty Hunter ของ Hack The Box (HTB CBBH) เป็นประสบการณ์สอบ hands-on certification ฝั่ง red team ใบที่ 3 ต่อจาก [eJPT](/posts/ejpt-certification-review) และ [CPTS](/posts/htb-cpts-certification-review) รอบนี้รู้สึกสนุกและไม่เครียดเหมือนตอนสอบ CPTS 555+ 🥳

<center><div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="e57ee613-7d61-40c5-9e0b-b92fed9bf774" data-share-badge-host="https://www.credly.com"></div><script type="text/javascript" async src="//cdn.credly.com/assets/utilities/embed.js"></script></center>

## CBBH Course Overview
เงื่อนไขของการสอบ CBBH คือต้องเรียน Bug Bounty Hunter Job Role Path ให้ครบ 100% เนื้อหามีทั้งหมด 20 modules โดยจะมี module ที่เป็นเนื้อหาเดียวกับของ CPTS ประมาณ 50%

อย่างผมที่เรียน Penetration Tester Job Role Path (เพื่อสอบ CPTS) มาแล้ว จะมี progress ก่อนเริ่มเรียน CBBH อยู่ที่ประมาณ 70% 🤣 เลยทำให้ใช้เวลาเรียนจนจบ Bug Bounty Hunter Job Role Path แค่ประมาณสองสัปดาห์

คอร์สโดยรวมก็มีคุณภาพสูงตามสไตล์ HTB ตัวเนื้อหาจะเน้นไปที่การโจมตี web application เป็นหลัก โดยจะไม่เน้นการทำ lateral movement หรือ privilege escalation ปิดท้ายด้วยการสอน Bug Bounty Hunting Process และวิธีการเขียน report of findings แบบ professional

## CBBH Exam Overview
การสอบจะใช้ voucher 1 ใบ เมื่อสอบเสร็จต้องส่ง report ให้ทีมงาน HTB ตรวจสอบและให้ feedback หากสอบไม่ผ่านมีสิทธิ์ retake ได้ 1 ครั้ง พอดีคราวนี้ผมใช้ voucher จาก HTB Enterprise ของที่ทำงาน เลยไม่ต้องกดดันว่าจะเสีย voucher ฟรี 😆

เราสามารถเริ่มสอบเมื่อไรก็ได้ ไม่ต้องจองเวลา และไม่มี proctor เมื่อกดปุ่มเริ่มสอบแล้วจะมีนาฬิกานับถอยหลังให้ 7 วัน เราต้องหา flag เพื่อทำคะแนนให้ได้อย่างน้อย 80 จาก 100 คะแนน และต้องส่ง report ที่มีเนื้อหาตาม template ที่ HTB กำหนด

รูปแบบการสอบจะเป็นการทำ private web application bug bounty พร้อมเขียน report ให้กับบริษัทที่จ้างเรา โดยเริ่มต้นจะมีข้อมูลให้แค่ URL ของเว็บไซต์หลัก และ IP address ของ web server

## My Exam Experience
ผมเริ่มสอบเช้าวันที่ 12 ก.พ. 68 และส่ง report ตอนเย็นวันที่ 18 ก.พ. 68 (ก่อนหมดเวลาสอบประมาณ 12 ชั่วโมง) ประสบการณ์ในการสอบโดยรวมรู้สึกแตกต่างจากตอน[สอบ CPTS](/posts/htb-cpts-certification-review) อยู่พอสมควร 🤔

การสอบคราวนี้ผมลองทำตามแนวทางที่เค้าบอกว่า Hack The Box ออกแบบการสอบไว้เพื่อการนี้ นั่นคือผมไม่ได้ทุ่มเวลาทั้งวันทุกวันให้กับการสอบ CBBH อย่างเดียว พยายามใช้ชีวิตตามปกติ และใช้เวลาสอบในช่วงวันหยุด และวันธรรมดาหลังเลิกงาน

สิ่งที่สัมผัสได้คือ รู้สึกเครียดน้อยกว่าตอนสอบ CPTS และจะทำได้ดีเป็นช่วงๆ ถ้าสรุปเป็น timeline ก็ประมาณนี้

* เริ่มสอบวันแรกเป็นวันหยุด ทำคะแนนได้ 20 คะแนน
* อีก 2 วันต่อมาเป็นวันทำงาน ไม่ได้คะแนนเลย
* มาทำต่อวันเสาร์ทั้งวัน ได้มาอีก 40 คะแนน
* เช้าวันอาทิตย์ได้เพิ่มมาอีก 5 คะแนน
* บ่ายวันอาทิตย์ จนหมดวันจันทร์ (ทำงาน) ไม่ได้คะแนนเลย 
* วันอังคาร (ลาป่วยเพราะท้องเสีย 💩) ช่วงสายๆ ได้เพิ่มมาอีก 15 คะแนน ถึงเกณฑ์ผ่านพอดี
* เวลาที่เหลือนั่งทำ report of findings สลับกับเข้าห้องน้ำ 😫

## The Wait
หลังจากส่ง report เรียบร้อยก็ทำใจว่าคงต้องรอถึงเดือนหน้ากว่าจะรู้ผล เพราะการพิจารณา report ของทีมงาน HTB มี SLA อยู่ที่ 20 วันทำการ ผมส่งไปวันที่ 18 ก.พ. ดังนั้นก็อาจจะต้องรอจนถึงวันที่ 18 มี.ค. ในกรณีเลวร้ายสุด

## The Result
แต่ปรากฏว่าวันต่อมา (19 ก.พ.) เข้าไปดูใน HTB Enterprise ก็พบว่ามันขึ้นว่า "Exam Passed" และมีลิงก์ให้กดดาวน์โหลด certificate แล้ว 😱 

ทีแรกเข้าใจว่าเพราะเป็น HTB Enterprise เลยได้ผลสอบเร็ว แต่พอไปดูใน Discord ก็พบว่ามีคนมาบอกว่าสอบผ่านกันเยอะ แสดงว่าผมบังเอิญส่งไปตอนที่ทาง HTB examiner เค้ากำลังตรวจรายงานล็อตใหม่พอดี 😝

สำหรับ certificate ของ CBBH จะหน้าตาประมาณนี้

{{<image src="/img/htb-cbbh-certification-review/htb-cbbh-certificate.png" alt="Hack The Box CBBH Certificate" position="center" style="box-shadow: 0 5px 10px 0 rgba(0,0,0,0.2); margin-bottom: 1.5em;">}}

## CBBH Exam Tips & Resources
ขอแบ่งเป็นสองส่วน คือ การเตรียมตัวสอบ และระหว่างการสอบ

### Before the Exam
* **Take good notes** แนะนำให้จดโน้ตระหว่างเรียน ส่วนตัวผมจดโน๊ตไม่ค่อยดีเท่าไหร่ คือจดบ้างไม่จดบ้าง สุดท้ายพอจะใช้สิ่งที่ไม่ได้จดไว้ก็ต้องย้อนกลับไปเปิดหาจาก module ใน HTB Academy
* **Learn how to use Burp Suite** แทบจะเรียกว่าเป็นเครื่องมือหลักในการสอบของผมเลยก็ว่าได้
* **Learn how to enumerate & exploit manually** น่าจะเป็นคำแนะนำมาตรฐาน ว่าอย่าหวังพึ่ง automate tools หรือ public exploit อย่างเดียว
* **Learn [SysReptor](https://github.com/Syslifters/sysreptor)** เป็นเครื่องมือทำ penetration testing report ที่ช่วยให้ทำ report ที่มีหน้าตา professional ได้แบบง่ายๆ ช่วยลดความผิดพลาดในการเขียน report ได้มาก และ[มี template สำหรับการสอบ certification ของ HTB](https://www.hackthebox.com/blog/certification-templates) ทั้งหมดให้ใช้ด้วย
* **Watch walkthroughs / read writeups** อันนี้เป็นลิสต์ของ box ที่คนสอบผ่านหลายๆ คนแนะนำให้ศึกษา คิดว่าดูเฉพาะ initial foothold ที่เกี่ยวกับ web application ก็น่าจะพอ
  * Academy
  * BountyHunter
  * Editorial
  * Forge
  * GoodGames
  * Headless
  * Spider 
  * TwoMillion
  * Usage

### During the Exam
* **Think out of the box** เป็นคำที่ทุกคนชอบแนะนำคนที่จะสอบ CBBH เอาจริงๆ ผมก็ว่าไม่ถึงขนาดนั้น เพราะสุดท้ายมันก็วนกลับมาที่การทำ enumeration ว่าเราทำได้ละเอียดครบถ้วนแค่ไหน ครอบคลุมความเป็นไปได้ทั้งหมดหรือยัง
* **Don't get stuck for too long** ถ้าพยายามโจมตีเป้าหมายนึงนานแล้วแต่ไม่สำเร็จ ลองเปลี่ยนไปโจมตีครื่องอื่นแทน วนไปเรื่อยๆ สมองจะได้ไม่ล้า
* **Take a break** อันนี้เกิดจากการสังเกตตัวเองว่า productivity จะดีขึ้นถ้าผมหยุดสอบไปซักพัก แล้วกลับมาทำใหม่... หลังจากนั้นก็จะเริ่ม stuck อีก วนไปเรื่อยๆ ดังนั้นถ้าติดนานๆ การพักอาจจะดีกว่า
* **Let your brain do its thing** จริงๆ น่าจะคล้ายๆ ข้อก่อนหน้า ในการสอบครั้งนี้มีหลายครั้งที่ผมได้ flag แบบแว่บเข้ามาในหัว คืออยู่ดีๆ ก็คิดแนวทางการโจมตีออกระหว่างที่ทำอย่างอื่นอยู่ อันนึงระหว่างอาบน้ำ กับอีกอันระหว่างขับรถกลับคอนโด
* **Keep it simple / Don't overthink it** มีหลายครั้งที่ผมพยายามใช้ท่าแปลกๆ แต่สุดท้ายวิธีที่ทำให้ได้ flag มันตรงไปตรงมากว่าที่คิดตอนแรกเยอะ ถ้าคิดอะไรไม่ออกก็ลองย้อนกลับไปดูเนื้อหาใน module ที่เรียน

## Summary
สรุปว่าเป็นประสบการณ์สอบ certification ที่ดีและสนุกไม่แพ้ CPTS แต่เครียดน้อยกว่าเยอะ 🥹 ได้เรียนรู้เพิ่มเติมหลายอย่างระหว่างการสอบ ว่าเออมันทำแบบนี้ได้ด้วยแฮะ ทั้งในเรื่องช่องโหว่ เทคนิคการโจมตี รวมไปถึงการตั้งค่า และการพัฒนาเว็บแอปพลิเคชัน
