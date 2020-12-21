---
title: "Information Security vs Cybersecurity"
date: 2020-12-21T21:01:26+07:00
tags: ["cybersecurity", "information security", "rant"]
---

วันนี้นั่งประชุมกับทีม IT และเพิ่งค้นพบว่า นิยามของ "ความมั่นคงปลอดภัยไซเบอร์" กับ "ความมั่นคงปลอดภัยทางสารสนเทศ" ของผมกับของคนอื่น ไม่เหมือนกัน

สำหรับผมมันเป็นแบบนี้

<img src="/img/information-security-vs-cybersecurity/my-venn-diagram.png" alt="My Venn Diagram" style="margin: 0 auto;">

Cybersecurity ในนิยามของผมคือ Information Security ของ traditional IT บวกกับ OT security ที่เกี่ยวข้องกับ physical process ไม่ว่าจะเป็นระบบ ICS/SCADA หรือ IoT ทุกอย่างรวมอยู่ภายใต้คำว่า cybersecurity แต่เป็นส่วนที่อยู่นอก information security

สำหรับทีม IT มันเป็นแบบนี้

<img src="/img/information-security-vs-cybersecurity/their-venn-diagram.png" alt="Their Venn Diagram" style="margin: 0 auto;">

ในนิยามของเค้า Cybersecurity เป็น subset ของ Information Security เพราะคำว่า "cyber" คือส่วนที่เป็นข้อมูล digital หรือการทำงานผ่านเน็ตเวิร์กเท่านั้น แต่คำว่า "information" จะหมายรวมถึงสารสนเทศทั้งที่เป็น digital และ analog รวมไปถึงทรัพยากรอื่นๆ เช่น process และ people ด้วย

ลอง Google ดูก็พบนิยาม/การเปรียบเทียบที่น่าสนใจในหลายเว็บ แต่มีอยู่ไอเดียนึงที่ผมไม่เคยนึกถึงเลยก็คือ จริงๆ แล้วมันอาจจะเป็นสิ่งที่ intersect กันแบบนี้ก็ได้

<img src="/img/information-security-vs-cybersecurity/others-venn-diagram.png" alt="Other's Venn Diagram" style="margin: 0 auto;">

ที่มา: [Understanding difference between Cyber Security & Information Security - CISO Platform](https://www.cisoplatform.com/profiles/blogs/understanding-difference-between-cyber-security-information)

อารมณ์ประมาณว่า information security ก็จะดูเรื่องข้อมูลสารสนเทศทั้งหมดโดยไม่แบ่งแยกว่าอยู่ในรูปแบบ digital หรือ analog ส่วน cybersecurity ก็จะดูทุกๆ อย่าง (things) ที่อาจถูกโจมตีได้ผ่านระบบ ICT ซึ่ง -security ทั้งสองวงก็จะมีส่วนที่มาคาบเกี่ยวกันอยู่ตรง digital information อะไรทำนองนี้

สรุปว่า&hellip; ไม่สรุป เพราะผมก็ไม่รู้เหมือนกันว่าอันไหนถูก 😆 แต่อย่างหนึ่งที่น่าสังเกตคือ ปัจจุบันเราจะเห็นคำว่า "สารสนเทศ" น้อยลง แต่เห็นคำว่า "ไซเบอร์" บ่อยขึ้น อย่างในภาพรวมของประเทศก็จะเป็น "พ.ร.บ. การรักษาความมั่นคงปลอดภัยไซเบอร์" หรือในส่วนของ sector-specific เช่น สำนักงานนโยบายและแผนพลังงาน (สนพ.) ก็มี "แผนการพัฒนาการรักษาความมั่นคงปลอดภัยไซเบอร์สำหรับสมาร์ทกริด" นอกจากนี้หลายๆ หน่วยงานก็จะมีการจัด "การแข่งขันทักษะทางไซเบอร์" เป็นต้น
