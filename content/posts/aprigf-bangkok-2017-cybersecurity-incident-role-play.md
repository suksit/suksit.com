---
title: "APrIGF Bangkok 2017 Cybersecurity Incident Role Play"
date: 2017-07-28T15:49:40+07:00
tags: [ "cybersecurity", "aprigf2017", "workshop", "rant" ]
---

วันนี้ได้มีโอกาสไปร่วมงาน [APrIGF Bangkok 2017](https://2017.aprigf.asia/) ที่อาคารมหิตลาธิเบศร จุฬาลงกรณ์มหาวิทยาลัย ในช่วง session Cybersecurity Incident Role Play พบว่าเป็นประสบการณ์ที่ดี (แม้ว่าจะไม่ได้มีส่วนร่วมแชร์อะไรกับชาวโลกเค้าเลยก็ตาม 😆)

ลักษณะของ session จะเป็นแบบให้ผู้เข้าร่วม workshop มาเล่นสวมบทบาทเป็นหน่วยงานต่างๆ ในบริษัทแห่งหนึ่ง ซึ่งในบริษัทนี้จะประกอบด้วยสี่กลุ่มคือ Management, IT, Legal, และ Communication ตัวผมเองได้ไปนั่งงงๆ อยู่ในกลุ่ม Communication 😵

ส่วนผู้ดำเนินรายการมีทั้งหมด 5 คน โดยผู้ดำเนินรายการหลัก คือ [@adliwahid](https://twitter.com/adliwahid) คนนี้ฮามาก เป็น Security Specialist จาก APNIC และจะมีอีก 4 คนประจำอยู่แต่ละกลุ่ม หนึ่งในสี่คนนี้คือ [@kitisak](https://twitter.com/kitisak) ซึ่งปัจจุบันเป็นที่ปรึกษาด้าน information security ให้กับ Thai Banker's Association และเป็นผู้แนะนำให้ผมมาร่วมงานนี้ด้วย

<!--more-->

จากนั้นก็เริ่มเล่นกัน โดยผู้ดำเนินรายการจะมี scenario แบบเป็นลำดับเหตุการณ์ให้ ซึ่งเริ่มจากกลุ่ม IT และ Communication ได้รับอีเมลจากคนที่อ้างว่าเป็น hacker ระบุว่าได้ขโมยข้อมูลภายในของบริษัทออกมา ประกอบด้วยข้อมูลของพนักงาน และข้อมูลที่เป็นความลับของลูกค้า บลา บลา บลา&hellip; และเรียกเงินค่าไถ่แลกกับการไม่เปิดเผยข้อมูลดังกล่าว 🤔

ถึงตอนนี้เริ่มสนุก 🙃 เพราะแต่ละกลุ่มต้องพยายามคิดว่าจะทำอย่างไรในสถานการณ์ต่างๆ ที่มีเวลาจำกัด เช่น จะจ่ายเงินให้ hacker ไหม, จะแจ้งลูกค้าและผู้ถือหุ้นหรือเปล่า, IT จะดำเนินการอย่างไรต่อไป, ฯลฯ ซึ่ง scenario ก็จะค่อยๆ เผยออกมาเรื่อยๆ เมื่อเวลาผ่านไป&hellip; ทั้ง session ใช้เวลาประมาณ 1 ชั่วโมงครึ่ง ซึ่งผมรู้สึกว่าเวลาผ่านไปเร็วมาก

สุดท้ายก็จะเป็นบทสรุป โดยให้ผู้เข้าร่วม workshop แสดงความคิดเห็นร่วมกับทีมผู้ดำเนินรายการ จังหวะนี้รู้สึกพลาด เพราะพยายามตั้งใจฟัง เลยลืมจด 😖 เอาเท่าที่จำได้ก็ประมาณนี้

- หน่วยงานควรจะมี incident response plan / team สำหรับรับมือกับเหตุการณ์ไม่คาดฝัน เพราะในช่วงสถานการณ์แบบนั้น เราแทบจะไม่มีเวลาคิดวางแผนอะไรเลย ถ้ามี instructions ให้ทำตามเป็นลำดับ 1, 2, 3, 4, &hellip; ก็จะทำให้ไม่มั่วและวุ่นวายเหมือนตอนเล่นเกม
- สิ่งสำคัญสำหรับ incident reponse คือ 3 C's (Collaborate, Coordinate, Communicate) ต้องมีการสื่อสารกับส่วนที่เกี่ยวข้องทั้งหมด ต้องรู้ว่าควรจะติดต่อใคร ต้องมีการกำหนดศูนย์กลางในการติดต่อประสานงาน และความร่วมมือทั้งภายในและภายนอกหน่วยงานนั้นมีความสำคัญมาก
- ต้องมีการวิเคราะห์มูลค่า ความสำคัญ และชั้นความลับของข้อมูล รวมทั้งผลกระทบที่จะเกิดขึ้นหากข้อมูลรั่วไหลหรือสูญหาย จากนั้นจึงค่อยกำหนดมาตรการป้องกันที่เหมาะสมต่อไป
- cybersecurity เป็นความรับผิดชอบของทุกคนในหน่วยงาน เวลาเกิดเหตุการณ์ต่างๆ จะโทษแต่ IT หรือให้ IT ดำเนินการอยู่ฝ่ายเดียวไม่ได้ ทุกหน่วยงานต้องช่วยกัน
- จุดอ่อนที่สุดของระบบ cybersecurity คือ คน ถ้ามีการ traning ที่เหมาะสม และทุกคนมี awareness ด้าน cybersecurity ก็จะช่วยลดความเสี่ยงจากการถูกโจมตีลงได้
- ควรให้ข้อมูลเท่าที่จำเป็นแก่ผู้ที่เกี่ยวข้อง เช่น CEO อาจจะออกมาประกาศให้ลูกค้าทราบว่า ขณะนี้ระบบมีปัญหา เรากำลังวิเคราะห์หาทางแก้ไขกันอยู่ ผู้ได้รับผลกระทบมีใครบ้าง คาดว่าจะดำเนินการแล้วเสร็จเมื่อไร แต่ไม่จำเป็นต้องบอกว่า เราโดนจดหมายขู่ หรือสงสัยว่าจะโดนขโมยข้อมูล อะไรทำนองนี้
- ในการให้ข้อมูลกับ public ควรใช้ภาษาที่ผู้ฟังเข้าใจได้ง่ายที่สุด เช่น ไม่จำเป็นต้องบอกว่าองค์กรเราปฏิบัติตามมาตรฐาน ISO 27001, NERC-CIP, ฯลฯ เพราะลูกค้าส่วนใหญ่อาจจะฟังแล้วไม่เข้าใจ และพาลทำให้รู้สึกน่ารำคาญเปล่าๆ

ปล. พบว่าการทำ workshop ทำนองนี้กับชาวต่างชาติ สนุกกว่าแบบที่มีแต่คนไทยล้วนเยอะ เพราะแต่ละคนมาจากต่างสังคมต่างวัฒนธรรม ทำให้เห็นแนวคิดหรือวิธีการแก้ปัญหาที่หลากหลาย และส่วนใหญ่ก็ไม่กลัวที่จะแสดงความคิดเห็นจากมุมมองของตัวเอง จนบางทีก็ดูเหมือนจะทะเลาะกัน แต่ที่แน่ๆ คือทุกคนอยากมีส่วนร่วม หวังไว้ว่าต่อไปตัวเองต้องทำให้ได้แบบนั้น 😤
