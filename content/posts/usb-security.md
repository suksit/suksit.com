---
title: "USB Security"
date: 2018-07-22T20:33:25+07:00
tags: [ "cybersecurity", "usb", "usb sanitizer", "sheep dip pc", "hid" ]
---

วันนี้ได้ความรู้ใหม่เกี่ยวกับ USB Security จากกระทู้ใน SANS ICS Community มาประมาณนี้

**กรณีที่ไม่ต้องใช้ USB**

* รัน regedit แล้วไปที่ `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\USBSTOR` สร้าง `REG_DWORD` value ชื่อ `Start` แล้วใส่ค่าเป็น `4`
* disable USB port ใน BIOS และใส่พาสเวิร์ดใน BIOS ด้วย เพื่อป้องกันการแก้ไข
* ถ้าจะให้ชัวร์ก็ทำลาย port USB ไปเลย เค้าบอกว่าพวกอุปกรณ์ที่ใช้ lock port บางทีก็แกะได้ง่ายๆ ด้วย swiss army knife

**กรณีที่ยังต้องใช้ USB อยู่**

* ใช้ [sheep dip PC](https://en.wikipedia.org/wiki/Sheep_dip_(computing)) หรือ clean kiosk แสกน USB drive ก่อนนำไปใช้ในระบบ (เพิ่งเคยได้ยินคำว่า sheep dip PC ก็วันนี้ 😅) เครื่องพวกนี้ปกติจะไม่ต่อเน็ตเวิร์ก และมีโปรแกรม antivirus มากกว่าหนึ่งยี่ห้อ เพื่อสแกนไฟล์ใน USB drive
* ใช้วิธี transfer ข้อมูลจาก untrusted USB drive มาใส่ใน trusted USB drive ก่อนเอาไปใช้ในระบบ (USB sanitizer) ลอง google ดูพบว่ามี solution แบบ open source ที่น่าสนใจคือ [CIRCLean](https://github.com/CIRCL/Circlean)
* solution แบบไม่ฟรี แต่คิดว่าคอนเซปต์น่าจะคล้ายๆ กันคือ [ODIX](https://odi-x.com/) ในหน้าเว็บเค้าเรียกว่า Content Disarm & Reconstruction แต่อ่านคำอธิบายแล้วเหมือนเอา sheep dip PC กับ USB sanitizer มารวมกัน

<!--more-->

**อุปกรณ์ USB อื่นๆ**  
เอาจริงๆ แล้วเวลาพูดว่า USB มันไม่ได้จำกัดอยู่แค่ USB drive เท่านั้น แต่ต้องคำนึงถึงอุปกรณ์ประเภท HID (Human Interface Device) อื่นๆ ด้วย เช่น เมาส์ คีย์บอร์ด รวมทั้งพวก gadget ต่างๆ ที่ต้องเสียบ port USB เพื่อใช้งาน อุปกรณ์พวกนี้สามารถใช้เป็นช่องทางในการโจมตีได้หมด เจอวิดีโอน่าสนใจตัวนึง เห็นเค้าเกริ่นว่าช่วงหลังจะบอกวิธีป้องกันด้วย ยังไม่ได้ดูแต่ขอแปะไว้ก่อน 😆

<div style="margin: 3rem 0;">
  {{<youtube id="ADqMCKtufNY" autoplay="false">}}
</div>
