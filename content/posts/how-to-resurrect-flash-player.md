---
title: "How to Resurrect Flash Player"
date: 2021-01-23T08:34:44+07:00
toc: false
images:
tags: [ "flash", "adobe", "cybersecurity" ]
---

เมื่อวันที่ 12 ม.ค. 64 เป็นวันที่ Adobe เริ่ม block ไม่ให้ Flash Player ทำงาน ซึ่งก็เป็นเรื่องที่ดีมากๆ เมื่อมองในแง่ Cybersecurity แต่&hellip; มันดันมี Cybersecurity Tool บางเจ้าในที่ทำงานผม ที่ใช้ Flash ในหน้า admin!!! ซึ่งก็แน่นอนว่าทำให้หลังจากวันที่ 12 จะเปิดหน้า admin เข้าไปตั้งค่าอะไรไม่ได้เลย 🙄

เดือดร้อนต้องหาวิธีทำให้ Flash Player กลับมาใช้ได้ในระหว่างที่รอ solution ระยะยาวจาก vendor

ลอง Google ดูก็พบว่ามันมีสิ่งที่เรียกว่า "Enterprise Enablement" เขียนไว้เป็นเรื่องเป็นราวใน section แรกของหัวข้อ Administration ในเอกสาร [Adobe Flash Player Administration Guide](https://www.adobe.com/devnet/flashplayer/articles/flash_player_admin_guide.html) อารมณ์ประมาณว่าถ้าองค์กรยังไม่พร้อมจะหักดิบเลิกใช้ Flash เราก็มีวิธี enable มันกลับขึ้นมาใหม่ให้ 🎉

แต่ถ้าอ่านเอกสารแล้วดูยืดเยื้อ แค่ทำตาม[โพสต์นี้](https://community.adobe.com/t5/flash-player/flash-player-stops-working-after-12-jan-2021/m-p/11747456?page=1#M210670)ก็ใช้ Flash ต่อได้ทันที สรุปสาระสำคัญคือ

### ใช้ Browser ที่รองรับ Flash Player

* Firefox ESR 78 (remains supported until October 2021)
* IE11 (as long as you don't install the Microsoft update which removes Flash. This update will be mandatory in Summer 2021)

### แก้ไขไฟล์ `C:\Windows\SysWOW64\Macromed\Flash\mms.cfg`

```
EOLUninstallDisable=1
SilentAutoUpdateEnable=0
AutoUpdateDisable=1
EnableAllowList=1
AllowListUrlPattern=https://server_ip_or_url/
AllowListUrlPattern=https://server_ip_or_url/
```

เท่านี้ก็จะสามารถใช้งาน Flash ต่อไปได้อีกสักพักใหญ่ๆ แต่ทางที่ดีก็ควรหา solution ใหม่ หรืออัพเกรดระบบให้เป็นเวอร์ชันที่ไม่จำเป็นต้องใช้ Flash อีกต่อไป 🙃
