---
title: "Achievement Unlocked - BOF"
date: 2022-03-28T22:31:33+07:00
toc: false
images:
tags:
  - rant
  - cybersecurity
  - tryhackme
  - buffer-overflow
---

เพิ่งเล่นห้อง [Buffer Overflow Prep](https://tryhackme.com/room/bufferoverflowprep) ใน TryHackMe จบ รู้สึกเป็น milestone สำคัญในการเรียนรู้ด้าน cybersecurity ของตัวเองอีกหนึ่งอย่าง

โดยส่วนตัวมีความไม่ถูกกับโค้ด Assembly และ memory stack มาแต่ไหนแต่ไร เห็นทีไรตาลายทุกที 😅 ยิ่งเวลาเล่น CTF ถ้าเจอโจทย์ประเภท pwn หรือ reverse engineering นี่แทบจะไม่แตะเลย

จนมาเรียน Offensive Pentesting Path ใน TryHackMe ก็พบว่ามันมี module นึงที่เป็นเรื่อง buffer overflow (BOF) ล้วนๆ อยู่ 4 ห้อง ผมก็ข้ามไปเล่น module อื่นก่อนจนหมด แต่ยังไงถ้าอยากจบ learning path นี้ก็ต้องเรียนเรื่อง BOF อยู่ดี เลยกัดฟันลองทำโจทย์ดู 😑

ครั้งแรกพบว่าทำตาม instruction ที่เค้าบอกแทบไม่ได้เลย เหมือนไม่เก็ต (หรือเพราะจิตใต้สำนึกตั้งท่าไว้แล้วว่ามันต้องยากก็ไม่รู้) เลยหยุดไปพักใหญ่ๆ (นานอยู่ น่าจะเกือบเดือน)

จนไปเห็นโพสต์นึงใน Reddit ที่แนะนำว่าเรื่อง BOF ดู YouTube 13 นาทีก็ทำได้แล้ว ก็เลยตามไปดูวิดีโอ [Buffer Overflow for the OSCP Exam](https://www.youtube.com/watch?v=kWPN0gc8NS0) ของ Andy Li ก็พบว่าเออมันดูง่ายจริงๆ แฮะ แค่ทำตาม step ก็จบ 😲

บวกกับที่ดูวิดีโอของใครซักคน (จำไม่ได้ว่า John Hammond หรือ The Cyber Mentor) แต่เค้าพูดประมาณว่า การทำ basic buffer overflow ก็คือการทำตาม methodology ที่เค้าออกแบบมาดีแล้วนั่นแหละ ทำตามนี้ได้ชัวร์ อะไรทำนองนี้

เลยเหมือนได้เปลี่ยน mindset ใหม่ และไปลองเล่นห้อง Buffer Overflow Prep อีกครั้ง คราวนี้พบว่าค่อยๆ ทำไปได้เรื่อยๆ และมีความเข้าใจ/มั่นใจในกระบวนการมากขึ้น จนเล่นได้จบทั้ง 4 ห้องใน module นั้น

สรุปว่าได้สกิลเพิ่มมาอีกหนึ่งอย่าง 🎉 และเป็นการยืนยันในสิ่งที่ผมชอบในการทำงานด้าน cybersecurity ก็คือ มันมีเรื่องให้เรียนรู้ได้ตลอดเวลา ในหลายแง่มุม โดยมีทั้งส่วนที่เป็นเนื้อหาและการลงมือทำนี่แหละ 🙃
