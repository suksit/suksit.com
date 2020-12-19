---
title: "Packtpub Notify"
date: 2017-11-07T23:33:03+07:00
tags: ["go", "packtpub", "line", "line-notify"]
---

ปกติทุกเช้าผมจะต้องเข้าไปที่[หน้าแจกหนังสือฟรีของ Packt](https://www.packtpub.com/packt/offers/free-learning/) เพื่อดูว่าหนังสือฟรีวันนี้น่าสนใจไหม ประมาณว่าถ้าเก่าเกินก็ไม่เอา หรือถ้าเป็นเรื่องที่คาดว่าไม่น่าจะอ่านอยู่แล้วก็ไม่กด 😒 (แจกฟรีแล้วยังจะหยิ่งเลือกโหลดอีก ฮ่าๆๆ)

พอดีช่วงนี้กำลังหัดเขียน[ภาษา Go](https://golang.org/) เลยอยากลองทำโปรแกรมง่ายๆ ที่มีประโยชน์ในชีวิตประจำวัน คิดไปคิดมาก็ออกมาเป็น [Packtpub Notify](https://github.com/suksit/packtpub-notify/) นี่แหละ คอนเซปต์ก็ไม่มีอะไร แค่อ่านหน้าเว็บของ Packt แล้วส่ง notification ด้วย [LINE Notify](https://notify-bot.line.me/en/) มาให้ผมทุกเช้า ว่าวันนี้มีหนังสืออะไร เป็นหน้าปก กับรายละเอียดนิดหน่อย ให้ตัดสินใจได้ว่าจะโหลดไหม 😆

<!--more-->

เพื่อให้ครบของที่กำลังเล่นก็เลยทำ Dockerfile พร้อมตั้ง cron tab สำหรับใช้ build image เพื่อเอาไปใช้ได้เลย&hellip; ส่วนหน้าตาผลลัพธ์ก็ประมาณนี้

![Packtpub Notify in Action](https://i.imgur.com/5SiEFl3.png)

ปล. เห็นใน Github มีสคริปต์ที่ช่วยโหลดหนังสือจาก Packt แบบอัตโนมัติ เช่น [packtpub-crawler](https://github.com/niqdev/packtpub-crawler/) หรือ [Free Learning PacktPublishing script](https://github.com/igbt6/Packt-Publishing-Free-Learning/) แต่เข้าไปอ่าน issues ของตัวแรกแล้วเหมือนตอนนี้จะใช้ไม่ได้ เพราะติด reCAPTCHA 😑 ส่วนตัวหลังจะไปเรียกใช้ service ของ [Anti Captcha](https://anti-captcha.com/) (เสียตังค์) แต่ถ้าแลกกับความสะดวกก็อาจจะโอเค 😕
