---
title: "Shift Left is Hard"
date: 2023-03-04T13:20:53+07:00
toc: false
images:
tags:
  - rant
  - cybersecurity
---

จากประสบการณ์ที่ผ่านมา ผมรู้สึกว่าการที่ระบบหรือโครงการอะไรซักอย่าง จะมี security by design หรือ shift left ไม่ใช่เรื่องง่ายๆ เลย ซึ่งเท่าที่ลองวิเคราะห์ดู คิดว่ามันน่าจะเกิดจากกรอบความคิด (mindset) ของผู้มีส่วนเกี่ยวข้องทั้งหมด ถ้าให้แบ่งเป็นกลุ่มๆ น่าจะประมาณนี้

## Project Team / Vendor

แน่นอนว่าเป้าหมายของ project team คือการทำให้งานแล้วเสร็จตามกำหนด เลยอาจจะมองว่า security team เป็นคนที่จะคอยทัก คอยขัด ทำให้งานเดินไม่ตรงตามแผนหากต้องมีการแก้ไข ทำให้บางครั้งไม่มีการ involve security team ในการตัดสินใจบางอย่าง ซึ่งพอผ่านไปแล้วทีม security มาพบทีหลังและบอกว่าควรแก้ไข ก็จะเข้ากับ stereotype ที่ว่าเป็นคนคอยทัก คอยขัด ไปโดยปริยาย 😅

อีกส่วนหนึ่งที่เจอบ่อยๆ คือมองว่า security team เป็นผู้คุมกฎ เอาไว้ขออนุญาต หรือไว้บอกว่า ทำได้หรือไม่ได้ เท่านั้น แต่ในมุมมองผม security team มีหน้าที่เป็นที่ปรึกษา เพื่อระบุและวิเคราะห์ความเสี่ยง ต้องทำงานร่วมกับ project team เพื่อคิดหาแนวทางที่สามารถ support business process โดยมีความเสี่ยงอยู่ในระดับที่ยอมรับได้ ดังนั้นมาคุยกันตั้งแต่แรก ดีกว่านะ 🥲

หรือบางครั้ง security team อาจจะถามลง detail ถึงกระบวนการบางอย่าง ซึ่ง project team มองว่ายังไม่ถึงขั้นตอนที่จะลงรายละเอียดขนาดนั้นในโครงการ และปัดตกคำถามไป หรือไม่ได้พยายามหาคำตอบต่อ พอมาถึงขั้นตอนที่ต้องลง detail ก็พบว่ามีทางเลือกให้ไม่มากแล้ว เพราะระบบที่ออกแบบและติดตั้งมาได้ระยะหนึ่งแล้วนั้น ไม่ได้คิดเรื่องกระบวนการที่ว่าไว้ตั้งแต่แรก หรือถ้าจะแก้ไขก็ต้องมีค่าใช้จ่ายเพิ่ม 😣

สิ่งที่เคยพบอีกอย่างก็คือ การเอา compliance เป็นตัวตั้ง ในการตัดสินใจบางเรื่อง โดยไม่ถามทีม security เพราะคิดว่าทำแค่นี้ก็ comply ตามมาตรฐานหรือนโยบายแล้ว แต่ในความเป็นจริงนั้น comply !== secure สิ่งที่ควรทำจริงๆ คือการคุยกับ security team และดูเรื่องความเสี่ยง (risk) และกระบวนการที่เกี่ยวข้องทั้งหมดในภาพรวม (อ่านไปอ่านมาก็คล้ายๆ ย่อหน้าแรกแฮะ 😑)

## Executive

ผู้บริหารก็มีส่วนสำคัญในการทำให้ระบบหรือโครงการนั้นๆ มี security ครอบคลุมความเสี่ยงที่เกี่ยวข้องตั้งแต่แรกๆ โดยไม่ต้องมาปรับปรุงแก้ไขเพิ่มเติมในภายหลัง

ผมเข้าใจ(เอาเอง)ว่า เมื่อมองในมุมการบริหารโครงการ ผู้บริหารอาจจะเห็นว่าเรามี specifications หรือ TOR ที่เขียนมาครอบคลุมแล้ว ถ้าผู้รับจ้างหรือ project team ทำตามทุกอย่าง ระบบก็จะปลอดภัยแน่นอน แต่ในมุมมองผม ทุกโครงการยังต้องมีทีม security เข้าไป involve ตั้งแต่เริ่ม kick-off จนจบอยู่ดี

