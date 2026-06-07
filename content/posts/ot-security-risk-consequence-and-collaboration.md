---
title: "Risk, Consequence, and Collaboration"
date: 2026-06-07T08:38:31+07:00
draft: false
toc: false
images:
tags:
  - cybersecurity
  - operational technology
  - rant
---

เมื่อ 2-3 วันก่อนได้อ่านบทความ 2 เรื่อง คือ [Absolute And Relative Risk Reduction](https://dale-peterson.com/2026/06/02/absolute-and-relative-risk-reduction/) ของ Dale Peterson และ [Engineering and network security: the missing link in cyber-physical risk management](https://www.controlglobal.com/blogs/unfettered/blog/55381500/cyber-physical-security-the-collaboration-between-engineering-and-cybersecurity-disciplines) ของ Joe Weiss

ถ้าดูจากหัวข้อ เหมือนจะไม่ค่อยเกี่ยวข้องกัน แต่พออ่านแล้วรู้สึกว่า ทั้งสองบทความมีแนวคิดบางอย่างที่สอดคล้องกันอยู่

* **Likelihood vs Consequence:** เป้าหมายของการทำ cybersecurity ในปัจจุบันจะเน้นที่การลด likelihood (โอกาสที่จะโดนโจมตี หรือช่องโหว่ของ protocol ต่างๆ) แต่อาจจะมองข้ามเรื่องการลด consequence (ผลกระทบทางกายภาพ หรือผลกระทบต่อ operation)
* **You Will Ultimately Get Breached:** air gap ไม่มีจริง และสุดท้ายระบบ OT จะโดนโจมตีในที่สุด ดังนั้นแนวป้องกันชั้นสุดท้ายจะต้องอยู่ที่ระดับ process level และ physical level
* **Limitation of Cybersecurity Controls:** IT/OT network security controls ที่เป็น best practice ที่แนะนำกัน เช่น การทำ microsegmentation หรือ protocol monitoring ไม่สามารถป้องกันหรือกู้คืน catastrophic process failure ได้

บทความของ Dale จะพูดถึงประเด็นที่ว่า การระบุ risk reduction แบบ relative อาจจะทำให้ไม่เห็นภาพรวมที่แท้จริง และอาจทำให้การตัดสินใจลงทุนด้าน cybersecurity ไม่คุ้มค่าเท่าที่ควร

เช่น ถ้าเราบอกว่าการ implement control นี้ จะทำให้ relative risk reduction อยู่ที่ 80% (if an attacker breaches the perimeter, the tool stops them 80% of the time)... ผู้บริหารฟังแล้วน่าจะรู้สึกประทับใจ และอาจจะไฟเขียวให้ดำเนินการได้เลย

แต่จริงๆ แล้วโอกาสที่ attacker จะทะลุผ่าน perimeter และเข้ามาถึงระบบ OT ได้ อาจมีน้อยมาก เช่น 0.1% ต่อปี ดังนั้น absolute risk reduction ของ control ที่เราต้องการ implement จะเท่ากับ 0.08% เท่านั้น 🤔

Dale แนะนำว่าควรเอา budget ไปลงที่การทำ consequence reduction อาจจะดีกว่า คือการพยายามลดผลกระทบที่อาจเกิดขึ้น เช่นการทำ backup, orchestration, รวมถึงทำยังไงให้ recovery process กลับมาได้เร็วที่สุด

> ผมมองว่า อาจจะรวมไปถึงเรื่องการทำ cyber-informed engineering ด้วยก็ได้

ส่วนบทความของ Joe จะเน้นเรื่อง collaboration ระหว่างทีม security และ engineer โดยเค้าไม่ค่อยเห็นด้วยกับแนวคิดที่ว่า "IT security pro can easily pivot to OT"

เพราะมันต้องอาศัยความเข้าใจเชิงลึกเกี่ยวกับ physical process ที่เกี่ยวข้อง อุปกรณ์หรือ sensor ต่างๆ รวมไปถึง control loop เพื่อป้องกัน physical catastrophe ที่อาจเกิดขึ้น

> อันนี้ผมเห็นด้วย เพราะอย่างงานที่ทำอยู่ ทีม OT security ก็ไม่สามารถทำเพียงทีมเดียวได้ ต้องใช้ความรู้และความร่วมมือจาก system owner เยอะมากๆ

Joe ยังพูดถึงเรื่องที่ว่า การโจมตีระบบ OT ไม่ได้มาจาก network หรือ malware เท่านั้น อาจจะเป็นการโจมตีโดยใช้หลักการทางฟิสิกส์ตรงๆ เลยก็ได้ โดยยกตัวอย่าง [Aurora Generator Test](https://en.wikipedia.org/wiki/Aurora_Generator_Test)

ระบบ OT ควรต้องมี resilience นั่นคือ ต้องทนทานต่อการโจมตีทางไซเบอร์ รวมไปถึงต้องสามารถจำกัดผลกระทบของ physical consequences ที่อาจเกิดขึ้นโดยความไม่ตั้งใจหรืออุบัติเหตุต่างๆ ด้วย

ประเด็นสำคัญคือทีม security ต้องเข้าใจ physical consequence และวิธีการควบคุมผลกระทบที่อาจเกิดขึ้น ซึ่งต้องอาศัยความรู้และทักษะของทีม engineer จึงจะประเมินความเสี่ยงด้านไซเบอร์ของระบบ OT ได้สอดคล้องกับความเป็นจริง

ดังนั้นการสื่อสารและความร่วมมือระหว่างทีม security กับทีม engineer จึงเป็นสิ่งสำคัญมากๆ ในการทำ cybersecurity ของระบบ OT 🫠
