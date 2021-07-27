---
title: "How to Run Windows Update with PowerShell"
date: 2021-07-27T07:39:58+07:00
toc: false
images:
tags: [ "windows", "powershell", "windows update" ]
---

เนื่องจากช่วงนี้ WFH แบบ 100% และ VPN client ของที่ทำงานกำหนดว่าต้องลง antivirus และต้องอัปเดต signature ล่าสุดเสมอ ถึงจะอนุญาตให้เข้าถึงเครือข่ายภายในได้

โดยส่วนตัว ผมไม่ได้ใช้ 3<sup>rd</sup> party antivirus มาพักใหญ่ๆ แล้ว ([สาเหตุ](/posts/red-x-blue-pill-2019/#breaking-scada-and-anti-virus-for-fun--profit) 😅) ดังนั้น antivirus ที่ใช้งานอยู่ในเครื่องก็คือ Microsoft Defender ที่ติดมากับ Windows 10 นี่แหละ

ทำให้ทุกครั้งก่อนที่ผมจะต่อ VPN ต้องไปที่ Settings > Update & Security แล้วก็กด Check for updates ซึ่งพอต้องทำบ่อยๆ เข้าก็รู้สึกว่ามันเสียเวลา น่าจะมีวิธีแบบกดคลิกเดียวแล้วให้วินโดวส์ check และ install update อัตโนมัติ 😑 พอลอง Google ดูก็พบว่า PowerShell มันทำสิ่งนี้ได้ โดยใช้โมดูล [PSWindowsUpdate](https://www.powershellgallery.com/packages/PSWindowsUpdate/) 

วิธีการติดตั้ง ก็รันคำสั่งนี้ใน Elevated PowerShell (run as Administrator)

```powershell
Install-Module -Name PSWindowsUpdate
```

ส่วนวิธีใช้งานหาได้ทั่วไปจาก Google แต่สิ่งที่ต้องงมอยู่นานนน คือต้องใช้ option อะไรเพื่อจะ**ติดตั้งเฉพาะ patch ของ Microsoft Defender** (เพราะถ้าเป็น update อื่นๆ ผมอยากจะอ่านก่อนว่ามันคืออะไร และไม่ใช่เงื่อนไขจำเป็นในการต่อ VPN) หาไปหามาเกือบชั่วโมง ก็พบว่าอ่าน help ของมันเองได้ข้อมูลครบสุด 🤣 โดยใช้คำสั่ง

```powershell
Get-Help Get-WindowsUpdate -Full
```

ลองเล่นอยู่ซักพักก็พบว่าคำสั่งที่ต้องการคือ

```powershell
Get-WindowsUpdate -Install -WindowsUpdate -Category 'Definition Updates' -AcceptAll
```

ที่เหลือก็แค่สร้าง batch file ที่จะรันคำสั่งข้างบน อันนี้ผมใช้ [PowerShell](https://github.com/PowerShell/PowerShell) ตัวใหม่ ถ้าหากใครใช้ Windows PowerShell ธรรมดา ก็เปลี่ยน `pwsh` เป็น `powershell` แทน 🙃

```cmd
@echo off
pwsh -ExecutionPolicy bypass -NoProfile -Command "& Get-WindowsUpdate -Verbose -Install -WindowsUpdate -Category 'Definition Updates' -AcceptAll"
pause
```
