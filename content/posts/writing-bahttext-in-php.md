---
title: "Writing BAHTTEXT() in PHP"
date: 2018-06-16T16:53:53+07:00
tags: ["php", "bahttext", "rant", "code"]
---

เมื่อวันก่อนมีคนมาโพสต์ถามใน LINE ว่า จะเขียนโค้ด PHP เพื่อแปลงค่าเงินเป็นตัวหนังสือให้สั้นๆ เหมือนโค้ด FoxPro ที่แปะให้ดูเป็นตัวอย่างได้ไหม

```foxpro
FUNCTION spell

PARAMETER Vn
Va = STRT(TRAN(Vn,'@R G9A9B9C9D9E9F9A9B9C9D9E9F9.9F9S'),' F0.','')

RETURN STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(;
STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(STRT(;
SUBS(Va,RAT(' ',Va)+2,35),'1','หนึ่ง'),'2','สอง'),'3','สาม'),'4','สี่'),;
'5','ห้า'),'6','หก'),'7','เจ็ด'),'8','แปด'),'9','เก้า'),'.0F0S','บาทถ้วน'),;
'0F',''),'0E',''),'0D',''),'0C',''),'0B',''),'0',''),'A','ล้าน'),;
'B','แสน'),'C','หมื่น'),'D','พัน'),'E','ร้อย'),'F','สิบ'),'.','บาท'),;
'หนึ่งสิบ','สิบ'),'สองสิบ','ยี่สิบ'),'สิบหนึ่ง','สิบเอ็ด'),'S','สตางค์')
```

รู้สึกว่าน่าสนใจดีเลยลองเขียนดู แน่นอนว่าออกมาไม่ใกล้เคียงกับคำว่าสั้น 😅 แต่ก็สนุกดีและใช้งานได้ เลยขอจดเก็บไว้หน่อย รูปแบบการทำงานของฟังก์ชันพยายามลอกของ Excel มา คือปัดทศนิยมเป็นสองตำแหน่ง รองรับค่าลบ ค่าศูนย์ และตัวเลขยาวๆ ได้ (เท่าที่ทดสอบด้วย PHPUnit คือที่ระดับ 1&times;10<sup>12</sup> ยังโอเคอยู่) หน้าตาโค้ดก็ประมาณนี้
<!--more-->
```php
<?php
declare(strict_types=1);

function bahtText(float $amount): string
{
    [$integer, $fraction] = explode('.', number_format(abs($amount), 2, '.', ''));

    $baht = convert($integer);
    $satang = convert($fraction);

    $output = $amount < 0 ? 'ลบ' : '';
    $output .= $baht ? $baht.'บาท' : '';
    $output .= $satang ? $satang.'สตางค์' : 'ถ้วน';

    return $baht.$satang === '' ? 'ศูนย์บาทถ้วน' : $output;
}

function convert(string $number): string
{
    $values = ['', 'หนึ่ง', 'สอง', 'สาม', 'สี่', 'ห้า', 'หก', 'เจ็ด', 'แปด', 'เก้า'];
    $places = ['', 'สิบ', 'ร้อย', 'พัน', 'หมื่น', 'แสน', 'ล้าน'];
    $exceptions = ['หนึ่งสิบ' => 'สิบ', 'สองสิบ' => 'ยี่สิบ', 'สิบหนึ่ง' => 'สิบเอ็ด'];

    $output = '';

    foreach (str_split(strrev($number)) as $place => $value) {
        if ($place % 6 === 0 && $place > 0) {
            $output = $places[6].$output;
        }

        if ($value !== '0') {
            $output = $values[$value].$places[$place % 6].$output;
        }
    }

    foreach ($exceptions as $search => $replace) {
        $output = str_replace($search, $replace, $output);
    }

    return $output;
}
```

ตัวอย่างการใช้งานและผลลัพธ์ที่ได้ 😆

```php
<?php
echo bahtText(0)."\n";
echo bahtText(11)."\n";
echo bahtText(0.5)."\n";
echo bahtText(1270851.375291)."\n";
echo bahtText(-185409.12)."\n";

# results
ศูนย์บาทถ้วน
สิบเอ็ดบาทถ้วน
ห้าสิบสตางค์
หนึ่งล้านสองแสนเจ็ดหมื่นแปดร้อยห้าสิบเอ็ดบาทสามสิบแปดสตางค์
ลบหนึ่งแสนแปดหมื่นห้าพันสี่ร้อยเก้าบาทสิบสองสตางค์
```
