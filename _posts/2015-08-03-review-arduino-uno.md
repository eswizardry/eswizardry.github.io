---
layout: post
title: "แกะกล่อง Arduino UNO"
comments: True
description: "Arduino UNO นั้นใช้ Atmega328 (มีหน่วยควมจำแบบ Flash 32kB ใช้เป็น bootloader ไป 0.5kB, SRAM 2kB และ EEPROM อีก 1kB) เป็นไมโครคอนโทรลเลอร์หลักซึ่งใช้แพ็คเกจแบบ DIP ทำให้ง่ายต่อการพัฒนา"
tags:
- arduino
---

<a href="{{ page.url }}"><img src="/assets/review-uno/arduino-uno.jpg" /></a>
<!--more-->

<br/>
บล็อกก่อนหน้าผมได้เขียนแนะนำเกี่ยวกับ Arduino ไปแล้ววันนี้จะมาแนะนำบอร์ดอย่างเป็นทางการจาก Arduino ที่ได้รับความนิยมสูงสุดในตอนนี้คือเจ้า Arduino [UNO](https://www.arduino.cc/en/Main/arduinoBoardUno)

> [UNO](https://www.arduino.cc/en/Main/arduinoBoardUno) ในภาษาสเปนกับอิตาเลียนนั้นแปลว่า One ในภาษาอังกฤษ หรือ หนึ่งในภาษาไทยนั่นเอง

<br/>
บอร์ด Arduino [UNO](https://www.arduino.cc/en/Main/arduinoBoardUno) นั้นเป็นบอร์ดที่ออกมาตั้งแต่ปลายปี 2010 แต่ด้วยความที่ตัวผมเองทำงานด้านนี้อยู่แล้วและมองว่า Arduino เป็นแค่ของเล่นหรือสำหรับมือใหม่ก็เลยไม่ได้สนใจที่จะหามาลองเล่นจนแต่ช่วงนี้ว่างๆ และเห็นพัฒนาการของ Arduino ผ่านมามากกว่าห้าปีแล้วและคิดว่า มันมีอะไรดี จึงลองหามาเล่นซักหน่อย

<br/>
![uno-box](/assets/review-uno/uno-box.jpg)
<br/>

## ภายในกล่องมีอะไรบ้าง
- ครั้งแรกที่ผมได้รับพัสดุเจ้า Arduino และเจอกับกล่องผมก็ประหลาดใจเล็กน้อยเพราะว่ามันมีขนาดเล็กกว่าที่ผมคิดไว้พอสมควร
<br/>
![uno-inpalm](/assets/review-uno/uno-inpalm.jpg)
<br/>

- ภายในกล่องก็จะประกอบไปด้วยตัวบอร์ด แผ่นพับที่มีข้อความขอบคุณ และสติ๊กเกอร์ Arduino
<br/>
![uno-unbox](/assets/review-uno/uno-unbox.jpg)
<br/>

## ฮาร์ดแวร์ของ [UNO](https://www.arduino.cc/en/Main/arduinoBoardUno)
- [UNO](https://www.arduino.cc/en/Main/arduinoBoardUno) นั้นใช้ [Atmega328](http://www.atmel.com/devices/atmega328.aspx) (มีหน่วยควมจำแบบ Flash 32kB ใช้เป็น bootloader ไป 0.5kB, SRAM 2kB และ EEPROM อีก 1kB) เป็นไมโครคอนโทรลเลอร์หลักซึ่งใช้แพ็คเกจแบบ [DIP](https://en.wikipedia.org/wiki/Dual_in-line_package) ทำให้ง่ายต่อการพัฒนาเช่นเวลาที่เราต้องการนำชิปที่ถูกโปรแกรมไปใช้ในบอร์ดอื่น หรือเวลาที่ชิปเสียเราก็สามารถที่จะหาซื้อชิปมาเปลี่ยนเองได้ง่ายๆ

- มี I/O ให้ใช้งานทั้งหมด 20 ขา (แบ่งเป็นดิจิตอล I/O 16 ขา และ อินพุตแบบแอนาล็อกอีก 6 ขา) ใช้คริสตัลความถี่ 16 MHz มี USB คอนเน็คเตอร์แบบ B, หัวต่อ DC adaptor, พอร์ตสำหรับโปรแกรมแบบ ICSP, และสวิตช์สำหรับรีเซ็ท

- ตัวบอร์ดสามารถเลือกแหล่งจ่ายไฟได้โดยอัตโนมัติระหว่างจากพอร์ต USB และแหล่งจ่ายภายนอก แต่สิ่งที่ผมคิดว่ามันยังขาดอยู่ก็คือสวิตช์เปิดปิดซึ่งไม่มีเราต้องทำการเปิดปิดโดยการดึงปลั๊กหรือถอดสาย USB เท่านั้น

- อ้อเกือบลืมอีกอย่างว่าบนบอร์ดนั้นยังประกอบไปด้วยไมโครคอนโทรลเลอร์อีกตัวหนึ่งคือ [Atmega16U2](http://www.atmel.com/devices/ATMEGA16U2.aspx) ซึ่งทำหน้าที่เป็น [USB-to-Serial convertor](http://www.ftdichip.com/Products/Cables/USBRS232.htm)

<br/>

## ทดลองจ่ายไฟ
จากนี้ไปเราก็มาลองจ่ายไฟให้กับเจ้าบอร์ด [UNO](https://www.arduino.cc/en/Main/arduinoBoardUno) กันครับการจ่ายไฟให้กับบอร์ดที่ง่ายและถูกที่สุดก็ผ่านสาย USB นั่นแหละครับโดยใช้สาย USB ที่มีหัวต่อเป็นแบบ type A-to-B ครับ
<br/>
![uno-cable](/assets/review-uno/uno-cable.jpg)
<br/>

หลังจากเราเสียบสาย USB เข้ากับคอมพิวเตอร์และบอร์ดเรียบร้อยแล้วให้สังเกตว่าจะมี [LED](https://en.wikipedia.org/wiki/Light-emitting_diode) สีส้มกระพริบถี่ๆ ประมาณ 2-3 วินาทีจากนั้นก็จะกระพริบทุกๆ ครึ่งวินาทีนั้นก็คือโปรแกรมที่ถูกติดตั้งมาจากโรงงานครับโดย [LED](https://en.wikipedia.org/wiki/Light-emitting_diode) สีส้มนั้นจะถูกต่อกับดิจิตอล I/O ขาที่ 13

สำหรับการแกะกล่อง Arduino [UNO](https://www.arduino.cc/en/Main/arduinoBoardUno) ก็จบเพียงแค่นี้ครับ เดี๋ยวไว้ว่างๆ จะมานำเสนอเกี่ยวกับการใช้งาน