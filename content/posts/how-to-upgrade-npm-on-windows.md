---
title: "How to Upgrade npm on Windows"
date: 2018-04-06T12:02:13+07:00
tags: [ "nodejs", "npm" ]
---

ถ้าใครใช้ Node.js บนวินโดวส์ น่าจะเคยเจอข้อความที่บอกว่า npm เวอร์ชันที่คุณใช้มันเก่าแล้วนะ ให้อัพเกรดโดยใช้คำสั่ง `npm install -g npm` ซึ่งถ้าลองรันดูก็จะพบว่า… มันอัพเกรดไม่ได้ 🙄 ที่ตลกคือ ถึงจะอัพเกรด Node.js เป็นเวอร์ชันล่าสุด npm ตัวที่มากับแพ็กเกจก็ยังไม่ใช่เวอร์ชันล่าสุดอยู่ดี 😒

ลอง Google ดูก็พบว่ามีคนทำ tools ไว้ให้ชื่อ [npm-windows-upgrade](https://github.com/felixrieseberg/npm-windows-upgrade) ผมเคยลองใช้แล้วเวิร์กอยู่ แต่ล่าสุดมาลองอีกทีเมื่อประมาณเดือนที่แล้ว พบว่าใช้ไม่ได้ 😑 เดาว่าสาเหตุอาจจะเกิดจากตามที่เค้าเตือนไว้ในหน้า GitHub

> Chances are that you attempted to upgrade npm before, it somehow failed, and you then went looking for this tool. If the tool fails to upgrade, it may be troubled by partial changes done during npm install npm or npm upgrade npm.

<!--more-->

มานั่งๆ คิดดู แค่อัพเกรด Node module ทำไมดูชีวิตยากลำบาก เลยลองรัน `npm install -g npm` อีกครั้ง แล้วนั่งดู error message ของมัน ก็พบว่า ที่มันอัพเกรดไม่ได้ เพราะมีการใช้ไฟล์ `npm` หรือไฟล์ `npx` อยู่… เลยลองลบไฟล์ที่มันบ่นดู มั่วไปมั่วมาซักพักก็พบว่าสามารถอัพเกรด npm ได้!!! 😁 สรุปวิธีการก็ง่ายๆ ตามนี้

* เข้าไปที่โฟลเดอร์ที่ติดตั้ง Node.js
* ลบไฟล์ `npx`, `npx.cmd`
* เปลี่ยนชื่อไฟล์ `npm`, `npm.cmd` เป็นอย่างอื่น เช่น `npm1`, `npm1.cmd`
* รันคำสั่ง `npm1 install -g npm`
* ลบไฟล์ `npm1`, `npm1.cmd`

เราก็จะสามารถติดตั้ง npm เวอร์ชันล่าสุดได้ตามต้องการ 🎉
