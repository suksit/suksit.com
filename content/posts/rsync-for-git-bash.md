---
title: "rsync for Git bash"
date: 2017-07-23T22:50:17+07:00
tags: [ "git", "bash", "rsync", "windows", "msys2" ]
---

ด้วยความที่เป็น developer สายวินโดวส์ (ไม่มีตังค์ซื้อ Mac 😂) ผมเลยต้องติดตั้ง Cygwin ไว้ตลอดเพราะต้องการใช้ bash และ tools ต่างๆ ของลินุกซ์ แต่พบว่าบางทีมันจะมีปัญหาเรื่องพาธของไฟล์เวลาใช้ tools ที่เป็น Windows Native ใน bash ของ Cygwin เช่นพวก git, composer, node, npm, php, ฯลฯ

ช่วงหลังๆ เลยหันมาใช้ bash ใน Git for Windows อย่างเดียว ก็รู้สึกว่าพอใช้แทน Cygwin ได้ แต่วันนี้เพิ่งรู้ว่า มันไม่มี rsync ให้ใช้ 😕

Google หาข้อมูลอยู่เป็นชั่วโมง ก็พบ[วิธีติดตั้ง rsync เพิ่มให้ Git bash](https://groups.google.com/forum/#!topic/git-for-windows/p4DWwAV_aJ0) อาจจะดูยุ่งยากเล็กน้อย แต่ก็ได้ผลตรงตามจุดมุ่งหมาย เลยขอจดไว้หน่อย

<!--more-->

- ติดตั้ง [MSYS2](http://www.msys2.org/) โดยเลือกลงไว้ในไดเร็กทอรีที่เข้าถึงได้ง่าย หรือจะใช้ path default ของมันเลยก็ได้ (C:\msys64)
- เปิด shell ของ MSYS2 ขึ้นมา แล้วรันคำสั่ง `pacman -S rsync` เพื่อติดตั้งแพ็กเกจ rsync เสร็จแล้วปิดหน้าต่างไปได้เลย
- copy ไฟล์ rsync.exe จากไดเร็กทอรี {PATH_TO_MSYS2}\usr\bin\rsync.exe มาใส่ไว้ในไดเร็กทอรี {PATH_TO_GIT_FOR_WINDOWS}\mingw64\bin
- uninstall MSYS2 หรือจะเก็บไว้ก็ได้ ตามสะดวก
- เปิด Git bash หน้าต่างใหม่ขึ้นมา ตอนนี้คำสั่ง `rsync` ควรจะใช้งานได้แล้ว

ปล. ถ้าอ่านในลิงก์มันจะบอกว่าให้ย้ายจาก Git bash มาใช้ MSYS2 ไปเลย แต่ด้วยความที่ไม่ชอบติดตั้งอะไรโดยไม่จำเป็น เลยได้ออกมาเป็นวิธีการของตัวเองแบบข้างบน 😆