ซึ่งทีม security เองก็ต้องพยายามชี้แจงให้ผู้บริหารเข้าใจ และสนับสนุนให้เข้าไปมีส่วนร่วมในกระบวนการพัฒนาระบบ/โครงการ ซึ่งอาจจะเป็นเรื่องที่ท้าทาย หรือเป็นเรื่องง่ายก็ได้ ขึ้นอยู่กับ mindset ของผู้บริหาร นโยบาย และวัฒนธรรมองค์กร 😏

เพราะสุดท้ายถ้าปล่อยให้ project team หรือผู้รับจ้าง ออกแบบ/ตัดสินใจเรื่อง security เองทั้งหมดโดยไม่มี objective opinion ถึงแม้ระบบหรือโครงการที่ส่งมอบจะครบถ้วนถูกต้องตาม spec/TOR ทุกอย่าง แต่ก็อาจจะมีจุดอ่อนหรือไม่สามารถรองรับกระบวนการด้าน security ที่จำเป็น ซึ่งคนที่ต้องรับผิดชอบแก้ไขต่อก็คงไม่พ้น security team อยู่ดี 🤣

## Security Team

แน่นอนว่าปัญหาไม่ได้เกิดจากคนอื่นเท่านั้น ตัวทีม security เองก็ต้องคอยสังเกตตัวเองว่าทำหน้าที่ได้เหมาะสมไหม โทนเสียงที่ใช้ จังหวะที่พูดเรื่อง security ในที่ประชุม รวมทั้งความสามารถในการอธิบายให้เห็นความสำคัญของประเด็นที่พูด (soft skills ล้วนๆ 😵‍💫)

หรือบางที project team ฟอร์เวิร์ดเมลที่มีการคุยและตัดสินใจเรื่อง security กันไปแล้วมาให้ โดยจั่วหัวว่า FYI&hellip; ทีม security ก็อาจจะรู้สึกทำตัวไม่ถูก ว่าควรตอบหรือแสดงความคิดเห็นไหม (แต่ส่วนตัวถ้าผมมีประเด็น/คำถาม ก็จะ comment กลับไป ถือว่าทำหน้าที่ในส่วนของเรา)

สองตัวอย่างข้างบน เป็นสิ่งผมรู้สึกว่ายาก และไม่แน่ใจเหมือนกันว่าความพอดีอยู่ที่ไหน บางทีนั่งฟังคนอื่นคุยกันแล้วเห็นว่ามันอาจจะทำให้เกิดความเสี่ยง ก็อาจจะต้องเสนอหน้าเข้าไปคุยด้วยทั้งๆ ที่เค้าไม่ได้ถาม 555+ 🙄

ทั้งนี้ทั้งนั้น hard skills ก็ยังคงเป็นสิ่งที่ขาดไม่ได้ ไม่งั้น security team ก็จะไม่สามารถวิเคราะห์หรือให้คำแนะนำที่เหมาะสมในแต่ละเรื่องได้เลย 😩

อีกประเด็นคือการยึดติดกับ compliance/นโยบาย/แนวปฏิบัติ มากเกินไป สิ่งที่ security team ต้องเตือนตัวเองเป็นระยะๆ คือเรามีหน้าที่ support business process ให้ดำเนินงานต่อไปได้ โดยลดความเสี่ยงให้เหลือน้อยที่สุด และบางครั้งอาจจะต้อง compromise บางอย่าง

ซึ่งผมคิดว่าเราจะหลีกเลี่ยงการมาถึงจุดที่ต้อง compromise ได้ด้วยการให้ security team มีส่วนร่วมให้มากที่สุดในทุกกระบวนการตั้งแต่ต้นจนจบนี่แหละ

## Summary

สมมติมีคนถามผมว่า ถ้าอยากทำ security by design หรือ shift left ให้มีประสิทธิภาพ หรือประสบความสำเร็จ สิ่งสำคัญลำดับแรกๆ มีอะไรบ้าง ผมก็คงตอบประมาณนี้

1. Executive support
2. Stakeholders' mindset
3. Security team's skills (both soft & hard)

แน่นอนว่านี่ก็ยังรู้สึกว่าที่ผ่านมายังห่างไกลจากคำว่า "ประสบความสำเร็จ" เป็นอารมณ์ประมาณว่า ถึงผลลัพธ์จะออกมาไม่ได้แย่ แต่มันสามารถทำให้ดีกว่านี้ได้ ก็เป็นทักษะที่ต้องเรียนรู้และพัฒนากันต่อไป 🔥
