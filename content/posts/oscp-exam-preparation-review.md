---
title: "OSCP Exam Preparation Review"
date: 2026-05-01T21:50:14+07:00
draft: false
toc: true
images:
tags:
  - rant
  - offsec certified professional
  - oscp
  - offsec
  - certification
  - penetration testing
  - cybersecurity
---

## Preface

บล็อกนี้จะเล่าถึงแนวทางการเตรียมตัวสอบ OSCP ของผม ถ้าต้องการอ่าน[ประสบการณ์การสอบ OSCP](/posts/oscp-certification-review) ดูได้ตามลิงก์ครับ

## PEN-200 Challenge Labs

Resource หลักที่ใช้ในการเตรียมตัวสอบ ก็คือคอร์ส PEN-200 ของ OffSec ผมเรียนแบบผ่านๆ เน้นเก็บโมดูลให้ครบ เพราะมีพื้นฐานมาแล้วจากการเรียน Penetration Tester Job Role Path ของ HTB และช่วงที่อบรม OSCP Boot Camp 5 วัน ก็เหมือนเป็นการทบทวนไปในตัวด้วย

สิ่งที่ผมคิดว่าสำคัญที่สุดในคอร์ส PEN-200 คือ Challenge Labs ทั้ง 11 แล็บ ที่ช่วยให้เห็นสไตล์การออกโจทย์ของ OffSec โดยเฉพาะ OSCP A, B, C ที่มีรูปแบบเหมือนการจำลองการสอบ OSCP ถ้าทำทั้ง 3 แล็บนี้ได้ภายในเวลา 24 ชั่วโมง ก็พอจะมั่นใจได้ในระดับนึงว่ามีโอกาสที่จะสอบผ่านสูง

ผมเล่น Challenge Labs ไปเกือบทั้งหมด ยกเว้น Skylark ที่คิดว่าน่าจะใหญ่เกินไป แล็บท้ายๆ พวก Poseidon, Feast, Laser อาจจะต้องใช้ความรู้/ทักษะนอก scope OSCP ไปเล็กน้อย แต่ผมว่าสามารถใช้ฝึกการทำ enumeration ในส่วน Active Directory ได้ดี

## Practice Machine List

แพลตฟอร์มอื่นๆ ที่ผมใช้ฝึกเพิ่มเติมนอกจาก Challenge Labs จะมีอยู่ 2 ที่ คือ Proving Grounds และ Hack Smarter โดยรายการเครื่องที่ผมเล่นจะมาจาก 2 แหล่งคือ

