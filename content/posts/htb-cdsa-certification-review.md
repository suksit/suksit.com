---
title: "HTB CDSA Certification Review"
date: 2025-07-05T10:29:42+07:00
draft: false
toc: true
images:
tags:
  - rant
  - certified-defensive-security-analyst
  - cdsa
  - hack-the-box
  - certification
---

## TL;DR
ถ้าจะอ่านสาระล้วนๆ ข้ามไปที่ [CDSA Exam Tips & Resources](#cdsa-exam-tips--resources) ได้เลยครับ 🤣

## Preface
ผมเพิ่งผ่านการสอบ Certified Defensive Security Analyst ของ Hack The Box (HTB CDSA) เป็นประสบการณ์สอบ hands-on certification ฝั่ง blue team ใบที่ 3 ต่อจาก [BTL1](/posts/btl1-certification-review) และ [TryHackMe SAL1](/posts/thm-sal1-certification-review) ถือเป็นประสบการณ์สอบ certification ที่น่าสนใจอีกครั้งสำหรับผม

<center><div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="b1267119-d67d-4bad-a690-2d57a747c226" data-share-badge-host="https://www.credly.com"></div><script type="text/javascript" async src="//cdn.credly.com/assets/utilities/embed.js"></script></center>

## CDSA Course Overview
เงื่อนไขของการสอบ CDSA คือต้องเรียน SOC Analyst Job Role Path ให้ครบ 100% เนื้อหามีทั้งหมด 15 modules

สารภาพตามตรงว่าผมเรียนแบบ speedrun เพื่อต้องการเก็บ Cube ให้ครบก่อน Silver Annual Subscription จะหมดอายุ (ไม่ควรเอาเป็นแบบอย่าง) 😫 ซึ่งก็พอถูไถไปได้เพราะมีความรู้ + ทักษะจากที่เคยเรียนใน TryHackMe และ BTL1 มาบ้างแล้ว

คอร์สโดยรวมก็มีคุณภาพสูงตามสไตล์ HTB ตัวเนื้อหาจะเน้นไปที่การวิเคราะห์ log, การทำ incident handling, การทำ network traffic analysis, การทำ threat hunting, รวมไปถึงการทำ digital forensics และ malware analysis โดยมี tools หลักคือ Elastic SIEM กับ Splunk

## CDSA Exam Overview
การสอบจะใช้ voucher 1 ใบ เมื่อสอบเสร็จต้องส่ง report ให้ทีมงาน HTB ตรวจสอบและให้ feedback หากสอบไม่ผ่านมีสิทธิ์ retake ได้ 1 ครั้ง ตอนสอบผมใช้ voucher จาก HTB Enterprise ของที่ทำงานอีกเช่นเคย มีแล้วต้องใช้ให้คุ้ม 😁

เราสามารถเริ่มสอบเมื่อไรก็ได้ ไม่ต้องจองเวลา และไม่มี proctor เมื่อกดปุ่มเริ่มสอบแล้วจะมีนาฬิกานับถอยหลังให้ 7 วัน เราต้องหา flag เพื่อทำคะแนนให้ได้อย่างน้อย 85 จาก 100 คะแนน และต้องส่ง report ที่มีเนื้อหาตาม template ที่ HTB กำหนด

รูปแบบการสอบจะเป็นการทำ private security incident investigation พร้อมเขียน report ให้กับบริษัทที่จ้างเรา โดยจะมี context ตอนเริ่มให้นิดหน่อยว่ามันเกิดเหตุการณ์อะไรขึ้น ทำไมเราถึงต้องเข้ามา investigate incident

## My Exam Experience
ผมเริ่มสอบเช้าวันที่ 24 พ.ค. 68 และส่ง report ตอนเช้าวันที่ 31 พ.ค. 68 ใช้เวลาเกือบเต็มโควต้า 7 วันพอดี

การสอบคราวนี้ผมยังใช้แนวทางเดียวกับตอน[สอบ CBBH](/posts/htb-cbbh-certification-review) ก็คือไม่ได้นั่งทำทั้งวันทุกวัน โดยใช้ชีวิตตามปกติ และใช้เวลาสอบในช่วงวันหยุด และวันธรรมดาหลังเลิกงาน

เนื่องจากผมไม่ได้ทำงานเป็น SOC analyst ทำให้ทุกครั้งที่มีการสอบหรือเล่น CTF โจทย์แนวๆ blue team investigation แบบนี้ จะรู้สึกว่ามันยาก แต่ก็พอจะทำคะแนนได้อยู่ถ้ามี guiding question มาให้ 

> ถ้าให้ประเมินตัวเองก็คิดว่ามี skill ที่จะหาคำตอบได้ แต่ยังขาด intuition หรือ sense ในการประกอบชิ้นส่วนจากหลักฐานต่างๆ ให้มันเชื่อมโยงกันและได้ออกมาเป็น security incident report 🥺

ผมน่าจะใช้เวลาไม่เกิน 3 วันในการหา flag จนได้คะแนนผ่านเกณฑ์ หลังจากนั้นเป็นเวลาที่ใช้ทำ report ล้วนๆ

ระหว่างที่นั่งทำ report ก็มีความรู้สึกว่าการเขียน incident investigation report นี่มันยากกว่าการเขียน penetration testing report เยอะเลย เพราะมันเป็นการพยายามหาว่า attacker เข้ามาทำอะไรกับระบบบ้าง ซึ่งสิ่งที่เราหาได้ในรายงาน มันถูกต้องและครบถ้วนหรือเปล่าก็ไม่รู้ 😵‍💫 ต่างจาก pentest report ที่เป็นการเขียนรายงานสิ่งที่เราทำเองกับมือ

> สิ่งที่ได้จากการสอบครั้งนี้คือ รู้สึกนับถือทีมงานฝั่ง blue team หรือ SOC หรือใครก็ตามที่สามารถ investigate incident และเขียน report ออกมาได้เป็นเรื่องราว อ่านเข้าใจง่าย และได้ข้อมูลครบถ้วน เพราะมันไม่ใช่เรื่องที่ทำได้ง่ายๆ เลย (อย่างน้อยก็สำหรับผม) 🙏

## The Result
ผมส่ง report ไปเมื่อวันที่ 31 พ.ค. และรู้ผลสอบเมื่อวันที่ 1 ก.ค. นับวันแล้วก็ประมาณ 20 business days พอดีตาม SLA ของ HTB

สำหรับ certificate ของ CDSA จะหน้าตาประมาณนี้

{{<image src="/img/htb-cdsa-certification-review/htb-cdsa-certificate.png" alt="Hack The Box CDSA Certificate" position="center" style="box-shadow: 0 5px 10px 0 rgba(0,0,0,0.2); margin-bottom: 1.5em;">}}

## CDSA Exam Tips & Resources
เอาจริงๆ คือไม่กล้าแนะนำ tips ใดๆ เพราะเป็นการสอบที่ผมน่าจะผ่านมาได้แบบฉิวเฉียด แต่สิ่งที่พอจะนึกออกคือรูปแบบการสอบจะให้อารมณ์คล้ายๆ [Boss of the SOC (BOTS) ของ Splunk](https://bots.splunk.com/) ถ้าไปลองเล่นดูก่อนก็น่าจะสร้างความคุ้นเคยได้ดี

อ้อ... อีกเรื่องคือ ถ้ามีความรู้ฝั่ง offensive security ด้วยก็น่าจะเป็นประโยชน์ตอนทำ incident investigation เพราะอาจช่วยให้จินตนาการออกว่า attack chain, TTPs, และ tools ที่ attacker น่าจะใช้ มันมีอะไรบ้าง ทำให้กำหนดเป้าหมายในการค้นหาได้ดีขึ้นครับ

## Summary
ผมคิดว่า CDSA เป็น certification ที่ดีมากๆ สำหรับคนทำงานระดับ tier 2 ขึ้นไปในศูนย์ SOC เพราะน่าจะได้ความรู้และสกิลที่จำเป็นในการทำงานครบถ้วน แต่สำหรับคนที่ทำงานใน tier 1 อาจจะไปลองเริ่มกับ THM SAL1 หรือ Blue Team Level 1 (BTL1) ก่อน น่าจะได้รับความรู้และทักษะที่ตรงกับงานกว่า 🤔