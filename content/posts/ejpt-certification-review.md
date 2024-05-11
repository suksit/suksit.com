---
title: "eJPT Certification Review"
date: 2024-05-01T19:59:16+07:00
draft: false
toc: false
images:
tags:
  - ejpt
  - junior penetration tester
  - certification
  - ine
  - rant
---

วันนี้เพิ่งสอบผ่าน [eJPT Certification](https://security.ine.com/certifications/ejpt-certification/) ของ INE เลยมาบันทึกประสบการณ์ไว้กันลืม

<div align="center">
  <a href="https://certs.ine.com/843e15e9-e284-472b-830b-71ed44616ee6" target="_blank">
    <img src="https://api.accredible.com/v1/frontend/credential_website_embed_image/badge/102719315" alt="eJPT Badge" title="eJPT Badge">
  </a>
</div>

## Overview

eJPT (Junior Penetration Tester) เป็น certification ระดับเริ่มต้นของคนที่ทำงานด้านการทดสอบเจาะระบบ หรือ penetration testing มีเนื้อหาครอบคลุมหัวข้อต่อไปนี้

* Assessment Methodologies (25%)
* Host and Networking Auditing (25%)
* Host and Network Penetration Testing (35%)
* Web Application Penetration Testing (15%)

การสอบจะเป็น hands-on exam แบบออนไลน์ โดยจำลองการทดสอบเจาะระบบของบริษัทสมมติแห่งหนึ่งภายในเวลา 48 ชั่วโมง ลักษณะข้อสอบจะเป็นแบบ multiple choice questions ผสมกับ capture the flag (นิดเดียว) สอบเสร็จแล้วรู้ผลเลย ไม่ต้องเขียนรายงานส่ง และไม่มีคนคุมสอบ (proctor)

## Course Content

ไม่ขอรีวิวคอร์ส เพราะผมเรียนไปได้นิดเดียว รู้สึกว่าเนื้อหาแน่นดี แต่อารมณ์เหมือนนั่งอ่าน PowerPoint 😅 สรุปว่าไม่ได้เรียนจนจบ แต่ดอง exam voucher ไว้จนมันจะหมดอายุในอีก 15 วัน เลยตัดสินใจสอบ 555+

## Certification Exam

การลงทะเบียนสอบง่ายมาก กดปุ่มเดียวแล้วรอระบบโหลดซักพัก ก็เข้าไปสอบได้ทันที รูปแบบการสอบจะต้องใช้ Kali VM ที่ระบบเตรียมไว้ให้ ไม่สามารถโหลด tools เพิ่มเติมได้

ผมใช้เวลาสอบประมาณ 10 ชั่วโมง โดยเริ่มตั้งแต่ประมาณ 9 โมงเช้า สอบเสร็จตอน 1 ทุ่มกว่าๆ รวมเวลากินอาหารกลางวันและอาหารเย็น

คำแนะนำในการสอบ: ถ้าไม่รู้จะเริ่มต้นยังไง ให้ลองอ่านคำถามแต่ละข้อ อาจจะได้ไอเดียว่าควรทำยังไงถึงจะได้คำตอบ

ลักษณะคำถามจะไม่ได้เรียงตั้งแต่ต้นจนจบ อาจจะลองไล่ดูคำถามเร็วๆ จะช่วยให้เห็นภาพรวมของ network และเครื่อง server ที่เราต้องทดสอบเจาะระบบได้ชัดเจนขึ้น

## Additional Notes

แน่นอนว่าสิ่งที่ทำให้รอดมาได้คือบุญเก่าจากการเล่น TryHackMe อีกตามเคย 🙏

รู้สึกว่าการสอบจะเน้นให้ใช้ Metasploit พอสมควร ถ้าใช้จนคล่องก็น่าจะไปได้เร็ว ส่วนผมก็งมๆ มึนๆ อาศัยหาจาก Google เอาเวลาต้องการทำอะไร 😔

สิ่งที่ได้จากการสอบคือ ได้ reflect ตัวเองว่า methodology ยังไม่นิ่ง, การใช้ tools ยังไม่คล่อง, และการ think like a hacker ยังไม่ครอบคลุมเท่าที่ควรจะเป็น และทำให้รู้ว่ายังไม่พร้อมจะสอบในระดับ OSCP จริงๆ แต่ก็มีกำลังใจขึ้นมาหน่อยว่าอย่างน้อยก็พอมีทักษะในระดับเบื้องต้นนะ 555+ 🤣

ปล. eJPT Certification มีอายุแค่ 3 ปี คิดไว้แล้วว่าถ้าหมดอายุก็คงไม่สอบใหม่ 👋
