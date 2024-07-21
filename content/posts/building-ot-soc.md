---
title: "Building an OT SOC"
date: 2024-07-20T08:58:48+07:00
draft: false
toc: true
images:
tags:
  - sans
  - cybersecurity
  - operational technology
  - security operations center
  - soc
---

## Overview

เมื่อคืนได้นั่งดูวิดีโอย้อนหลังงาน SANS ICS Security Summit & Training 2024 ใน session ที่ชื่อ "Lessons Learned Building OT SOCs" ของ Bruce Large รู้สึกว่าได้เรียนรู้เยอะมาก เลยมาจดไว้เผื่อเป็น reference ในอนาคต

{{< youtube _i5Ws-2egL0 >}}

Bruce เล่าถึงแนวทางในการบริหารจัดการ SOC สำหรับระบบ OT โดยแบ่งเนื้อหาเป็น 3 ประเด็นหลักๆ คือ people, process, และ technology

## People

### Leading the Team
* สิ่งสำคัญในการเป็น leader คือต้องรู้ทั้ง technical และเรื่องคน ต้องสามารถปรับการบริหารจัดการให้เข้ากับสมาชิกในทีมแต่ละคนได้
* จัดการ workload ให้ดี โดย Bruce บอกว่าทีมเค้าใช้ Kanban Board เพื่อให้เห็นปริมาณงานของแต่ละคนในทีม
* นอกจากบริหารจัดการคนในทีมแล้ว ต้อง manage up (ผู้บริหาร) และ manage out (หน่วยงานที่เกี่ยวข้อง) ให้ครอบคลุมทั้งในและนอกองค์กรด้วย
* ควรเขียน [SOC Charter](https://www.isaca.org/resources/news-and-trends/industry-news/2022/writing-a-charter-for-an-enterprise-security-operations-center) เพื่อระบุหน้าที่ ขอบเขต และอำนาจ ในการปฏิบัติงานของ SOC ให้ชัดเจน

### Training and Development
* ควร balance ระหว่างสกิลที่ทีมควรจะมี กับงานที่แต่ละคนอยากจะทำ (incident response, security architecture, security operations, etc.)
* อาจจะจัด 1-on-1 session มานั่งคุยกัน เพื่อกำหนด training plan ที่เหมาะสมสำหรับทีมงานแต่ละคน
* ใช้วิธี teach back คือไปเรียน/ศึกษามาแล้วให้มาสอนคนอื่นๆ ต่อด้วย ซึ่งช่วยในการกระจายความรู้ ฝึกทักษะการสื่อสาร และสร้างความคุ้นเคยกับคนนอกทีม
* ใช้ได้ทั้ง free resources (อาจจะใช้เวลานานหน่อย รอเรียนตอนว่างๆ) หรืออบรมแบบเป็นทางการ (อบรมทีเดียว 3 วัน 5 วัน มีค่าใช้จ่าย แต่ประหยัดเวลาได้มากกว่า)
* ถ้ามีโอกาสควรจัดหลักสูตรแบบเป็นทีม เพราะในการทำงานจริงของ SOC ต้องอาศัย team work ค่อนข้างสูง

### Using the SOC Human Capital Model
* เป็นโมเดลที่ได้จาก[โครงการวิจัย](https://www.usenix.org/system/files/conference/soups2015/soups15-paper-sundaramurthy.pdf)ที่ทำโดยการไปนั่งทำงานใน SOC จริงๆ
* เน้นที่การพัฒนาสกิลของทีม SOC เป็นวงรอบ Skills --> Empowerment --> Creativity --> Growth โดยมีเป้าหมายในการเพิ่ม Operational Efficiency
* มี metrics วัดประสิทธิภาพการทำงาน เพื่อให้ management เห็นผลลัพธ์จากการลงทุน (return on investment)

{{< figure src="/img/building-ot-soc/soc-human-capital-model.png" attr="SOC Human Capital Model" >}}

### Communication
* สิ่งสำคัญอีกอย่างคือการฝึกทักษะการสื่อสาร ทั้งการพูด และการเขียน
* สมาชิกในทีมควรรู้ว่าแต่ละคนถนัด/ชอบการสื่อสารแบบไหน และบางครั้งต้องปรับแนวทางการสื่อสารให้เข้ากับทีม
* มีคอร์สแนะนำคือ "[Effective Information Security Writing](https://chrissanders.org/training/writing/)" ของ Chris Sanders ซึ่งจะสอนทั้งการเขียนสไตล์ incident response SOC ticket และ penetration testing report

## Process

### Mental Models
* การปรับตัวเข้ากับสภาพแวดล้อมการทำงาน เรามีกระบวนการยังไงบ้างเมื่อมีสมาชิกใหม่เข้ามาเพิ่มในทีม
* เราสามารถ rotate สมาชิกระหว่างทีมได้ไหม เช่น OT SOC, IT SOC, Site Engineering, Security Architecture เพื่อให้แต่ละทีมเข้าใจภาพรวมทั้งหมดขององค์กร
* SOC Ride Along Day คือเปิดศูนย์ SOC ให้ทีมอื่นเข้าไปดู (เช่น เดือนละครั้ง) เพื่อให้เห็นว่า SOC มีกระบวนการทำงานยังไง สามารถ integrate กับระบบอื่นได้ยังไงบ้าง เป็นการเพิ่ม understanding, trust, และ awareness ให้กับส่วนที่เกี่ยวข้อง
* แนะนำให้อ่าน [Publications](https://chrissanders.org/publications/) ของ Chris Sanders

### Knowledge Base
* ระบบ OT แต่ละระบบมีความแตกต่างกัน และทีม SOC จะมีความรู้ที่สำคัญอยู่เยอะ ทั้งเรื่องใน SOC และนอก SOC
* เราจะจัดทำแหล่งความรู้สำหรับสมาชิกใหม่ในทีมได้ยังไง
* วิธีที่ Bruce ยกตัวอย่างคือ ให้หา Subject Matter Expert (SME) แล้วจัด lunch & learn โดยมอบหมายให้มีคน take note... หลังจากเสร็จแล้ว ก็ให้ SME คนที่สอนมาตรวจสอบสิ่งที่โน้ตได้ แล้วเก็บไว้เป็น knowledge base หนึ่งเรื่อง
* ควรใช้ controlled document framework (เอกสารที่มีกระบวนการ authorized, review, etc. เช่นพวก procedures, standards) ควบคู่ไปกับการทำ KB ทั้งนี้ความรู้บางอย่างจาก KB อาจจะขยับไปอยู่ใน controlled document ก็ได้
* ควรหาวิธีเก็บ KB ให้ปลอดภัย เพราะเป็นข้อมูลสำคัญที่ผู้โจมตีสามารถเอาไปใช้ประโยชน์ได้ และต้องคิดเผื่อกรณีที่เราอาจไม่สามารถเข้าถึง KB ได้ตามปกติ จะทำยังไงให้ทีม SOC ยังคงมีข้อมูลที่จำเป็นในการทำงานได้

### Detection Engineering
* เป็นกระบวนการที่ทำให้ use case ที่เราสร้างขึ้น มีความสอดคล้องกับ security activities อื่นๆ เช่น Risk Assessment, Cyber Threat Intelligence, Project Work, Threat Hunting เป็นต้น
* สร้าง use case ยังไงให้ analyst เอาไป take action ต่อได้
  * บอก next steps, แนะนำ playbook
  * กำหนดประเภทของ rules
    * High Confidence มั่นใจว่าเป็นการ attack แน่ๆ ดูเคสนี้ก่อน
    * Investigative ยังไม่ค่อยแน่ใจ ให้ไป investigate ต่อ
    * Anomaly อาจจะเป็นแค่ noise เฉยๆ ไว้ดูหลังจากจัดการเคสที่สำคัญกว่าแล้ว
  * กำหนด life cycle ของ rules
    * Experimental
    * Functional
    * Stable
    * Retired
* กำหนดกระบวนการ request for detection
* แนะนำให้อ่าน blog ของ SANS เรื่อง [Purple Teaming and Threat-Informed Detection Engineering](https://www.sans.org/blog/purple-teaming-threat-informed-detection-engineering/)

{{< figure src="/img/building-ot-soc/detection-engineering.png" attr="Detection Engineering" >}}

### Metrics & Reporting
* ควรมีทั้ง leading และ lagging metrics
* ในระดับบนสุดไม่ควรมีเกิน 6 key metrics (สามารถมี sub metrics เพื่อ drill down ลงไปต่อได้)
* ควรเป็น metrics ที่ทำให้เห็นภาพรวมกว้างๆ ของงาน SOC ทั้งหมด เช่น collection, detection, incident response, ..., etc.
* ควรผสมกันระหว่าง operational metrics และ improvement metrics (OKRs)
* แนะนำให้ฟัง [Blueprint Podcast](https://www.sans.org/podcasts/blueprint/) ของ SANS

### Purple Team for Validating the Capability
* SOC เป็นมากกว่าแค่ security controls แต่เป็น complex capabilities ที่ people, process, technology ทำงานร่วมกัน
* แนะนำ Cyber Vee Model สรุปคร่าวๆ คือเป็นกระบวนการ concept --> design --> develop --> validate
* ซึ่งถ้ามองในมุมการออกแบบและพัฒนา SOC เราสามารถ validate ได้โดยการทำ red teaming ซึ่งเป็นมากกว่า penetration testing เพราะต้องการวัด capability ของ blue team ด้วย

{{< figure src="/img/building-ot-soc/cyber-vee-model.png" attr="Cyber Vee Model" >}}

## Technology

### Stuck? Start at the OT DMZ
* ถ้าไม่รู้จะเริ่มจากตรงไหน Bruce แนะนำให้เริ่มจาก OT DMZ
* เพราะ OT DMZ หรือ iDMZ (Industrial DMZ) มักจะมีระบบและเทคโนโลยี IT ที่ทีม SOC คุ้นเคยอยู่เยอะ
* 90% ของ incident ในระบบ OT จะเริ่มจากฝั่ง IT หรือจุดที่ IT/OT เชื่อมต่อกัน ดังนั้น OT DMZ จึงเป็นจุดเริ่มต้นที่ดีที่ในการออกแบบ defensible architecture
* ถ้าทีม SOC มาจากฝั่ง IT ก็จะเป็นโอกาสที่ดีในการสร้าง trust กับทีม OT ที่เกี่ยวข้อง

### Industrial NIDS
* แนะนำให้อ่าน [The Five ICS Cybersecurity Critical Controls](https://www.sans.org/white-papers/five-ics-cybersecurity-critical-controls/) ของ SANS โดย NIDS จะอยู่ใน Control No. 3: ICS Network Visibility and Monitoring
* ศึกษา network ของระบบ OT ให้เข้าใจ ว่าควรวาง NIDS ไว้ตรงจุดไหน
* ใช้ scenario จาก Control No. 1: ICS-specific Incident Response Plan และศึกษา TTP ของผู้โจมตี เพื่อให้มั่นใจว่า NIDS จะเห็นสิ่งที่เราต้องการตรวจจับ
* อาจจะเริ่มลองจาก network security monitoring tools ที่เป็น open source เพื่อให้เห็นประโยชน์ก่อนลงทุน

### Use a Collection Management Framework
* แนะนำให้[ดูวิดีโอ และอ่าน Whitepaper](https://www.dragos.com/resources/webinar/using-a-collection-management-framework-for-ics-security-operations-and-incident-response/) ของ Dragos
* ใช้เพื่อกำหนดความต้องการในรวบรวม log, ระยะเวลาในการจัดเก็บ, และความครอบคลุมของ log ที่จัดเก็บ
* เป็นองค์ประกอบสำคัญในกระบวนการ security operations อื่นๆ เช่น Threat Hunting และ Detection Engineering

### Validate Technology with Penetration Testing
* ใช้หลักการเดิมตาม Cyber Vee Model
* เป็นวิธีที่ดีที่สุดในการตรวจสอบว่า use case ที่สร้างไว้ สามารถใช้งานได้จริง
* เราจะได้ข้อมูลจำนวนมากจากการทำ pentest ที่สามารถเอาไปทำ Detection Engineering ต่อได้
* สร้างความมั่นใจให้ทีม SOC ว่าสิ่งที่ออกแบบและสร้างไว้ สามารถตรวจจับการโจมตีที่เกิดขึ้นได้

## Resources & References
* [MITRE 11 Strategies of a World-Class Cybersecurity Operations Center](https://www.mitre.org/sites/default/files/2022-04/11-strategies-of-a-world-class-cybersecurity-operations-center.pdf)
* [Building a Security Operations Centre](https://www.ncsc.gov.uk/collection/building-a-security-operations-centre)
* [SOC-CMM](https://www.soc-cmm.com/downloads/soc-cmm%20whitepaper.pdf)
* [EPRI Integrated SOC](https://smartgrid.epri.com/doc/ICCS_Summit/C4.1_King_EPRI%20European%20Summit%20-%20Threat%20Management%20Presentation%20-%20Ralph%20King%20-%20FINAL.pdf)
* [SANS LDR551: Building and Leading Security Operations Centers](https://www.sans.org/cyber-security-courses/building-leading-security-operations-centers/)

## Summary

สำหรับผมถือเป็นวิดีโอความยาว 35 นาทีที่คุ้มค่าสุดๆ ดูจบแล้วรู้สึกว่ามีเรื่องที่ต้องไปศึกษาต่อเยอะมาก แต่อย่างน้อยก็ทำให้เห็นแนวทางที่ชัดเจนขึ้นว่าถ้าต้องการพัฒนาทีม SOC สำหรับระบบ OT ควรจะต้องมีอะไรบ้าง ถ้าใครมีเวลา แนะนำให้ดูวิดีโอเต็มๆ ครับ

ปิดท้ายด้วยตารางสรุปจาก slide แผ่นสุดท้ายของ Bruce

<table>
<thead>
  <tr>
    <th>People</th>
    <th>Process</th>
    <th>Technology</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td valign="top" width="33.3%">
      <p><b>Be</b> an enabling leader</p>
      <p><b>Guide</b> training in your team -- dont' dictate</p>
      <p><b>Use</b> the SOC Human Capital model</p>
      <p><b>Focus</b> on developing team communication</p>
    </td>
    <td valign="top" width="33.3%">
      <p><b>Develop</b> Mental Models</p>
      <p><b>Use</b> Detection Engineering</p>
      <p><b>Enable</b> Knowledge Management</p>
      <p><b>Empower</b> with Metrics</p>
      <p><b>Validate capabilities</b> with Purple Teams</p>
    </td>
    <td valign="top" width="33.4%">
      <p><b>Start</b> with the OT DMZ</p>
      <p><b>Deploy</b> Industrial NIDS</p>
      <p><b>Develop</b> a CMF</p>
      <p><b>Validate technology</b> with Penetration Testing</p>
    </td>
  </tr>
</tbody>
</table>
