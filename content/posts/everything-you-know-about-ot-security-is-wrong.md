---
title: "Everything You Know About OT Security is Wrong"
date: 2026-07-11T07:53:11+07:00
draft: false
toc: false
images:
tags:
  - rant
  - operational technology
  - cybersecurity
---

หลายอาทิตย์ก่อนได้ดู webinar ที่บรรยายโดย Andrew Ginter แห่ง Waterfall Security ชื่อหัวข้อ [Everything You Know About OT Security is Wrong](https://waterfall-security.com/resources-webinar-vod-everything-you-know-about-ot-security-is-wrong/)

หลายๆ เรื่องเป็นสิ่งที่ผมเห็นด้วยและเคยพูดถึงไปในบล็อกบ้างแล้ว การได้นั่งดูวิดีโอนี้ถือเป็นการเติมกาวให้ confirmation bias ของตัวเอง 555+

{{<image src="/img/everything-you-know-about-ot-security-is-wrong/webinar-cover.jpg" alt="NCSC's Secure Connectivity for Operational Technology (OT)" position="center" style="box-shadow: 0 5px 10px 0 rgba(0,0,0,0.2); margin-bottom: 1.5em; width: 100%;">}}

เนื้อหาของ webinar จะพูดถึงสิ่งที่คนส่วนใหญ่เข้าใจผิดเกี่ยวกับ OT security รวมๆ แล้วมีประมาณ 11 ข้อ

1. **Asset inventory is the first step: You can't protect what you don't know you have** เกือบทุกคำแนะนำด้าน cybersecurity จะบอกว่าให้ทำ asset inventory ก่อน แต่จริงๆ การรู้ว่าเรามี asset จำนวนเท่าไหร่ และแต่ละตัวมี vulnerability อะไรบ้างนั้น ไม่สำคัญเท่าการรู้ว่า data flow ที่วิ่งผ่าน security boundary มีอะไรบ้าง และอาจถูกเอามาใช้ในการโจมตีระบบ OT ได้ยังไง

> Inventory DATA FLOWS first &ndash; flows crossing consequence boundaries.

2. **OT/engineering teams resist cybersecurity measures** โดยเฉพาะเรื่องการ patch หรืออัปเดต firmware... สาเหตุหลักคือ security team กับ engineer มองคนละมุมกัน ส่วนใหญ่ security team จะมองเรื่องช่องโหว่และการโจมตี แต่ engineer จะมองเรื่อง operation และ safety

> Every changes that you make to the system risks making a mistake. Some mistakes kill people or can take down the whole system.

สิ่งสำคัญคือทั้งสองทีมต้องทำความเข้าใจข้อจำกัดของแต่ละฝ่าย แล้วพูดคุยเพื่อหาแนวทางที่เหมาะสมร่วมกัน

3. **Protect the information &ndash; the CIA, or AIC, or IAC or something** อันนี้ไม่ใช่แค่ความเข้าใจผิดของคนส่วนใหญ่ แต่มันฝังลึกอยู่ในมาตรฐานหรือ guidelines ด้าน OT cybersecurity ด้วย จริงๆ แล้วในระบบ OT ส่วนใหญ่ สิ่งที่เราต้องปกป้องคือ physical process ไม่ใช่ information

> IT protects information &ndash; OT prevents sabotage of physical operations.

ถ้าอยากจะลิสต์สิ่งที่ OT security ต้องปกป้องก็ควรจะเป็น safety, reliability, และ efficiency/performance มากกว่า

4. **Air gaps are a myth, they provide a false sense of security** อันนี้ผมเจอกับตัวเองบ่อยเหมือนกัน คำว่า air gap ในความหมายของผมคือ ไม่มีการเชื่อมต่อกับเครือข่ายภายนอก แต่สำหรับ IT หรือที่ปรึกษา(ส่วนใหญ่) air gap = no route to the internet แปลว่าถ้าระบบ OT เชื่อมต่อกับ intranet หรือระบบภายนอกอื่นๆ ที่อยู่ในองค์กร ก็ยังนับว่าเป็น air gap อยู่

Andrew บอกว่าสำหรับระบบ OT สิ่งที่ควรทำคือ Network Engineering

> Network Engineering = deterministic control over the movement of information into OT systems at consequence boundary.

5. **Prevention / the perimeter is dead. Visibility / response are the priority** อาจจะเป็น concept ที่จริงสำหรับ IT network แต่สำหรับระบบ OT ยังไงก็ควรต้องมี prevention ที่เชื่อถือได้ เพราะการคิดจะพึ่ง detection / alert แล้วหวังว่าเราจะสามารถ response ได้รวดเร็วและทันต่อสถานการณ์ อาจจะทำให้สายเกินไป

> "Hope" is not what we expect of design engineers. We expect engineering-grade protection not IT-grade "hope".

6. **If only we could secure OT as well as we do IT, then we would be good** ถ้าดูจาก consequence ที่จะเกิดขึ้นเมื่อระบบถูกโจมตี ระบบ OT ควรจะต้อง secure กว่าระบบ IT ดังนั้นการเอา security controls ของ IT มาใช้กับระบบ OT อาจจะไม่เพียงพอ

> Physical operations must be protected materially more thoroughly than is reasonable on internet-connected IT systems.

7. **Brownfield equipment is the problem** Andrew มองว่าคำว่า greenfield ในระบบ OT ไม่มีอยู่จริง ระบบ OT ส่วนใหญ่จะ out-of-date ไปเรียบร้อยเมื่อนำออกใช้งาน เพราะตั้งแต่กระบวนการออกแบบ ติดตั้ง ไปจนถึง commissioning จะต้องมีการทำ engineering change control และไม่ได้อัปเดตแพตช์ล่าสุดแน่นอน ดังนั้นยังไงมันก็เป็น brownfield แม้จะเพิ่ง implement เสร็จก็ตาม

> Brownfield is the nature of change-controlled systems, and all consequential OT systems are change controlled. Get used to it.

อันนี้ผมมองว่าน่าจะต้องดูว่า brownfield equipment นั้นมัน legacy แค่ไหน มันอาจจะเป็นปัญหาจริงๆ ก็ได้ เพราะถ้ามองในมุม performance หรือ security controls แล้ว อุปกรณ์ที่เพิ่งติดตั้งเมื่อ 5 ปีที่แล้ว ควรจะมีความสามารถหรือประสิทธิภาพดีกว่าอุปกรณ์เก่าที่ใช้มานาน เราอาจจะไม่ได้เรียกมันว่า greenfield equipment แต่เราน่าจะมีทางเลือกในการทำให้มัน secure มากกว่าอุปกรณ์ที่อยู่มา 20 ปีแล้ว

8. **We have no budget** องค์กรส่วนใหญ่มี budget เพียงแต่ cybersecurity ไม่ได้รับ priority ที่เหมาะสมมากกว่า ซึ่งเป็นหน้าที่ของทีม security ที่จะต้องสื่อสารกับผู้บริหารเพื่อให้เห็นความสำคัญของ cybersecurity ในมุมของ business ให้ได้

> We need a clearer understanding of risk &ndash; the language of business &ndash; need to be able to explain risks, not just patching metrics.

9. **Zero Trust, encryption, and IAM are the answers. What was the question?** สรุปสั้นๆ คือมันเป็น IT-style protection ที่อาจจะไม่เพียงพอสำหรับระบบ OT (ทำนองเดียวกับข้อ 6.) สิ่งที่ Andrew แนะนำคือ Network Engineering และ Cyber-Informed Engineering

> Use network engineering and CIE to defeat the most sophisticated adversaries first &ndash; use what budget is left over on other IT-style protections.

10. **Our biggest single threat is insiders &ndash; with USB drives** Andrew บอกว่าการที่ระบบ OT ส่วนใหญ่ดาวน์ไปนั้นเกิดจาก insider จริง แต่มันไม่ใช่การโจมตี และ USB drive ก็เป็นช่องทางที่ทำให้เกิดความเสี่ยงจริง แต่มันมีอะไรที่เราต้องป้องกันมากกว่าแค่ USB drive

> Prevention: control flow of attack information both online & offline e.g. USB, laptops.

รวมไปถึงต้องมีกระบวนการรับมือเมื่อโดนโจมตีจริงๆ

> Defense in depth: detect, respond, and recover.

11. **Patching is the most important part of our security program** ความจริงคือกระบวนการ patch เป็นกระบวนการที่ "แพง" ที่สุดใน OT security program และผลที่ได้ก็อาจจะไม่คุ้มค่ากับการลงแรงซักเท่าไหร่ รวมทั้งไม่ได้ช่วยป้องกัน zero-day attack, stolen password, firewall misconfiguration, หรือการเอา HMI ไปต่อเข้า internet ดังนั้นเราอาจจะเลือก patch เฉพาะระบบที่มีความเสี่ยงเป็นพิเศษ และใช้ control อื่นๆ ในการลดความเสี่ยงควบคู่กันไป

> Patch most expose systems &ndash; to USB / pivoting through temporary laptops / expose to internet.

และเน้น concept ตามข้อ 1. และข้อ 4.

> Control flows of attack information into most sensitive systems &ndash; patch more cautiously.

แต่เอาจริงๆ ถ้าดูแล้วระบบสำคัญมันมีความเสี่ยงเยอะๆ เราอาจจะออกแบบอะไรผิดมาตั้งแต่ต้นก็เป็นได้

> "Most sensitive" system that NEED to be exposed to USB/pivoting/internet attacks, are a very bad design &ndash; redesign on an emergency basis.

สุดท้าย Andrew แนะนำให้อ่าน [Secure Connectivity Principles for Operational Technology (OT)](https://www.ncsc.gov.uk/collection/operational-technology/secure-connectivity) ของ UK NCSC ที่ทำร่วมกับหน่วยงานด้านไซเบอร์ของหลายประเทศ

{{<image src="/img/everything-you-know-about-ot-security-is-wrong/ncsc-secure-connectivity-for-operational-technology.png" alt="NCSC's Secure Connectivity for Operational Technology (OT)" position="center" style="box-shadow: 0 5px 10px 0 rgba(0,0,0,0.2); margin-bottom: 1.5em; width: 80%;">}}

ปล. ข้อมูลข้างบนเป็นสิ่งที่ผมสรุปมาคร่าวๆ อาจจะมีรายละเอียด/ประเด็นไม่ครบถ้วนเท่าไร ถ้ามีเวลาแนะนำให้นั่งดู จะได้ฟังเนื้อหาแบบเต็มๆ ครับ ความยาวประมาณ 1 ชั่วโมง
