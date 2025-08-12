---
title: "THM PT1 Certification Review"
date: 2025-08-12T15:30:30+07:00
draft: false
toc: true
images:
tags:
  - tryhackme
  - certification
  - junior penetration tester
  - pt1
  - rant
---

เมื่อวานนี้ (11 ส.ค. 68) ผมเพิ่งผ่านการสอบ [Junior Penetration Tester (PT1)](https://tryhackme.com/certification/junior-penetration-tester/) certification ของ TryHackMe เป็นประสบการณ์สอบ certification ใบที่สองของค่ายนี้ เลยมาบันทึกประสบการณ์ไว้อีกเช่นเคย

<div style="text-align: center; margin-bottom: -1.5em;">
  <div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="2f156e98-12d4-4e4e-8459-ce39ea2467db" data-share-badge-host="https://www.credly.com"></div><script type="text/javascript" async src="//cdn.credly.com/assets/utilities/embed.js"></script>
</div>

## Overview

THM PT1 เป็น certification แบบ hands-on ระดับ entry-level สำหรับ Red Team ที่ทาง THM พัฒนาร่วมกับ hiring managers และ penetration testers หลายคน เข้าใจว่าเค้าพยายามวางตำแหน่งให้อยู่ในระดับเดียวกับ [eJPT](/posts/ejpt-certification-review) ของ INE และ PJPT ของ TCM Security

## Course Content

การสอบ PT1 ไม่จำเป็นต้องเรียนจบ learning path ใดๆ สามารถซื้อคูปองเพื่อสอบได้เลย แต่ถ้าเป็นผู้เริ่มต้นหรืออยากเรียนเพื่อให้มีความรู้ก่อนสอบ ทาง THM แนะนำให้เรียนตาม [Jr Penetration Tester](https://tryhackme.com/path/outline/jrpenetrationtester) learning path

## Exam Overview

การสอบต้องใช้ voucher 1 ใบ โดยหากสอบไม่ผ่านจะมีสิทธิ์ retake ได้ 1 ครั้ง ตัวผมเองได้รับ voucher มาจาก promotion ของทาง THM สำหรับคนที่ถือ eJPT, PJPT, หรือ OSCP สามารถกรอกฟอร์มเพื่อรับ voucher สอบ PT1 ฟรี โดยต้องสอบภายในวันที่ 31 ส.ค. 2568 (เหมือนตอนหลังจะเพิ่มสิทธิ์ให้คนถือ Pentest+, GPEN, และ PNPT ด้วย)

ก่อนสอบต้องยืนยันตัวตนโดยการถ่ายรูปตัวเอง และถ่ายรูป official document ที่ใช้ระบุตัวตนได้ (passport, ID card, etc.) รูปแบบการสอบจะแบ่งเป็น 3 section ที่สามารถเลือกสลับทำได้ตลอดเวลา คือ

1. Web Applicaton Security (400 คะแนน)
2. Network Security (360 คะแนน)
3. Active Directory (240 คะแนน)

เมื่อกดปุ่มเริ่มสอบจะมีเวลาให้ 48 ชั่วโมง เพื่อทำข้อสอบให้ครบทั้ง 3 section มีคะแนนรวม 1000 คะแนน เงื่อนไขการสอบผ่านคือต้องทำคะแนนให้ได้ 750 คะแนนขึ้นไป

จุดเด่นของ PT1 คือ เป็นการสอบแบบ hands-on ทั้งหมด โดยจำลองระบบเครือข่ายของ corporate network ที่มีทั้งส่วนที่เป็น web application, internal servers, และ Active Directory โดยแต่ละส่วนจะมี flag จำนวนแตกต่างกัน รวมทั้งหมด 10 flag

เราต้องทดสอบเจาะระบบทั้ง 3 section แล้วพยายามหา flag เพื่อพิสูจน์ว่าเราสามารถ compromise เซิร์ฟเวอร์หรือ exploit ช่องโหว่ (vulnerability) ต่างๆ ได้สำเร็จ แล้วเขียนรายงานการวิเคราะห์รวมทั้งข้อแนะนำในการแก้ไขสำหรับแต่ละช่องโหว่ โดยรายงานจะถูกตรวจและให้คะแนนโดย AI

## My Exam Experience

ผมพบว่าทำส่วนที่เป็น Active Directory ได้ครบก่อนส่วนอื่น เพราะค่อนข้างตรงไปตรงมาและเอา methodology ที่เรียนจาก HTB CPTS มา apply ได้แบบเต็มๆ ส่วนถัดมาที่ทำได้ครบคือ Network Security ส่วนนี้มีสิ่งที่รู้สึกว่าไม่ค่อย make sense และไม่สมจริงอยู่นิดหน่อย (อ่านรีวิวของคนอื่นหลายๆ ที่ก็พูดในทำนองเดียวกัน) แต่ก็ช่างมันละกัน 🤣 การหา flag ในส่วนนี้เหมือน CTF ทั่วไป ที่บอกพาธของไฟล์ `user.txt` และ `root.txt` มาให้

ส่วนสุดท้ายที่ผมใช้เวลามากที่สุดคือ Web Application Security เนื่องจากวิธีที่จะได้ flag มานั้นจะไม่เหมือน 2 ส่วนที่พูดไปตอนแรก สรุปรวมๆ คือเราต้อง test ไปเรื่อยๆ ว่าแต่ละ feature ในเว็บมีช่องโหว่อะไรบ้าง ตามประเภทของ vulnerability ที่กำหนดไว้ใน Rules of Engagement (RoE) โดยถ้าทดสอบแล้วสามารถ exploit ช่องโหว่ได้สำเร็จ server จะพ่น flag ออกมาให้ ในส่วนนี้ผมหาไปได้ 3 จาก 4 flag แล้วหมดพลัง แต่คิดว่าคะแนนน่าจะถึงเกณฑ์ผ่านแล้ว เลยเลิกทำ แล้วกดส่ง report ไปวัดใจกับ AI ต่อ 😑

สรุปว่าพี่ AI ใจดี ให้สอบผ่านที่ 802 คะแนน 🥳

![My First Attempt with 802 Score](/img/thm-pt1-certification-review/first-attempt.png)

เมื่อสอบผ่านแล้วจะได้ certification หน้าตาประมาณนี้ พร้อม Credly badge ที่ผมแปะไว้ตอนต้น blog

![PT1 Certificate](/img/thm-pt1-certification-review/pt1-certificate.png)

## PT1 Exam Tips

เนื่องจากมีคนเขียน review การสอบ PT 1 ไว้ค่อนข้างเยอะและละเอียดกว่าผมมากกก เลยพยายามจะไม่เขียนซ้ำ แต่แนะนำให้อ่านอย่างน้อย 3 blog นี้

1. [PT1 Review - Dragkob](https://dragkob.notion.site/pt1-review-dragkob)
2. [TryHackMe PT1 Review: Real Hands-On Pentest Cert for Beginners?](https://blog.sth.sh/tryhackme-pt1-review-real-hands-on-pentest-cert-for-beginners-de332c9229ec)
3. [Full Guide to help you pass your TryHackMe PT1 Exam](https://systemweakness.com/full-guide-to-help-you-pass-your-tryhackme-pt1-exam-3cf1f1fcb30b)

โดยส่วนตัวขอฝากคำแนะนำไว้ 2 เรื่องคือ

1. รูปแบบการเขียน report ให้ดูตัวอย่างจากห้อง [Writing Pentest Reports](https://tryhackme.com/room/writingpentestreports) ของ TryHackMe
2. คอนเซปต์ของ half-flag หรือ partial flag ในส่วนของ Web Application Security คือ "ช่องโหว่เดียวกัน สามารถมี impact ได้หลายแบบ" ถ้าเข้าใจแนวคิดนี้ จะพบว่าการที่ระบบแยก flag ออกเป็นสองส่วนจะค่อนข้าง make sense และน่าจะทำให้สามารถหา flag ส่วนที่เหลือได้ไม่ยากนัก