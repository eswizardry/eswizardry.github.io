---
layout: post
title: "มาเพิ่มแท็บให้กับ SourceInsight ด้วย TabSiPlus"
comments: True
description: "SourceInsight เป็น Text editor ตัวหนึ่งที่ผมใช้ทำงานเป็นหลัก ก่อนจะเปลี่ยนมาใช้ Sublime Text"
tags: tools
---

<a href="{{ page.url }}"><img src="/assets/tabSiPlus/SI-about-logo.jpg" /></a>
<!--more-->

[SourceInsight](http://www.sourceinsight.com/) เป็น [Text editor](https://en.wikipedia.org/wiki/Text_editor) ตัวหนึ่งที่ผมใช้ทำงานเป็นหลัก (ส่วนมากใช้อยู่ที่ทำงาน) ก่อนจะเปลี่ยนมาใช้ [Sublime Text](http://www.sublimetext.com/) ในปัจจุบันซึ่งก็ใช้ในการพัฒนาและเขียนบล็อกในเว็บนี้ด้วย

## SourceInsight
เป็น [Text editor](https://en.wikipedia.org/wiki/Text_editor) ที่พัฒนาโดยบริษัท SourceDynamic มี features ที่เด่นดังนี้

### [SourceInsight Features](http://www.sourceinsight.com/prodinfo.html)
- Call Graphs and Class Tree Diagrams
- Context Sensitive Dynamic Type Resolution
- Symbol Windows For Each File
- Automatic Display of Declarations in the Context Window
- Syntax Formatting - Like Syntax Coloring but More
- Context-Sensitive Smart Rename
- Finds References Quickly
- Mixed Language Editing
- Keyword Searches Like an Internet Search on Your Code Base
- Symbolic Auto-Completion
- Quick Access to All Symbols and Files
- Project Orientation
- etc.

จากฟังก์ชันการทำงานนี่ถือว่าเป็น [Text editor](https://en.wikipedia.org/wiki/Text_editor) ที่ครบเครื่องมาก ถ้าจะมีตัวเปรียบเทียบที่ทำความสารถได้ขนาดนี้โดยไม่ต้องมีส่วนเสริม (plug-in) แล้วล่ะก็เห็นจะมีแต่ [SlickEdit](http://www.slickedit.com/) อีกตัวซึ่งตัวนี้อาจมีฟังก์ชันเยอะกว่า [SourceInsight](http://www.sourceinsight.com/) ด้วยซ้ำไปแต่สำหรับผมคิดว่ามันเยอะเกินพอดีทำให้กินทรัพยากรของเครื่องมากไปและหน้าตาของมันแม้จะดูทันสมัยแต่ก็เต็มไปด้วย scroll bar ซึ่งกินพื้นที่การทำงานบนหน้าจอไปเยอะเลย รู้สึกว่ามันรก

กลับมาที่ [SourceInsight](http://www.sourceinsight.com/) พระเอกของเรากันต่อ สำหรับผมแล้วนอกจากหน้าตาที่ดูออกจะโบราณแล้ว ( เนื่องจากว่า [SourceInsight](http://www.sourceinsight.com/) นั้นไม่มีการพัฒนาเพื่อเพิ่มฟังก์ชันต่างๆ ไปหลายปีแล้วหรือจะบอกว่าเลิกพัฒนาไปแล้วก็ได้, นอกจากแก้ bug หรือพอร์ตไป windows เวอร์ชันใหม่) ก็มีอีกอย่างที่ผมอยากได้จาก [SourceInsight](http://www.sourceinsight.com/) คือแท็บของไฟล์ที่เราเปิดทำงานอยู่ทั้งหมดเพื่อเพิ่มความสะดวกในการเปลี่ยนไปทำงานกับไฟล์อื่นๆ และยังทำให้รู้สถานะว่าเราเปิดไฟล์อะไรค้างไว้บ้าง

ด้านล่างคือ SourceInsight แบบดั้งเดิมที่ยังไม่มี tab
![notap](/assets/tabSiPlus/SI-noTap.jpg)

## [TabSiPlus](http://goo.gl/1vI6AT)
[TabSiPlus](http://goo.gl/1vI6AT) เป็น plug-in ของ SourceInsight ที่พัฒนาโดยโปรแกรมเมอร์ชาวจีนซึ่งใช้ชื่อว่า Simon.W

### สิ่งที่จำเป็นต้องมีในการใช้งาน [TabSiPlus](http://goo.gl/1vI6AT)
- [Microsoft Visual C++ 2008 Redistributable Package](https://www.microsoft.com/en-us/download/details.aspx?id=29)
อันนี้ต้องถูกติดตั้งในเครื่องเพื่อการทำงานที่ถูกต้องของ TabSiPlus

## การใช้งาน [TabSiPlus](http://goo.gl/1vI6AT)
หลังจากโหลด TabSiplus มาแล้วให้ copy โฟลเดอร์ไปไว้ที่เราต้องการได้เลยหลังจากนั้นเปิดเข้าไปในโฟลเดอร์
แล้วดับเบิ้ลคลิก TabSiHost ถ้าไม่มีข้อผิดพลาดอะไรแค่นี้ TabSiPlus ก็ทำงานเรียบร้อยแล้ว
![้host](/assets/tabSiPlus/tapSi-host-run.jpg)

เปิด SourceInsight ขึ้นมาก็จะเจอกับ Tab ที่เพิ่มขึ้นมา
![taptop](/assets/tabSiPlus/SI-addTap-toTop.jpg)

## [TabSiPlus](http://goo.gl/1vI6AT) customization
ใหเปิดเข้าไปในโฟลเดอร์ของ TabSiPlus อีกทีจากนั้นเปิดไฟล์ Tabtest ขึ้นมาเพื่อปรับแต่ง theme ของ tab
![้tabtest](/assets/tabSiPlus/tapSi-folder-setting.jpg)

เปิดขึ้นมาแล้วจะเจอกับหน้าปรับแต่งธีมที่มีเครื่องหมายคำถามเต็มไปหมด
![้font](/assets/tabSiPlus/tapSi-load-setting.jpg)

หน้านี้ปรับแต่ง font
![้font](/assets/tabSiPlus/tapsi-font-setting.jpg)

หน้านี้ปรับ option ว่าต้องการให้มีไอคอนสำหรับปิดแท็บไหม และกรุ๊ปแท็บที่มีชื่อเดียวกันไหม
![้option](/assets/tabSiPlus/tapSi-addexitIconOption-setting.jpg)

อันข้างล่างคือตัวอย่างธีมที่ผมปรับแต่งไว้
![้option](/assets/tabSiPlus/tapSi-save-setting.jpg)


#### และภายในหน้าต่างของ SourceInsight ที่มี TabSiPlus เกาะอยู่เรายังสามารถปรับแต่ง option ต่างได้อีกหลายอย่างเช่น

- เลือก theme ที่เราสร้างขึ้น
- ปรับให้แท็บอยู่ข้างล่างหรือข้างบน
- อื่นๆ ลองปรับแต่งกันดูได้ครับ

![้optioUI](/assets/tabSiPlus/SI-tapOption-click.jpg)

![้optioUI](/assets/tabSiPlus/tapSiPlus-option-menu.jpg)

บล็อกนี้หลักๆแล้วผมต้องการบันทึกไว้กันลืมสำหรับตัวเองเผื่ออนาคตได้กลับมาใช้ SourceInsight อีก...<3
