---
layout: post
title: "รู้จักกับ Arduino"
comments: True
description: " Arduino นั้นเดิมทีถูกพัฒนาขึ้นมาเพื่อเป็นเครื่องมือในการสอนนักศึกษา ในปี 2005 โดย Massimo Banzi และ David Cuartielles ซึ่งก็ประสบความสำเร็จเป็นอย่างมากในแง่ของการสอน จากนั้นก็แพร่หลายมาสู่นักประดิษฐ์ ศิลปิน และ นักพัฒนาทั่วโลก"
tags:
- arduino
---

<a href="{{ page.url }}"><img src="/assets/intro-arduino/arduino-logo.jpg" /></a>
<!--more-->

[Arduino](https://www.arduino.cc/) (ออกเสียงว่า อา-ดู-อี-โน่) หลายคนอาจคิดว่าผมมาแนะนำนักฟุตบอลดาวรุ่งจาก อิตาลี แต่จริงๆ แล้วเจ้าตัว [Arduino](https://www.arduino.cc/) นี้ก็คือบอร์ดไมโครคอนโทรลเลอร์ขนาดเล็กที่มีพอร์ตซึ่งสามารถเชื่อมต่อกับคอมพิวเตอร์และทำให้คอมพิวเตอร์มีความสามารถในการในการรับสัญญาณจากอุปกรณ์ภายนอกและควบคุมอุปกรณ์ภายนอกได้มากกว่าที่คอมพิวเตอร์ทั่วไปจะทำได้

## กว่าจะมาเป็น [Arduino](https://www.arduino.cc/) ในทุกวันนี้
> [Arduino](https://www.arduino.cc/) นั้นเดิมทีถูกพัฒนาขึ้นมาเพื่อเป็นเครื่องมือในการสอนนักศึกษา ในปี 2005 โดย [Massimo Banzi](http://www.massimobanzi.com/) และ [David Cuartielles](https://twitter.com/dcuartielles) ซึ่งก็ประสบความสำเร็จเป็นอย่างมากในแง่ของการสอน จากนั้นก็แพร่หลายมาสู่นักประดิษฐ์ ศิลปิน และ นักพัฒนาทั่วโลก
และสิ่งที่ทำให้ [Arduino](https://www.arduino.cc/) ประสบความสำเร็จเป็นอย่างมากคือบอร์ด [Arduino](https://www.arduino.cc/) นั้นถูกออกแบบภายใต้สัญญาแบบ [Creative Commons License](http://creativecommons.org/) ทำให้เกิดการต่อยอดและสร้างบอร์ดทางเลือกออกมาได้อย่างอิสระ

<br/>
![arduino-uno](/assets/intro-arduino/arduino-uno.jpg)
<br/>

โดยเจ้าบอร์ด [Arduino](https://www.arduino.cc/) นี้จะมี I/O ซึ่งสามารถเชื่อมต่อเข้ากับอุปกรณ์และเซนเซอร์ได้มากมายยกตัวอย่างเช่น มอเตอร์, รีเลย์, เซนเซอร์แสง, ลำโพง และอื่นๆ อีกมากมาย
และ [Arduino](https://www.arduino.cc/) นี้เราสามารถที่จะโปรแกรมให้มันถูกควบคุมโดยคอมพิวเตอร์ หรือเราจะโปรแกรมให้ทำงานแบบ stand alone ก็ได้
ตัวบอร์ดนั้นถูกออกแบบภายใต้โครงการแบบโอเพนซอร์ส ซึ่งนั่นก็หมายความว่าใครก็สามารถที่จะนำแบบของ [Arduino](https://www.arduino.cc/) มาสร้างเองได้ จึงทำให้ปัจจุบันจะมีบอร์ดที่ไม่ใช่ official ออกมาขายในราคาถูกอย่างมากมายไม่ว่าจะเป็น

#### [Freeduino](http://www.freeduino.org/freeduino_open_designs.html)
![arduino-uno](/assets/intro-arduino/arduino-freeduino.jpg)
<br/>

#### [Roboduino](https://en.wikipedia.org/wiki/File:DFRobot_Arduino.jpg)
![roboduino](/assets/intro-arduino/arduino-roboduino.jpg)
<br/>

#### [Seeduino](http://www.seeedstudio.com/wiki/Seeeduino_v3.0)
![arduino-seeeduino](/assets/intro-arduino/arduino-seeeduino.jpg)
<br/>

> แม้ว่าตัวฮาร์ดแวร์ของ [Arduino](https://www.arduino.cc/) นั้นจะเป็นโอเพนซอร์สแต่ชื่อ [Arduino](https://www.arduino.cc/) นั้นสงวนลิขสิทธิ์นะครับ


## ทำไมต้องเป็น [Arduino](https://www.arduino.cc/)
หลายคนที่เล่่นหรือทำงานเกี่ยวกับไมโครคอนโทรลเลอร์อยู่แล้วก็อาจจะสงสัยว่าทำไมต้องใช้ [Arduino](https://www.arduino.cc/) ด้วยทั้งที่มีบอร์ดไมโครคอนโทรลเลอร์แบบนี้เยอะแยะ
ความพิเศษของเจ้า [Arduino](https://www.arduino.cc/) อยู่ที่ตัวฮาร์ดแวร์และซอฟต์แวร์นั้นถูกออกแบบมาให้ง่ายต่อการนำไปพัฒนาและใช้งานได้โดยที่ไม่จำเป็นต้องเป็นมืออาชีพหรือศึกษามาทางด้านไฟฟ้าและอิเล็กทรอนิกส์มาก่อน

ส่วนข้างล่างนี้ก็เป็นการแจกแจงข้อดีของ [Arduino](https://www.arduino.cc/) ที่ผมแปลมาจาก [arduino.cc](http://www.arduino.cc/en/Guide/Introduction)

- <strong>ราคาถูก</strong>: บอร์ด [Arduino](https://www.arduino.cc/) นั้นมีราคาที่ถูกมากเมื่อเทียบกับบอร์ดไมโครคอนโทรลเลอร์อื่นและบอร์ดที่ถูกที่สุดเราสามารถที่จะประกอบได้เองอีกด้วย หรือบอร์ดสำเร็จรูปเราก็สามารถหาซื้อได้ในราคาประมาณ $50 เท่านั้นเอง

- <strong>สามารถทำงานได้หลายแพลตฟอร์ม</strong>: ซอฟต์แวร์ในการพัฒนานั้นสามารถทำงานได้ทั้งบน Windows, Macintosh OS X และ Linux สำหรับไมโครคอนโทรลเลอร์ส่วนมากจะทำงานได้บน Windows เท่านั้น

- <strong>ง่าย</strong>: ซอฟแวร์ในการพัฒนานั้นถูกออกแบบมาให้ใช้งานง่ายสำหรับมือใหม่ แต่ก็ยังคงความยืดหยุ่นและมีความสามรถครบครันสำหรับมืออาชีพ สำหรับคุณครูหรือผู้สอนสามารถที่จะใช้ [Arduino](https://www.arduino.cc/) ซึ่งอยู่บนพื้นฐานของแพลตฟอร์ม [Processing](https://processing.org/) ในการสอนเขียนโปรแกรมเพื่อให้นักเรียนนักศึกษาสามารถเข้าใจการเขียนโปรแกรมได้ดียิ่งขึ้น

- <strong>โอเพนซอร์ส</strong>: อย่างที่กล่าวไปแล้วว่า [Arduino](https://www.arduino.cc/) นั้นเป็นแพลตฟอร์มที่เปิดเผยวงจรและซอร์สโค้ดซึ่งใครๆ ก็สามารถสร้างหรือนำไปต่อยอดได้


## ตัวอย่างของบอร์ดชีลด์ที่ได้รับความนิยมก็อย่างเช่น
นอกจากบอร์ด [Arduino](https://www.arduino.cc/) แล้วเรายังได้เห็นการต่อยอดของฮาร์ดแวร์ออกมาในรูปแบบของ [Shield (ชีลด์)](https://www.arduino.cc/en/Main/Products)  ซึ่งเป็นบอร์ดเสริมช่วยเพิ่มความสามารถให้กับ [Arduino](https://www.arduino.cc/) และลดการบัดกรีได้ทำให้การพัฒนาหรือประดิษฐ์อุปกรณ์ด้วยไมโครคอนโทรลเลอร์ง่ายขึ้นไปอีกขั้น

<br/>

#### [Ethernet Shield](https://www.arduino.cc/en/Main/ArduinoEthernetShield)
![shield-ethernet](/assets/intro-arduino/shield-ethernet.jpg)
<br/>

#### [Motor Shield](https://www.arduino.cc/en/Main/ArduinoMotorShieldR3)
![shield-motor](/assets/intro-arduino/shield-motor.jpg)

<br/>

#### [Proto Shield](https://www.arduino.cc/en/Main/ArduinoProtoShield)
![shield-proto](/assets/intro-arduino/shield-proto.jpg)

<br/>

#### [GSM Shield](https://www.arduino.cc/en/Main/ArduinoGSMShield)
![shield-gsm](/assets/intro-arduino/shield-gsm.jpg)
