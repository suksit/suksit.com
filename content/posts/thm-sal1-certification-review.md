---
title: "THM SAL1 Certification Review"
date: 2025-03-30T08:20:40+07:00
draft: false
toc: true
images:
tags:
  - tryhackme
  - certification
  - security analyst level 1
  - sal1
  - rant
---

เมื่อวานนี้ (29 มี.ค. 68) ผมเพิ่งผ่านการสอบ [Security Analyst Level 1 (SAL1)](https://tryhackme.com/certification/security-analyst-level-1) certification ของ TryHackMe เป็นประสบการณ์สอบที่ค่อนข้างแตกต่างจากครั้งอื่นๆ เลยมาบันทึกประสบการณ์ + feedback ไว้หน่อย

<div style="text-align: center; margin-bottom: -1.5em;">
  <div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="87e90664-661a-4d69-9a4d-d9177386e62a" data-share-badge-host="https://www.credly.com"></div><script type="text/javascript" async src="//cdn.credly.com/assets/utilities/embed.js"></script>
</div>

## Overview

THM SAL1 เป็น certification แบบ hands-on ระดับ entry-level สำหรับ Blue Team  ที่ทาง THM พัฒนาร่วมกับ Accenture และ Salesforce เข้าใจว่าเค้าพยายามวางตำแหน่งให้อยู่ในระดับเดียวกับ CompTIA CySA+ และ [Blue Team Level 1 (BTL1)](/posts/btl1-certification-review/)

## Course Content

การสอบ SAL1 ไม่จำเป็นต้องเรียนจบ learning path ใดๆ สามารถซื้อคูปองเพื่อสอบได้เลย แต่ถ้าเป็นผู้เริ่มต้นหรืออยากเรียนเพื่อให้มีความรู้ก่อนสอบ ทาง THM แนะนำให้เรียนตาม [SOC Level 1](https://tryhackme.com/path/outline/soclevel1) learning path

## Exam Overview

การสอบต้องใช้ voucher 1 ใบ โดยหากสอบไม่ผ่านจะมีสิทธิ์ retake ได้ 1 ครั้ง ตัวผมเองได้รับ voucher มาจาก promotion ของทาง THM สำหรับคนที่ได้รับ certification ของ CompTIA CySA+ หรือ Blue Team Level 1 ก่อนวันที่ 1 มี.ค. 2568 สามารถกรอกฟอร์มเพื่อรับ voucher สอบ SAL1 ฟรี โดยต้องสอบภายในวันที่ 31 มี.ค. 2568

ก่อนสอบต้องยืนยันตัวตนโดยการถ่ายรูปตัวเอง และถ่ายรูป official document ที่ใช้ระบุตัวตนได้ (passport, ID card, etc.) รูปแบบการสอบจะแบ่งเป็น 3 section คือ

* Multiple choice questions
* SOC simulation #1
* SOC simulation #2

เมื่อกดปุ่มเริ่มสอบจะมีเวลาให้ 24 ชั่วโมง เพื่อทำข้อสอบให้ครบ 3 section เมื่อทำเสร็จแต่ละ section จะมีช่วงให้พักได้ โดยเราสามารถกดเริ่ม section ถัดไปได้เมื่อพร้อม ทั้ง 3 section มีคะแนนรวมกัน 1000 คะแนน เงื่อนไขการสอบผ่านคือต้องทำคะแนนให้ได้ 750 คะแนนขึ้นไป

จุดเด่นของ SAL1 คือ SOC simulation ที่จำลองการทำงานในห้อง SOC (Security Operations Center) โดยเราต้องคอย monitor alert ที่เกิดขึ้นแบบ real-time แล้วใช้เครื่องมือที่ทาง THM เตรียมไว้ให้ในการวิเคราะห์ (triage) ว่า alert นั้นไม่เป็น incident (false positive) หรือเป็น incident (true positive) และต้องตัดสินใจว่าจะ escalate case ให้ทีมงานดำเนินการต่อหรือไม่ แล้วเขียนรายงานการวิเคราะห์รวมทั้งข้อแนะนำสำหรับแต่ละ alert โดยรายงานจะถูกตรวจและให้คะแนนโดย AI

## My Exam Experience

ผมใช้ความพยายามในการสอบ SAL1 ถึง 3 ครั้งกว่าจะผ่าน 😅 ประสบการณ์การสอบเป็นประมาณนี้

### 1<sup>st</sup> Attempt &ndash; March 8, 2025

ยืนยันตัวตนสำเร็จ กดปุ่ม Start Exam แล้วเข้าสู่ Section 1 เวลาเริ่มเดิน แต่พอกดปุ่ม Start Section แล้วระบบไม่ยอมพาไปหน้าถัดไป 😅 ติดต่อ support แล้วก็พบว่า THM ไม่มี support ในวันเสาร์-อาทิตย์ ผมพยายาม refresh หน้าเว็บอยู่หลายครั้ง รวมทั้งลอง logout/login ใหม่ ไปจนถึงลองลบ cookies และ clear cache แต่ก็ไม่สำเร็จ แถมช่วงหลังๆ มันขึ้นให้ verify ID อีกที ซึ่งก็พบว่า verify ID แล้วค้าง เข้าหน้า Start Exam ไม่ได้ สรุปว่าไม่มีโอกาสได้ทำข้อสอบ จนหมดเวลา 24 ชั่วโมง ได้ 0 คะแนน = สอบตก 😭 (สังเกตว่า Exam attempt เป็นลำดับที่ 2)

![My First Attempt with 0 Score](/img/thm-sal1-certification-review/first-attempt.png)

หลังจากนั้นผมก็คุยกับ support อยู่หลายวัน จนในที่สุดเค้าต้องทำ ID verification bypass ให้ ผมถึงสามารถเข้าไปสอบได้

### 2<sup>nd</sup> Attempt &ndash; March 17, 2025

คราวนี้เลือกสอบวันธรรมดา ผมเข้าไปสอบได้จนจบ แต่ตอนทำ SOC simulation มันมี scenario นึงที่ตอนแรกผม triage alert ว่าเป็น false positive แต่พอเห็น alert หลังๆ ขึ้นมา พบว่ามันเชื่อมโยงกันและเป็น true positive กะว่า triage อันนี้เสร็จจะกลับไปแก้ของเดิมให้มันถูก แต่ปรากฎว่าพอเขียนรายงานเสร็จปุ๊บ ระบบตัดจบเฉย เลยกลายเป็น triage ผิดไป 2 alert ทำให้ scenario นั้นได้คะแนนน้อย โดยคะแนนรวมอยู่ที่ 744 คะแนน = สอบตก 555+ (สังเกตว่า Exam attempt เป็นลำดับที่ 1)

![My Second Attempt with 744 Score](/img/thm-sal1-certification-review/second-attempt.png)

ก็คิดว่าเออ ไม่เป็นไร รอ retake ละกัน ซึ่งการ retake ต้องรอ cooldown 3 วันถึงจะสอบใหม่ได้ ผมรอถึง 3 วันแล้วก็พบว่า มันไม่มีปุ่มให้กด retake เพราะระบบมองว่าที่ผมกดเข้าไปสอบเมื่อวันที่ 8 มี.ค. แล้วไปต่อไม่ได้คือ failed รอบสองไปเรียบร้อย 😫

ซึ่งมันจะงงๆ หน่อย เพราะอันที่ได้ 0 คะแนนนั่นมันตั้งแต่วันที่ 8 มี.ค. ไม่รู้ทำไมระบบถึงมองว่าเป็น Exam attempt 2... อารมณ์เหมือน Back to the Future

ผมเลยคุยกับ THM support อีกรอบเพื่อถามว่าผมจะขอ retake ได้ไหม เพราะที่ผมเข้าไปสอบครั้งแรกไม่ได้ ผมมองว่าเป็น technical problem ของทาง THM ไม่ใช่ความผิดของผู้สอบ เจรจาอยู่หลายวัน จนในที่สุด support ก็ให้ retake voucher มา 🥹

### 3<sup>rd</sup> Attempt &ndash; March 29, 2025

รอบนี้ทุกอย่างเป็นไปอย่างราบรื่น ทั้งการทำ ID verification และการสอบใน section ต่างๆ ผมใช้เวลาในส่วน SOC simulation น้อยลงกว่าครั้งแรกเพราะพอเข้าใจแล้วว่าข้อสอบต้องการให้ทำอะไรบ้าง สรุปว่าได้คะแนนถึงเกณฑ์ผ่าน ทำไปได้ 893 คะแนน 🥳

![My Third Attempt with 893 Score](/img/thm-sal1-certification-review/third-attempt.png)

เมื่อสอบผ่านแล้วจะได้ certification หน้าตาประมาณนี้ พร้อม Credly badge ที่ผมแปะไว้ตอนต้น blog

![SAL1 Certificate](/img/thm-sal1-certification-review/sal1-certificate.png)

## Feedback

* There should be a dedicated, near real-time support team for SAL1 certification because I think many people will take the exam during weekends, and they cannot wait until Monday if there is a problem with the exam environment
* The SOC simulation should not end automatically, there should be a confirmation dialog for the user (just like in Section 1). Here are my two reasons:
    * The user will have a chance to review the reports before submitting
    * Not sure if it's the case, but I got feedbacks on "False Positives misclassified", which I thought might be caused by the exam automatically ended while there were still some un-triaged alerts.
* THM may want to consider using a more detailed form fields instead of the textarea so the user can provide more specific details in the report, to be more aligned with what the AI grader was expected.
* The support team were very helpful and reasonable 😇
* Yes, I would recommend taking SAL1 certification for entry-level SOC analysts to test their knowledge and skills. It was quite realistic, fun, and exciting.
