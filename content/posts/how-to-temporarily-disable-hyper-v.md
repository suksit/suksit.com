---
title: "How to Temporarily Disable Hyper V"
date: 2018-11-25T16:36:06+07:00
tags: ["windows", "hyper-v", "bcdedit"]
---

เมื่อวันก่อนพยายามจะลองเล่น [Ragnarok Eternal Love](https://www.ragnaroketernallove.com/) บนพีซี โดยให้มันรันบน Android Emulator แต่ปรากฏว่า emulator ที่รู้จักเกือบทุกตัวไม่รองรับ Hyper-V ซึ่งผมเปิดใช้งานเป็น default ไว้ เพราะต้องใช้ Docker ในการทำงาน

ลอง Google ดูก็ไปเจอ[บล็อกของ Scott Hanselman](https://www.hanselman.com/blog/SwitchEasilyBetweenVirtualBoxAndHyperVWithABCDEditBootEntryInWindows81.aspx) บอกว่าเราสามารถใส่ option ตอนบูตเครื่องได้ว่าจะเปิดใช้ Hyper-V หรือเปล่า ซึ่งวิธีที่ง่ายสุดคือการสร้าง boot entry ใหม่ใน BCD สำหรับบูตวินโดวส์แบบไม่เปิดฟีเจอร์ Hyper-V

วิธีทำก็เริ่มจากเปิด Command Prompt แบบ Run as administrator แล้วพิมพ์คำสั่งตามนี้

<!--more-->

```dos
C:\>bcdedit /copy {current} /d "No Hyper-V"
The entry was successfully copied to {xx-yy-zzz-aaaa-bbbbbbbb}.

C:\>bcdedit /set {xx-yy-zzz-aaaa-bbbbbbbb} hypervisorlaunchtype off
The operation completed successfully.
```

ส่วนการเข้าโหมด No Hyper-V สามารถเลือกได้จากเมนูตอนเปิดเครื่อง หรือถ้ากำลังใช้งานวินโดวส์อยู่ ให้กดปุ่ม Shift ค้างไว้แล้วเลือกเมนู Restart เพื่อรีบูตเข้า Advanced startup จากนั้นเลือก Use another operating system แล้วเลือก No Hyper-V ก็จะเป็นการบูตเข้าวินโดวส์แบบไม่เปิดฟีเจอร์ Hyper-V ตามที่เราต้องการ 🙂
