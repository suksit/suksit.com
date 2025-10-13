---
title: "GRID Certification Review"
date: 2025-10-13T13:10:27+07:00
draft: false
toc: true
images:
tags:
  - sans
  - ics515
  - certification
  - giac
  - grid
  - giac response and industrial defense
  - rant
---

ผมผ่านการสอบ [GIAC Response and Industrial Defense (GRID)](https://www.giac.org/certifications/response-industrial-defense-grid/) certification เมื่อประมาณกลางเดือน ก.ย. 68 คิดว่าน่าจะเป็น certification ที่แพงที่สุดในชีวิต ณ ตอนนี้ (รวมค่าเรียน + สอบ) 🤣 เลยมาบันทึกประสบการณ์ไว้กันลืม

<div style="text-align: center; margin-bottom: -1.5em;">
  <div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="1a6be0c6-0cee-4db4-94e4-4db4426ab50c" data-share-badge-host="https://www.credly.com"></div><script type="text/javascript" async src="//cdn.credly.com/assets/utilities/embed.js"></script>
</div>

## Overview

GRID เป็น certification ด้านการทำ cyber defense, monitoring, and incident response สำหรับระบบ OT/ICS โดยความรู้ที่ใช้ในการสอบจะมาจากหลักสูตร [ICS515: ICS Visibility, Detection, and Response](https://www.sans.org/cyber-security-courses/ics-visibility-detection-response) ของ SANS Institute

## Course Content

เนื้อหาในหลักสูตร ICS515 ของ SANS ถือว่าดีมากๆ สำหรับผม เคยได้ยินคนบอกว่าเรียนคอร์ส SANS แล้วเหมือน "drinking from a fire hose" พอได้มาเรียนเองก็เข้าใจได้ทันทีว่าเป็นคำเปรียบเทียบที่ไม่เกินจริง 😱

ICS515 จะแบ่งเนื้อหาออกเป็น 5 section เรียงตามนี้

1. ICS Cyber Threat Intelligence
2. Visibility and Asset Identification
3. ICS Threat Detection
4. Incident Response
5. Threat and Environment Manipulation

ในแต่ละ section จะมีเนื้อหาการเรียนเป็น slide พร้อมคำบรรยายแบบละเอียด(มากกกกก) โดยจะมี case study ของการโจมตีระบบ OT/ICS ที่เกิดขึ้นจริงแทรกอยู่เป็นระยะๆ ปิดท้ายแต่ละ section ด้วยการทำ lab ที่จำลอง supply chain ของระบบไฟฟ้า ตั้งแต่ระบบผลิต (generation) ระบบส่ง (transmission) และระบบจำหน่าย (distribution) บนบอร์ดและ PLC ที่แถมมากับ coursebook หน้าตาประมาณนี้

{{< figure src="/img/grid-certification-review/ics515-plc-board.png" >}}

(รูปจาก [LinkedIn Post ของ Robert M. Lee](https://www.linkedin.com/posts/robmichaellee_im-proud-to-announce-a-major-update-to-my-activity-6845679125366132737-X20e/) ที่เป็นคนสร้างคอร์ส ICS515 เพราะบอร์ดของผมแกะเก็บลงกล่องไปแล้ว ขี้เกียจเอามาประกอบใหม่ 555+)

โดยส่วนตัวผมชอบคอร์สนี้ตรงที่เค้าเอา concept / best practice หลายๆ อย่างมาสอนและทำให้เห็นภาพว่าแต่ละอย่างมันเชื่อมโยงกันยังไง เช่น

* Active Cyber Defense Cycle (ACDC)
* Analysis of Competing Hypotheses (ACH)
* Collection Management Framework (CMF)
* Five ICS Cybersecurity Critical Controls
* ICS Cyber Kill Chain
* Threat and Environment Manipulation (TEM)

นั่งเรียนไปก็จินตนาการไปด้วยว่าจะเอาเรื่องไหนมาปรับใช้กับงานที่ทำอยู่ได้บ้าง 💭 คหสต. แค่เรียนจนจบแล้วเอาความรู้และทักษะไปใช้ในองค์กรได้ ก็น่าจะคุ้มค่าอยู่ แต่ถ้าต้องออกค่าเรียน + สอบเอง ผมก็ขอยอมแพ้ ถถถ 😵

## Exam Overview

ถ้าซื้อ GRID Certification Exam จะมี Practice Test ติดมาให้ด้วย 2 อัน ข้อสอบจะเป็นแบบ multiple choice questions (MCQ) จำนวน 75 ข้อ ให้เวลาทำ 2 ชั่วโมง การสอบจะเป็นแบบ open book คือสามารถเอาหนังสือหรือโน๊ตเข้าไปในห้องสอบได้ด้วย คะแนนขั้นต่ำที่ถือว่าสอบผ่านคือ 74%

แนวทางที่เค้าแนะนำกันคือให้ทำ index และ highlight ข้อความสำคัญใน coursebook เพื่อให้หาหัวข้อที่เกี่ยวข้องได้สะดวกและรวดเร็ว ถ้าลอง google ดูก็จะเจอหลายแนวทาง ผมแนะนำให้ลองอ่านแนวทางของ [hacks4pancakes](https://tisiphone.net/2015/08/18/giac-testing/) ถ้า scroll ลงไปล่างๆ จะมีลิงก์ไป blog ของคนอื่นด้วย

## My Exam Experience

ผมจองวันและสถานที่สอบผ่านหน้า portal ของ GIAC รูปแบบก็เหมือนการจองสอบกับศูนย์สอบ Pearson Vue ตามปกติ

วันสอบก็รู้สึกแปลกหน่อยๆ ที่แบกหนังสือไปด้วย เพราะเคยสอบแบบ open book ครั้งสุดท้ายน่าจะตอนเรียน ป.โท เมื่อซักเกือบ 20 ปีที่แล้ว (แก่ไปไหน) 😅

ตอนเริ่มสอบช่วงแรกในห้องสอบมีผมอยู่คนเดียว ก็ทำข้อสอบอย่างสบายใจ แต่ซักพักพอมีคนมานั่งข้างๆ ก็เริ่มรู้สึกเกรงใจหน่อยๆ เพราะเวลาเปิดหนังสือหาข้อมูล เสียงกระดาษมันจะดังพอสมควร แต่ก็ทำอะไรไม่ได้มาก... แค่พยายามเปิดหนังสือให้เบาที่สุด 🥺

ผมใช้เวลาสอบเกือบ 2 ชั่วโมงเต็ม พอตอบข้อสุดท้ายเสร็จ ระบบก็แจ้งผลสอบมาบนหน้าจอเลย ไม่ต้องรอลุ้นให้ proctor พรินท์ผลสอบแต่อย่างใด สรุปว่าสอบผ่าน ได้ GIAC Certification ใบแรกในชีวิต 🎉

อ้อ... แล้วก็เพิ่งรู้ว่า GIAC ไม่มี certificate แบบ PDF ให้ดาวน์โหลดด้วย มีแค่ badge ใน Credly กับ certificate กระดาษที่ขอได้ฟรี ไม่มีค่าจัดส่ง

## GRID Exam Tips

1. คะแนนสอบจริงของผมใกล้เคียงกับ Practice Test ทั้งสองรอบ แต่ไม่ได้หมายความว่าถ้าทำ Practice Test ไม่ผ่านแล้วจะสอบตก เพราะเท่าที่เห็นใน Reddit ก็มีคนที่สอบ Practice Test ไม่ผ่าน แต่ตอนสอบจริงผ่าน อยู่หลายคน
2. ผมไม่ได้ทำ index เอง แต่ใช้ index ที่อยู่ใน coursebook เล่มสุดท้าย สิ่งที่ทำคือติด tag ในหน้าที่มีหัวข้อที่คิดว่าสำคัญ เพื่อช่วยให้เปิดหาได้เร็วขึ้น ถ้าหาจาก tag ไม่เจอค่อยไปเปิด index
3. ถ้าเป็นการสอบแบบปกติที่ไม่ให้เปิดหนังสือ ผมน่าจะใช้เวลาซัก 1 ชั่วโมงก็จบ แต่พอเปิดหนังสือได้ก็ทำให้ถึงจะรู้คำตอบอยู่แล้ว ก็อยากเปิดดูซักหน่อยเพื่อความชัวร์ ทำให้เสียเวลาไปโดยไม่จำเป็นเยอะอยู่ 😆