* OSCP Machine ที่ทางทีม Secure-D คัดเลือกมาจาก [NetSecFocus Trophy Room](https://docs.google.com/spreadsheets/u/1/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/htmlview) ของ TjNull อีกที
* [LainKusanagi list of OSCP like machines](https://docs.google.com/spreadsheets/d/18weuz_Eeynr6sXFQ87Cd5F0slOj9Z6rt/edit?gid=487240997#gid=487240997)

โดยผมเลือกเฉพาะเครื่องที่อยู่ใน Proving Grounds กับ Hack Smarter และไม่เล่นเครื่องที่อยู่ใน HTB เพราะรู้สึกว่าสไตล์โจทย์มันต่างจากของ OffSec 🤔

ทั้งสองลิสด์จะมีเครื่องที่ซ้ำกันอยู่พอสมควร รวมๆ แล้วผมน่าจะเล่นไปประมาณ 120 เครื่อง ในช่วงเวลา 90 วัน ก่อนสอบ

ประโยชน์จากการเล่นเครื่องพวกนี้ คือการสร้าง methodology ในการทดสอบเจาะระบบของตัวเอง และเรียนรู้ท่าใหม่ๆ ที่อาจจะไม่ได้มีสอนในคอร์ส PEN-200 รวมไปถึงฝึกความอดทนในการพยายามเจาะระบบ ที่อาจจะต้องใช้เวลาเครื่องละ 1-3 ชั่วโมง

โดยปกติถ้าเครื่องไหนใช้เวลาเกิน 2 ชั่วโมง ผมจะเปิด walkthrough ดูเป็น hint ว่าเค้าทำ enumeration ยังไง จุดไหนที่ผมพลาดไปและทำให้ติด แล้วหาทางไปต่อด้วยตัวเอง

ตอนเล่นเครื่องพวกนี้ช่วงแรกๆ ผมจะกังวลในการพยายามหาว่าต้องเริ่มจาก port ไหน ระบบไหนที่ต้องโจมตี และพยายามหา CVE number หรือ exploit อะไรทำนองนี้ เพื่อให้ได้ flag เร็วที่สุด จะได้ไปติ๊กใน list ว่าผ่านแล้ว และไปเล่นเครื่องต่อไป...

แต่ช่วงหลังๆ ที่เล่น ผมจะรู้สึกคล้ายๆ ว่าเป็นหุ่นยนต์ 🤖 ทำตาม methodology ไปตามลำดับ เพื่อรวบรวมข้อมูลเกี่ยวกับเครื่องนั้นๆ ให้ได้มากที่สุด ก่อนพยายามโจมตีจริงๆ และไม่ค่อยรู้สึกกังวลว่าจะเจาะเครื่องนี้ได้หรือไม่ได้อีกต่อไป ซึ่งไม่ได้แปลว่าผมเจาะระบบสำเร็จทุกครั้ง แต่เหมือน ยอมรับ/ปลงได้ กับความจริงที่ว่า

> Sometimes you don't know what you don't know.

## Mindset

สิ่งที่ผมคิดว่าสำคัญไม่น้อยกว่า knowledge และ technical skills คือ mindset ที่ควรจะมีตอนสอบ OSCP

วิธีสร้าง mindset ของผมคือการอ่าน success/failure story ของคนสอบ OSCP หลายๆ คน รวมถึง comment ในโพสต์นั้นๆ (ส่วนใหญ่จะมีคนมาเล่าใน [r/oscp](https://www.reddit.com/r/oscp/)) ถ้าเห็นคำเแนะนำอันไหนเข้าท่าก็จดไว้ เช่น

* OSCP is an enumeration exam
* Don't overthink it
* You are usually just 3-4 commands away to get the flag
* Take a lot of breaks
* The exam is basically OSCP D Challenge Lab
* ฯลฯ

อีกเรื่องที่เกี่ยวกับ mindset น่าจะเป็นเรื่องของความ "พร้อมที่จะสอบ" สำหรับผมเองรู้สึกว่าค่อนข้างตรงกับ quote นึงที่เห็นคนพูดบ่อยๆ [ตอนเตรียมตัวสอบ CISSP](/posts/cissp-exam-preparation-review)

> The strongest indicator for exam readiness is a change in mindset: boredom, frustration, and desire to see the exam whether pass or fail.

ถ้าอ่าน[โพสต์ก่อนหน้านี้](/posts/oscp-certification-review) จะเห็นว่าผมเลื่อนกำหนดการสอบเข้ามา เหตุผลหลักคือผมเริ่มรู้สึกว่า ถ้าไม่สอบซักที ก็จะไม่สามารถไป focus การทำงานอื่นๆ ต่อได้ เลยจองสอบให้มันรู้แล้วรู้รอดไป 😫

## Kali Setup

ผมติดตั้ง Kali Linux แบบ minimal ที่สุด คือมีเฉพาะ Desktop Environment แล้วค่อยติดตั้ง tools ที่จะใช้เพิ่มเติมทีหลังเอง และพยายามอัปเดตทั้ง OS และ tools ต่างๆ ให้เป็น version ล่าสุดอยู่เสมอ และทำ snapshot เก็บไว้เป็นระยะๆ เผื่อเกิด accident ระหว่างสอบจะได้ restore snapshot มาใช้ได้

## Recommended Tools

### [UV](https://github.com/astral-sh/uv)

เป็น tools โคตรเทพในการทำงานกับ Python 🤩 ดูตัวอย่างการใช้งานได้ที่[บล็อกของ 0xdf](https://0xdf.gitlab.io/cheatsheets/uv) ผมใช้ฟีเจอร์หลักๆ อยู่ 2 อย่าง คือ

* การติดตั้งและอัปเดต tools ที่พัฒนาด้วย Python เช่น NetExec, Impacket, BloodyAD, ฯลฯ
* การจัดการ dependency และการรัน exploit script ที่เขียนด้วย Python

### [RustHound-CE](https://github.com/g0h4n/RustHound-CE/)

เอาไว้ query ข้อมูลจาก Domain Controller เพื่อเอาไป import ใน BloodHound โดยปกติถ้ารัน SharpHound บนเครื่องเป้าหมายไม่ได้ ผมจะรัน RustHound บน Kali เป็นตัวเลือกที่สอง

### [Ligolo-NG](https://github.com/nicocha30/ligolo-ng)

เครื่องมือทำ pivoting ไว้ใช้ตอนเจาะระบบ Active Directory Set ทำให้สามารถเข้าถึงเครื่องที่อยู่ใน internal network ได้โดยไม่ต้องใช้ proxychains และใช้งานง่ายกว่า Chisel มากๆ 😍

### [fzf](https://github.com/junegunn/fzf)

เอาไว้ค้นหาคำสั่งที่เคยพิมพ์ไปแล้ว จริงๆ zsh ใน Kali ก็มี auto suggestion อยู่ แต่มันจะแนะนำแค่คำสั่งล่าสุดที่ใช้ ถ้าต้องการหาคำสั่งย้อนหลัง ผมว่า fzf ช่วยได้เยอะ สำหรับผมรู้สึกว่าเร็วกว่าไปเปิด cheatsheet พอสมควร 🙃

### [Sysreptor](https://github.com/Syslifters/sysreptor)

เอาไว้เขียน penetration testing report ด้วย Markdown พร้อมสร้าง PDF หน้าตาสวยงาม ใช้แล้วชีวิตดีกว่าการนั่งพิมพ์ใน Microsoft Word มากมาย มีทั้งเวอร์ชันที่รันแบบ local หรือ on cloud และมี [report design สำหรับ OffSec Exam](https://github.com/Syslifters/OffSec-Reporting) เตรียมไว้ให้เรียบร้อย

### [SiYuan](https://github.com/siyuan-note/siyuan)

เอาไว้จดโน้ตทั้งตอนเรียนและตอนทำแล็บ แต่ก่อนผมใช้ Obsidian อยู่พักใหญ่ แต่ตลอดเวลาที่ใช้รู้สึกว่ามันมีอะไรตะหงิดๆ บางอย่าง (ซึ่งก็อธิบายไม่ได้ว่าคืออะไร) เลยลองเปลี่ยนมาใช้ SiYuan รู้สึกว่าใช้แล้วคลิกกว่า Obsidian และรู้สึกสบายใจ เลยใช้ตัวนี้มาตลอด 😌

## Summary

ทั้งหมดที่เล่ามา ก็เป็นแนวทางการเตรียมตัวสอบ OSCP ที่ผมใช้ เผื่อจะเป็น guideline ให้กับคนที่กำลังจะสอบ OSCP แน่นอนว่าสุดท้ายแล้ว การหาแนวทางที่เหมาะกับตัวเองให้เจอ เป็นสิ่งที่สำคัญที่สุดครับ
