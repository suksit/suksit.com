---
title: "GCIP Certification Review"
date: 2025-12-26T09:19:35+07:00
draft: false
toc: false
images:
tags:
  - sans
  - ics456
  - nerc cip
  - certification
  - giac
  - gcip
  - giac critical infrastructure protection
  - rant
---

ผมผ่านการสอบ [GIAC Critical Infrastructure Protection (GCIP)](https://www.giac.org/certifications/critical-infrastructure-protection-gcip/) certification เมื่อวันคริสต์มาสที่ผ่านมา (25 ธ.ค. 68) เป็นการสอบแบบ open book ที่รู้สึกว่ายากมาก 😵 เลยมาบันทึกประสบการณ์เก็บไว้เป็นที่ระทึก

<div style="text-align: center; margin-bottom: -1.5em;">
  <div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="b7a34231-eb41-4eae-a8da-5a4925b13f4d" data-share-badge-host="https://www.credly.com"></div><script type="text/javascript" async src="//cdn.credly.com/assets/utilities/embed.js"></script>
</div>

## Overview

GCIP เป็น certification สำหรับผู้ที่ต้องดำเนินการตามมาตรฐาน NERC CIP เพื่อให้มีความเข้าใจใน requirements ต่างๆ ของมาตรฐาน รวมถึงแนวทางการ implement NERC CIP แบบ practical โดยความรู้ที่ใช้ในการสอบจะมาจากหลักสูตร [ICS456: Essentials for NERC Critical Infrastructure Protection](https://www.sans.org/cyber-security-courses/essentials-for-nerc-critical-infrastructure-protection) ของ SANS Institute

## Course Content

เนื้อหาในหลักสูตร ICS456 ของ SANS จะอธิบายเกี่ยวกับ cybersecurity regulation ในบริบทของระบบไฟฟ้าใน North America โดยไล่ตั้งแต่โครงสร้างการกำกับดูแล (FERC, NERC, etc.), ประวัติความเป็นมาของ NERC CIP, กระบวนการร่างมาตรฐานของ NERC, รายละเอียด requirements ของมาตรฐาน CIP แต่ละเล่ม และแนวทางการ implement (people, process, technology) รวมไปถึงกระบวนการ audit และบทปรับเมื่อเกิด violation แน่นอนว่ายังคงคอนเซปต์ "drinking from a fire hose" อยู่เหมือนเดิม 😱

ICS456 จะแบ่งเนื้อหาออกเป็น 5 section เรียงตามนี้

1. Asset Identification and Governance
2. Access Control and Monitoring
3. Systems Management
4. Information Protection and Response
5. CIP Processes

สิ่งที่ผมชอบคือ SANS ไม่ได้สอนมาตรฐาน NERC CIP โดยไล่ไปตั้งแต่ CIP-002 ถึง CIP-014 แบบทื่อๆ แต่เค้าสอนโดยใช้หลักการ defense in depth ให้เห็นภาพรวมของการบริหารจัดการด้าน cybersecurity ทั้งหมดภายในองค์กร โดยจัดกลุ่มแต่ละ CIP ที่เกี่ยวข้องหรือเชื่อมโยงกันมาไว้ใน section เดียวกัน

ในแต่ละ section จะมีเนื้อหาการเรียนเป็น slide พร้อมคำบรรยายแบบละเอียด(มากกกกก) ปิดท้ายแต่ละ section ด้วยการทำ lab เพื่อให้เข้าใจแนวทางการ implement NERC CIP แบบลงมือทำ

คอร์สนี้ผมเรียนแบบ on-site ในระยะเวลา 5 วัน ผู้สอนหลักคือ Tim Conway&hellip; รู้สึกประทับใจใน energy / passion / knowledge ของเค้ามาก ทำให้รู้สึกคุ้มค่าและสนุกกับการเรียนตลอด 5 วัน 🙏

คำถามที่ผมถามในห้อง ส่วนใหญ่จะไม่ค่อยเกี่ยวกับเนื้อหาที่สอน แต่เป็นเรื่องของระบบที่ดูแลอยู่ ว่าถ้าเป็นแบบนี้ควร implement หรือตีความยังไงดี หรือถ้าจะทำแบบนี้เพียงพอและเหมาะสมไหม ซึ่ง Tim ก็ตอบทุกคำถาม ทำให้ได้ความรู้และแนวทางการเอาสิ่งที่เรียนไปต่อยอด / ปรับปรุงจากสิ่งที่กำลังทำอยู่ ได้เยอะมาก 🤩

## Exam Overview

ถ้าซื้อ GCIP Certification Exam จะมี Practice Test ติดมาให้ด้วย 2 ชุด ข้อสอบจะเป็นแบบ multiple choice questions (MCQ) จำนวน 75 ข้อ ให้เวลาทำ 3 ชั่วโมง การสอบจะเป็นแบบ open book คือสามารถเอาหนังสือหรือโน๊ตเข้าไปในห้องสอบได้ด้วย คะแนนขั้นต่ำที่ถือว่าสอบผ่านคือ 70%

แนวทางเตรียมตัวสอบที่เค้าแนะนำกันคือให้ทำ index และ highlight ข้อความสำคัญใน coursebook เพื่อให้หาหัวข้อที่เกี่ยวข้องได้สะดวกและรวดเร็ว ถ้าลอง google ดูก็จะเจอหลายแนวทาง ผมแนะนำให้ลองอ่านแนวทางของ [hacks4pancakes](https://tisiphone.net/2015/08/18/giac-testing/) เช่นเคย

## My Exam Experience

ผมจองวันและสถานที่สอบผ่านหน้า portal ของ GIAC รูปแบบก็เหมือนการจองสอบกับศูนย์สอบ Pearson VUE ตามปกติ

วันสอบแบกหนังสือไปทั้งหมด 6 เล่ม คือ coursebook 5 เล่ม และ NERC CIP Active Standards อีกเล่มนึง

พอเริ่มทำข้อสอบไปได้ 2-3 ข้อ ก็นึกในใจว่า "ทำไมมันยากว่า practice test ขนาดนี้ฟระ!" สรุปว่าตลอดการสอบ ผมต้องเปิดหนังสือดูเกือบทุกข้อ อันที่อ่านโจทย์แล้วตอบได้เลยมีน้อยมาก (น่าจะไม่เกิน 10 ข้อ)

ผมใช้เวลาสอบเกือบ 3 ชั่วโมงเต็ม โดยเหลือเวลาประมาณ 10 นาที พอตอบข้อสุดท้ายเสร็จ ระบบก็แจ้งผลสอบมาบนหน้าจอเลย ไม่ต้องรอลุ้นให้ proctor พรินท์ผลสอบแต่อย่างใด สรุปว่าสอบผ่าน ได้ GIAC Certification ใบที่สองมาครอบครองต่อจาก [GRID](/posts/grid-certification-review/) 🎉

## GCIP Exam Tips

1. ผมรู้สึกตั้งแต่ตอนทำ Practice Test ทั้ง 2 ชุด ว่าข้อสอบ GCIP เป็นข้อสอบที่แปลกกว่าข้อสอบ certification ด้านไซเบอร์อื่นๆ ที่เคยสอบมา เข้าใจว่าน่าจะเพราะเป็นการทดสอบ "ความรู้ความเข้าใจเกี่ยวกับมาตรฐาน" ไม่ใช่ทดสอบ "ความรู้ความเข้าใจด้านไซเบอร์" อย่างที่ตัวเองคุ้นเคย 😑
2. ถ้าอ่านโจทย์แล้วไม่รู้ว่าควรไปเปิดเล่มไหน หัวข้อไหน หรือหาใน index แล้วไม่เจอ แนะนำให้กด Skip ข้อนั้นไปก่อน แล้วค่อยย้อนกลับมาทำ เพื่อไม่ให้เสียเวลามากเกินไป (ในการสอบอนุญาตให้ Skip ได้ทั้งหมด 10 ข้อ)
3. ฝึกบริหารเวลาให้ดี เพราะตอนทำ Practice Test ผมใช้เวลาประมาณ 2 ชั่วโมงนิดๆ แต่ตอนสอบจริงผมใช้เวลาจนเกือบหมด ส่วนน้องที่ทำงานอีกคนตอนทำ Practice Test ใช้เวลาเกือบ 3 ชั่วโมง ตอนสอบจริงคือทำไม่ทัน เลยต้องเดาไปหลายข้ออยู่ (แต่สอบผ่านเหมือนกัน) 🥹
4. CIP เป็นมาตรฐานที่ค่อนข้างเฉพาะทาง คือแต่ละ requirements จะมีเงื่อนไขกำกับอยู่ว่า บังคับใช้กับระบบแบบไหน ซึ่งข้อสอบส่วนใหญ่ก็จะทดสอบความเข้าใจเกี่ยวกับเรื่องนี้ ถ้าถามผมว่า CIP ไหนสำคัญที่สุด ก็น่าจะเป็น CIP-002 ที่เป็นพื้นฐานในการตีความและ implement มาตรฐาน CIP อื่นๆ ทั้งหมด