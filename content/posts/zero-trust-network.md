---
title: "Zero Trust Network"
date: 2018-07-11T20:30:09+07:00
tags: [ "cybersecurity", "zero trust network" ]
---

เมื่อวันก่อนอ่านเรื่อง "[What It Takes to Build a Zero Trust Network](https://www.csoonline.com/article/3287057/network-security/what-it-takes-to-build-a-zero-trust-network.html)" รู้สึกว่าเป็นแนวคิดที่น่าสนใจดี เลยขอจดไว้หน่อย

เค้าว่า "Zero Trust" เป็นคำที่คิดโดยบริษัท Forrester Research เมื่อประมาณปี 2010 โดยมีคอนเซปต์คร่าวๆ คือ อุปกรณ์ทุกอย่างในเน็ตเวิร์กจะถือว่าเชื่อถือไม่ได้ จนกว่าจะได้รับการยืนยันตัวตนของอุปกรณ์และผู้ใช้งาน โดยไม่สนใจว่าอุปกรณ์นั้นจะอยู่ที่ไหนในเน็ตเวิร์ก

> Trust is a dangerous vulnerability that can be exploited.
<cite>John Kindervag, field CTO at Palo Alto Networks</cite>

แปลว่าแนวคิดการแบ่งแยกเน็ตเวิร์กแบบเดิมๆ จะไม่มีอีกต่อไป เพราะตามแนวคิดนี้ทุกอย่างเชื่อถือไม่ได้ ไม่มี trusted netwok, trusted device, หรือ trusted people 😮
<!--more-->

> A security perimeter will still be around individual machines, but the idea of a privileged network sitting behind an enterprise perimeter has been obsoleted.
<cite>Charlie Gero, CTO of Enterprise and Advanced Projects Group at Akamai Technologies</cite>

เค้ายกตัวอย่าง [BeyondCorp](https://www.blog.google/products/google-cloud/preparing-for-a-beyondcorp-world-at-your-company/) ของ Google ซึ่งเป็น zero trust network รูปแบบหนึ่ง (ยังไม่ได้อ่าน จดไว้ก่อน) อ่านแล้วยังงงๆ คือไม่มีแม้แต่ VPN และ privileged network access ยังนึกภาพไม่ออกว่าการปฏิบัติงานจากข้างนอกจะทำยังไงบ้าง ไว้รู้มากกว่านี้จะมาอัพเดต 😅


> The trust you assign a user cannot be based on whether that user is attempting to access an enterprise application from inside your network perimeter or outside of it.  Instead access needs to be based on what you know about the user, what you know about their device and what is being accessed.
<cite>Tom Kemp, CEO of Centrify</cite>

ปัจจัยสำคัญสำหรับแนวคิดนี้คือการใช้ multi-factor authentication (MFA) ร่วมกับ user and entity behavioral analytics (UEBA) แต่สิ่งที่ขาดไม่ได้คือ visibility เพราะเราต้องเห็น "ทุกอย่าง" ในระบบ ไม่ว่าจะเป็นอุปกรณ์ แอพพลิเคชัน หรือผู้ใช้ ซึ่งถ้าจะทำตามแนวคิดนี้จริงๆ น่าจะต้องยกเครื่อง/เปลี่ยนแนวคิดการทำ asset/inventory management ทั้งหมดกันก่อน 😕

つづく
