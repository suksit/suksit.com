---
title: "STH Mini Web CTF 2025 #1"
date: 2025-04-05T19:20:00+07:00
draft: false
toc: true
images:
tags:
  - ctf
  - write-up
  - rant
---
## Introduction

ได้เห็น[โพสต์ของสยามถนัดแฮก (STH)](https://www.facebook.com/share/p/1ARZdYRh9c/) ใน Facebook ว่ามีการจัดแข่ง Mini CTF โดยให้หา flag 2 อัน จากเว็บ https://web1.ctf.p7z.pw แล้วเขียน write-up ลงบล็อกสาธารณะ เพื่อชิง Grab Food (E-Voucher) มูลค่า 500 บาท และ**ของที่ระลึกสุดพิเศษจาก HackTheBox** <span style="color:gray;"><-- สนใจอันนี้ เลยขอเล่นด้วยคน ในประเภทบุคคลทั่วไป</span> 😆

ที่รู้สึกแปลกๆ หน่อย ก็คือการให้เขียนลงบล็อกสาธารณะ แปลว่าคนที่ส่งหลังๆ ก็สามารถลอกของคนที่ส่งก่อนได้เลย 🤪 (ตอนที่เขียน write-up นี้ ผม google เจอประมาณ 3-4 บล็อก) แต่ถือว่าร่วมสนุกขำๆ ไปละกัน

## Website

เมื่อเข้าไปที่ URL https://web1.ctf.p7z.pw จะพบหน้าล็อกอินของ Scammer Gang Portal

<div align="center">

![Scammer Gang Portal Login](/img/sth-mini-web-ctf-2025-1/image-1.png)

</div>

### Weak/Default Credentials Testing

เมื่อลองใส่ weak credentials เช่น `admin:admin` และ `admin:P@ssw0rd` พบว่าไม่สามารถล็อกอินได้ และมี error message ว่า "Invalid username or password."

<div align="center">

![Login Error Message](/img/sth-mini-web-ctf-2025-1/image-2.png)

</div>

### Directory Brute Force
เมื่อลอง brute force directory ด้วย Gobuster เจอพาธที่น่าสนใจคือ `/admin.php` ที่โดน redirect กลับมาที่หน้าล็อกอิน

```shell-session
$ gobuster dir -u https://web1.ctf.p7z.pw/ -w /usr/share/seclists/Discovery/Web-Content/common.txt       
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     https://web1.ctf.p7z.pw/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/seclists/Discovery/Web-Content/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.hta                 (Status: 403) [Size: 1084]
/.htpasswd            (Status: 403) [Size: 1084]
/.htaccess            (Status: 403) [Size: 1084]
/.well-known/http-opportunistic (Status: 200) [Size: 26]
/Thumbs.db            (Status: 403) [Size: 1084]
/admin.php            (Status: 302) [Size: 0] [--> index.php]
/index.php            (Status: 200) [Size: 3775]
/thumbs.db            (Status: 403) [Size: 1084]
Progress: 4744 / 4745 (99.98%)
===============================================================
Finished
===============================================================
```

### View Page Source

เมื่อลองใช้ฟีเจอร์ View Page Source ของ browser พบว่ามี HTML comment ที่ระบุ credentials `test:test` อยู่ตรงใกล้ๆ login form

<div align="center">

![Credentials in HTML Source Code](/img/sth-mini-web-ctf-2025-1/image-3.png)
![alt text](image.png)

</div>

## Access as "test"
ผมสามารถล็อกอินเข้า portal ได้ด้วย credentials `test:test`

<div align="center">

![Credentials in HTML Source Code](/img/sth-mini-web-ctf-2025-1/image-4.png)

</div>

เมื่อล็อกอินสำเร็จ เราจะถูก redirect ไปที่ URL `/userinfo.php` ที่แสดง User Information สังเกตว่าในหน้านี้ไม่มีฟอร์มสำหรับ user input

<div align="center">

![User Information - test](/img/sth-mini-web-ctf-2025-1/image-5.png)

</div>

เมื่อลองดู traffic ใน Burp Suite จะเห็นว่าหน้านี้มีการโหลดไฟล์ `/script.js` และเรียกข้อมูลจาก endpoint `/api.php?action=get_userinfo`

<div align="center">

![script.js and api.php](/img/sth-mini-web-ctf-2025-1/image-6.png)

</div>

### script.js

ในไฟล์ `script.js` มีโค้ดอยู่ 3 ส่วนหลักๆ ส่วนแรกเป็นโค้ดที่จะรันเมื่อโหลดหน้าเว็บเสร็จ โดยจะเป็นการ fetch endpoint `api.php?action=get_userinfo` ซึ่งก็คือ GET request ตามที่เราเห็นใน Burp Suite ด้านบน

```javascript
document.addEventListener('DOMContentLoaded', () => {
  // Fetch the current user's information from the API
  fetch('api.php?action=get_userinfo')
    .then(response => response.json())
    .then(data => {
      if (data.username) {
        // Populate the page with user info
        document.getElementById('username').textContent = data.username;
        document.getElementById('role').textContent = data.role;
        document.getElementById('status').textContent = data.status;
      } else if (data.error) {
        console.error('API Error:', data.error);
      } else {
        console.error('Unexpected response format.');
      }
    })
    .catch(err => {
      console.error('Error fetching user info:', err);
    });
});

...SNIP...
```

เมื่อดู HTTP response ของ URL `/api.php?action=get_userinfo` ใน Burp Suite จะเห็นข้อมูล JSON ดังนี้

<div align="center">

![๋JSON Data in HTTP Response](/img/sth-mini-web-ctf-2025-1/image-7.png)

</div>

แต่เมื่อลองเรียก `/api.php?action=get_userinfo` ด้วย cURL พบว่าไม่สามารถเรียกดูข้อมูลได้ แสดงว่ามีการตรวจสอบ session ก่อนอนุญาตให้เข้าถึงข้อมูล

```shell-session
$ curl 'https://web1.ctf.p7z.pw/api.php?action=get_userinfo'
{"error":"Unauthorized"}
```

ถ้าลองดูใน cookies storage ของ browser จะเห็น cookie ที่ชื่อ `PHPSESSID` ที่ไว้เก็บ session ของ user

<div align="center">

![Browser Cookies Storage](/img/sth-mini-web-ctf-2025-1/image-8.png)

</div>

เราสามารถเรียก `/api.php?action=get_userinfo` ด้วย cURL ได้โดยการเพิ่ม HTTP header ชื่อ Cookie เข้าไปด้วย และจะได้ผลลัพธ์ออกมาเป็น JSON เหมือนที่เห็นใน Burp Suite

```shell-session
$ curl -H 'Cookie: PHPSESSID=ba2b06cda26d1e0cd7e52e0b1e0cc4bf' 'https://web1.ctf.p7z.pw/api.php?action=get_userinfo'
{"username":"test","role":"user","remember_me_token":"b81943ba-d1c5-495a-8427-4711c39256bf","status":"Novice scammer, successfully conned 3 victims."}
```

### remember_me_token

จากข้อมูล JSON สิ่งที่น่าสนใจคือ `remember_me_token` ที่น่าจะเอาไว้บอกให้ระบบล็อกอิน user แบบอัตโนมัติเวลาเปิดหน้าเว็บครั้งต่อไป แต่ใน cookies storage ของเบราเซอร์ตามภาพด้านบน ไม่มีค่าดังกล่าวเก็บไว้

เลยนึกขึ้นมาได้ว่า ตอนที่เราล็อกอินก่อนหน้านี้ไม่ได้เลือก option "Remember Me" ผมจึงลอง Logout แล้ว Login ใหม่โดยเลือก "Remember Me" ด้วย

<div align="center">

![Login with Remember Me Option](/img/sth-mini-web-ctf-2025-1/image-9.png)

</div>

คราวนี้มี cookie `remember_me` เพิ่มขึ้นมาอีกอัน สังเกตว่าทั้ง cookie `PHPSESSID` และ `remember_me` ตั้งค่า HttpOnly ไว้เป็น false แปลว่าเราสามารถแก้ไข cookie ดังกล่าวได้จากใน browser

<div align="center">

![Browser Cookies Storage](/img/sth-mini-web-ctf-2025-1/image-10.png)

</div>

ข้อมูลใน `remember_me` cookie มีหน้าตาเป็น Base64 encoded value จำนวน 3 ชุด คั่นด้วย `.` จึงพอจะเดาได้ว่าเป็น JWT (JSON Web Token)

```text
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6ImI4MTk0M2JhLWQxYzUtNDk1YS04NDI3LTQ3MTFjMzkyNTZiZiJ9.Rlk_a69lx16hNhwn4nBfRxhiMGmEDoPIcxfr1_7JdH8
```

เราสามารถเปิดดูและแก้ไขข้อมูล JWT ได้โดยใช้เว็บ https://jwt.io จะเห็นว่าเมื่อ decode ข้อมูล JWT ออกมาแล้ว ค่า `token` ใน payload ของ JWT เป็นค่าเดียวกับ `remember_me_token` ของ user "test" ที่เห็นใน JSON ก่อนหน้านี้

<div align="center">

![Decoded JWT](/img/sth-mini-web-ctf-2025-1/image-11.png)

</div>

> มาถึงตอนนี้ สมมติฐานของผมคือ ถ้าเราสามารถแก้ไขค่า `token` ใน JWT ให้เป็น token ของ admin user เราจะสามารถหลอกให้ portal ล็อกอินให้เราเป็น admin โดยอัตโนมัติได้

### Abusing Debug Functions

ย้อนกลับมาที่โค้ดอีกสองส่วนที่เหลือในไฟล์ `script.js` เป็นฟังก์ชันที่ไม่ได้ถูกเรียกใช้งานจากหน้าเว็บ เข้าใจว่าสำหรับไว้ให้ developer ใช้ debug ระบบ ฟังก์ชันแรกคือ `debugFetchUserTest()`

```javascript
...SNIP...

function debugFetchUserTest() {
  fetch('api.php?action=get_userinfo&user=test')
    .then(response => response.json())
    .then(data => {
      console.log('Debug get_userinfo for user=test:', data);
    })
    .catch(err => {
      console.error('Error in debugFetchUserTest:', err);
    });
}

...SNIP...
```

เมื่อลองเรียก URL ที่ระบุไว้ในฟังก์ชัน `debugFetchUserTest()` ด้วย cURL จะได้ข้อมูล JSON แบบเดียวกับตอนเรียก `/api.php?action=get_userinfo` แบบไม่มี parameter `user` (เพราะเป็นข้อมูลของ user "test" เหมือนกัน)

```shell-session
$ curl -H 'Cookie: PHPSESSID=ba2b06cda26d1e0cd7e52e0b1e0cc4bf' 'https://web1.ctf.p7z.pw/api.php?action=get_userinfo&user=test'
{"username":"test","role":"user","remember_me_token":"b81943ba-d1c5-495a-8427-4711c39256bf","status":"Novice scammer, successfully conned 3 victims."}
```

ผมลองเปลี่ยนค่าของ parameter `user` จาก "test" ให้เป็น username ที่น่าจะเป็นของ admin แต่ได้ผลลัพธ์เป็น "User not found" ทั้งหมด

```shell-session
$ curl -H 'Cookie: PHPSESSID=ba2b06cda26d1e0cd7e52e0b1e0cc4bf' 'https://web1.ctf.p7z.pw/api.php?action=get_userinfo&user=admin'
{"error":"User not found"}

$ curl -H 'Cookie: PHPSESSID=ba2b06cda26d1e0cd7e52e0b1e0cc4bf' 'https://web1.ctf.p7z.pw/api.php?action=get_userinfo&user=administrator'
{"error":"User not found"}

$ curl -H 'Cookie: PHPSESSID=ba2b06cda26d1e0cd7e52e0b1e0cc4bf' 'https://web1.ctf.p7z.pw/api.php?action=get_userinfo&user=root'
{"error":"User not found"}
```

สังเกตจาก error message ถ้าไม่มีช่องทางอื่นในการหา username ของ admin เราอาจสามารถใช้ช่องทางนี้ในการ brute force เพื่อหา valid username ได้

ผมลองย้อนกลับมาดูฟังก์ชันสุดท้ายในไฟล์ `script.js` คือ `debugFetchAllUsers()`

```javascript
...SNIP...

function debugFetchAllUsers() {
  // admin.php
  fetch('api.php?action=get_alluser')
    .then(response => response.json())
    .then(data => {
      console.log('Debug get_alluser result:', data);
    })
    .catch(err => {
      console.error('Error in debugFetchAllUsers:', err);
    });
}
```

ในฟังก์ชันนี้มี comment ที่อ้างถึงพาธ `/admin.php` ที่เราหาเจอด้วย gobuster ก่อนหน้านี้แล้ว และเมื่อลองเรียก URL ที่ระบุไว้ในฟังก์ชันด้วย cURL ปรากฏว่าได้รายชื่อ user ออกมา 2 account

```shell-session
$ curl -H 'Cookie: PHPSESSID=ba2b06cda26d1e0cd7e52e0b1e0cc4bf' 'https://web1.ctf.p7z.pw/api.php?action=ge
t_alluser'
["test","admin-uat"]
```

เมื่อลองใช้ cURL โดยเปลี่ยน parameter `user` ของ URL ในฟังก์ชัน `debugFetchUserTest()` เป็น "admin-uat" พบว่าได้ข้อมูล JSON ของ admin ออกมา

```shell-session
$ curl -H 'Cookie: PHPSESSID=ba2b06cda26d1e0cd7e52e0b1e0cc4bf' 'https://web1.ctf.p7z.pwuserinfo&user=admin-uat'
{"username":"admin-uat","role":"admin","remember_me_token":"73eb7063-f8c3-4e50-bea2-07c05681aa92","status":"Gang boss, oversees all operations."}
```

> ตอนนี้เราได้ `remember_me_token` ของ admin user แล้ว ขั้นตอนต่อไปคือหาทางแก้ไขค่า token ใน payload ของ JWT ให้เป็นของ "admin-uat" เพื่อทำให้แอปพลิเคชันล็อกอินให้เราเป็น admin โดยอัตโนมัติ

## Access as "admin-uat"

JWT หรือ JSON Web Token เป็นมาตรฐานในการแลกเปลี่ยนข้อมูลโดยใช้ JSON object นิยมใช้ในเว็บแอปพลิเคชันเพื่อทำ authentication และ authorization

โครงสร้างของ JWT โดยปกติจะแบ่งออกเป็น 3 ส่วน คือ

* **header** เก็บประเภทของ token และ algorithm ที่ใช้ในการ signing
* **payload** เก็บข้อมูลของผู้ใช้หรือแอปพลิเคชัน
* **signature** เก็บ digital signature เพื่อไว้ใช้ตรวจสอบความถูกต้องของ header และ payload

การคำนวณ digital signature ของ JWT ทำได้โดยนำ header และ payload มา encode เป็น Base64 แล้วเชื่อมกันด้วย `.` จากนั้นนำมาคำนวณค่า HMAC โดยใส่ secret ที่เรากำหนด

<div align="center">

![JWT Signature Algorithm](/img/sth-mini-web-ctf-2025-1/image-12.png)

</div>

ถ้าแอปพลิเคชันใช้ secret ที่ไม่แข็งแรงหรือมีความยาวพอ เราสามารถ brute force JWT เพื่อหาค่า secret ได้ และหลังจากนั้นเราสามารถปลอมแปลง JWT โดยใส่ payload ตามที่ต้องการ แล้ว sign JWT ด้วย secret ดังกล่าว

### Brute Forcing JWT Secret

ผมใช้ hashcat โหมด 16500 ในการ brute force JWT secret โดยใช้ wordlist จาก rockyou.txt และสามารถ crack ได้สำเร็จ ออกมาเป็นคำว่า `"bobcats"`

```shell-session
$ hashcat -a 0 -m 16500 eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6ImI4MTk0M2JhLWQxYzUtNDk1YS04NDI3LTQ3MTFjMzkyNTZiZiJ9.Rlk_a69lx16hNhwn4nBfRxhiMGmEDoPIcxfr1_7JdH8 ~/ctf/rockyou.txt       
hashcat (v6.2.6) starting

<SNIP>

Dictionary cache hit:
* Filename..: /home/kong/ctf/rockyou.txt
* Passwords.: 14344384
* Bytes.....: 139921497
* Keyspace..: 14344384

<SNIP>

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6ImI4MTk0M2JhLWQxYzUtNDk1YS04NDI3LTQ3MTFjMzkyNTZiZiJ9.Rlk_a69lx16hNhwn4nBfRxhiMGmEDoPIcxfr1_7JdH8:"bobcats"
                                                          
<SNIP>
```

### Forging JWT for "admin-uat"

ตอนนี้เรามีข้อมูลที่ต้องใช้ในการปลอมแปลง JWT สำหรับเว็บแอปพลิเคชันได้แล้ว โดยใส่ payload เป็น token ของ admin user แล้ว sign ด้วย secret ที่เราหามาได้ ทั้งหมดนี้ทำได้จากในเว็บ jwt.io

<div align="center">

![Forged JWT](/img/sth-mini-web-ctf-2025-1/image-13.png)

</div>

เราจะได้ JWT ใหม่เป็น

```text
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6IjczZWI3MDYzLWY4YzMtNGU1MC1iZWEyLTA3YzA1NjgxYWE5MiJ9.IFc2uZiX_3x1ihXgRaANOPvmySpQzFz_wMD0up8Ny0I
```

### Replacing JWT and Gaining Access as "admin-uat"

จากนั้นนำ JWT ที่ได้ไปใส่แทนค่าเดิมใน `remember_me` cookie

<div align="center">

![Replacing test's JWT with admin-uat's one](/img/sth-mini-web-ctf-2025-1/image-14.png)

</div>

> หลังจากเปลี่ยน JWT แล้วลอง refresh หน้าเว็บ ผมพบว่าตัวเองยังมีสิทธิ์เป็น user "test" อยู่เหมือนเดิม จึงลองลบ cookie ดัวอื่นๆ ออกหมด ให้เหลือแค่ `remember_me` แล้ว refresh หน้าเว็บอีกรอบ

<div align="center">

![Remove all other cookies but remember_me](/img/sth-mini-web-ctf-2025-1/image-15.png)

</div>

คราวนี้พบว่าแอปพลิเคชันทำการล็อกอินให้เราเป็น user "admin-uat" โดยอัตโนมัติตามที่ตั้งสมมติฐานไว้

<div align="center">

![User Information - admin-uat](/img/sth-mini-web-ctf-2025-1/image-16.png)

</div>

## Money Printing Panel

เมื่อเรามีสิทธิ์ admin แล้วจะสามารถเข้าถึงหน้า `/admin.php` ได้ ซึ่งหน้าเว็บจะเป็นฟอร์มสำหรับรับค่าจำนวนธนบัตรและสกุลเงินที่ต้องการสั่งพิมพ์

<div align="center">

![Money Printing Panel](/img/sth-mini-web-ctf-2025-1/image-17.png)

</div>

ทดลองใส่ตัวเลขแล้วกดสั่ง Print

<div align="center">

![Test Printing Money](/img/sth-mini-web-ctf-2025-1/image-18.png)

</div>

ตัวแอปพลิเคชันมีข้อความแจ้งกลับมาว่า "We need a number, but not a number" ฟังดูเป็นปรัชญาสุดๆ แต่ก็ไม่ค่อยเข้าใจว่ามันหมายถึงอะไร

<div align="center">

![Test Printing Money](/img/sth-mini-web-ctf-2025-1/image-19.png)

</div>

### Flag 1

เมื่อลอง view page source จะพบ Flag 1 อยู่ใน HTML comment ด้านบน form

<div align="center">

![Flag 1](/img/sth-mini-web-ctf-2025-1/flag1.png)

</div>

### Source Code Analysis

เมื่อลอง scroll ลงมาดู source code ส่วนที่เหลือ จะเห็นบางส่วนของโค้ด PHP อยู่ใน HTML comment

<div align="center">

![Exposed PHP Code](/img/sth-mini-web-ctf-2025-1/image-20.png)

</div>

ถ้าลองอ่านโค้ดดูจะสังเกตเห็นว่า `$outputMessage` ในบรรทัดสุดท้าย ("We need a number, ...") จะเป็นข้อความเดียวกับที่แสดงในหน้าเว็บเมื่อเราใส่ตัวเลขแล้วกดสั่ง Print เมื่อกี้ (เข้าเงื่อนไข `else`)

ดังนั้นนี่อาจเป็นโค้ดส่วนที่ใช้ตรวจสอบ input จากหน้าเว็บ ซึ่งถ้าเราใส่ input ที่ถูกต้อง (เข้าเงื่อนไข `if`) ก็น่าจะสามารถสั่ง print ธนบัตร และได้ Serial Number ที่เป็น Flag 2 ออกมาด้วย

### Bypassing Input Filters

เงื่อนไขในโค้ดคือ ต้องทำให้ expression ก้อนนี้ evaluate ออกมาแล้วมีค่าเป็น true คือทั้งส่วนที่อยู่หน้า `&&` และหลัง `&&` ต้องเป็น true ทั้งคู่

```php
validateNumber($amount) && strpos($amount, 'STH')
```
เงื่อนไขของส่วนที่อยู่หลัง `&&` ค่อนข้างตรงไปตรงมา คือ **input ต้องมีคำว่า `STH`** อยู่ด้วย **แต่ต้องไม่อยู่ในตำแหน่งเริ่มต้น** เพราะไม่อย่างนั้นฟังก์ชัน `strpos()` จะรีเทิร์นค่ามาเป็น 0 (ตำแหน่งแรกที่เจอ string) ซึ่งเท่ากับ false

เมื่อพิจารณาส่วนที่เรียกฟังก์ชัน `validateNumber($amount)` ที่อยู่หน้า `&&` จะเห็นว่ามีการใช้ regular expression เพื่อตรวจสอบว่า input ที่รับเข้ามา ขึ้นต้นและลงท้ายด้วย**ตัวเลข 0-9** ใน **multiline mode** (`/m`) จึงจะ return ค่าเป็น true

```php
preg_match('/^[0-9]+$/m', $input)
```

ตาม [documentation ของ PHP](https://www.php.net/manual/en/reference.pcre.pattern.modifiers.php) อธิบายความหมายของ modifier m (PCRE_MULTILINE) ไว้ประมาณนี้

<div align="center">

![PCRE_MULTILINE Pattern Modifier](/img/sth-mini-web-ctf-2025-1/image-21.png)

</div>

สรุปง่ายๆ คือใน multiline mode การ match "end of line" (`$`) ของ regular expression จะสิ้นสุดที่ newline character (`\n`) ถ้ามีตัวอักษรนี้อยู่ใน input ดังนั้นเราสามารถสร้าง input string ที่เข้าเงื่อนไขทั้งสองอย่างตามที่แอปพลิเคชันต้องการได้ดังนี้

```text
555\nSTH
```

โดย `555\n` จะสอดคล้องกับเงื่อนไขส่วนที่อยู่หน้า `&&` และ `STH` ที่ตามมา จะสอดคล้องกับเงื่อนไขส่วนที่อยู่หลัง `&&`

ผมใช้ Burp Suite ในการ intercept request จาก browser เพื่อแก้ไขข้อมูลในฟอร์มก่อนส่งต่อไปยังเว็บแอปพลิเคชัน โดยเปลี่ยนจากตัวเลข `555` ที่กรอกในฟอร์ม เป็น `555%0ASTH` (`%0A` คือ `\n` แบบ URL-encoded) แล้วจึง forward request ต่อไปยังปลายทาง

<div align="center">

![PCRE_MULTILINE Pattern Modifier](/img/sth-mini-web-ctf-2025-1/image-22.png)

</div>

### Flag 2

ผลที่ได้คือเราสามารถสั่ง print ธนบัตรได้สำเร็จ และได้ Flag 2 ออกมาตามภาพ

<div align="center">

![Flag 2](/img/sth-mini-web-ctf-2025-1/flag2.png)

</div>
