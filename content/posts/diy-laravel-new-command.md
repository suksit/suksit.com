---
title: "DIY `laravel new` Command"
date: 2018-07-08T08:16:54+07:00
tags: [ "laravel", "bash", "composer", "code", "rant" ]
---

เมื่อซัก 1–2 อาทิตย์ที่แล้ว พบปัญหาประหลาดกับคำสั่ง

```bash
laravel new <project-name>
```

โดยเมื่อรันคำสั่งดังกล่าว จะเจอ error ประมาณนี้

```bash
$ laravel new test-project
Crafting application...
'composer' is not recognized as an internal or external command,
operable program or batch file.
Application ready! Build something amazing.
```

คืออยู่ดีๆ เหมือนมันหาคำสั่ง composer ไม่เจอ ก็งงสิครับ เพราะแต่ก่อนคำสั่งนี้ (laravel new ...) มันเคยใช้งานได้ หรือถ้าลองเรียก composer เฉยๆ ใน Git Bash มันก็ยังทำงานได้ปกติ 😅

เช็คไปเช็คมา เลยพบว่ามันเกิดจาก 2-3 สาเหตุร่วมกันคือ

<!--more-->

1. ผมใช้ Git Bash ไม่ได้ใช้ Command Prompt หรือ PowerShell
2. ผมติดตั้ง Composer แบบ [Command-line Installation](https://getcomposer.org/download/) โดยโหลดไฟล์ `composer.phar` มา แล้ว rename เป็น `composer` ซึ่งมันรันได้ใน Git Bash แต่รันบน Command Prompt และ PowerShell ไม่ได้ เพราะนามสกุลไม่ใช่ไฟล์ executable ของวินโดวส์ (`*.cmd`, `*.bat`, `*.exe`)
3. Laravel Installer มันไปเรียกใช้แพ็กเกจ [Process](https://symfony.com/components/Process) ของ Symfony ซึ่งจะพยายามเช็คว่าตัวเองรันอยู่บน OS ไหน โดยใช้ `DIRECTORY_SEPARATOR` พอมันเจอว่าเป็น backslash (`\\`) ก็เลยไปเรียก `cmd.exe` แทนที่จะรันบน shell ปัจจุบันที่มันทำงานอยู่ เลยทำให้รันคำสั่ง `composer` ไม่ได้ ด้วยเหตุผลตามข้อ 2 😑

วิธีแก้อย่างถูกหลักการก็น่าจะต้องติดตั้ง Composer ใหม่ โดยใช้ตัวติดตั้งสำหรับวินโดวส์ที่มีให้โหลดในเว็บ ซึ่งมันจะมีไฟล์ `composer.cmd` มาให้ด้วย อยู่ใน path เดียวกันกับ `composer.phar` ทำให้ Laravel Installer สามารถเรียกคำสั่ง `composer` จาก Command Prompt ได้ แต่แน่นอนว่า วิธีง่ายๆ เราไม่ทำ 555+ 🙃

อันที่จริงเราสามารถสร้าง project Laravel ใหม่ได้โดยใช้อีกคำสั่งนึง ตามที่เขียนใน documentation ของ Laravel คือ

```bash
composer create-project --prefer-dist laravel/laravel <project-name>
```

แต่ผลลัพธ์ที่ได้จะไม่เหมือนการใช้คำสั่ง `laravel new …` ซะทีเดียว (จริงๆ คือมันไม่สร้างไฟล์ `.env` ให้ด้วย แค่นั้นแหละ 🤣) ด้วยความรำคาญ เลยคิดว่าสร้างคำสั่ง `laravel new` ส่วนตัวไว้ใช้เองเลยดีกว่า วิธีการก็ไม่มีอะไร ลอกคำสั่งใน Laravel Installer มาใช้ดื้อๆ นี่แหละ

```bash
#!/bin/bash

if [[ ! $# -eq 1 ]]; then
    printf "\n%s\n" "USAGE: `basename $0` <project-name>"
    exit 1;
fi

project="$1"
archive="/tmp/$$.zip"

curl --progress -o $archive http://cabinet.laravel.com/latest.zip
unzip -q -d "$project" $archive
rm $archive

cd "$project"

composer install --no-scripts
composer run-script post-root-package-install
composer run-script post-create-project-cmd
composer run-script post-autoload-dump
```

ตั้งชื่อไฟล์ว่า `laravel-new` แล้วเอาไปวางใน `~/bin/` เวลาใช้ก็เรียกจากที่ไหนก็ได้ หน้าตาคำสั่งก็จะคล้ายๆ ของต้นฉบับ

```bash
laravel-new <project-name>
```

สรุปคือเป็น shell script บ้านๆ ไม่มีการเช็ค error ใดๆ แต่ก็ใช้งานได้ดี ผลลัพธ์เหมือนการรันคำสั่ง `laravel new …` ทุกประการ 😁
