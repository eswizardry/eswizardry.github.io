---
layout: post
title: "มาสร้างเว็บบล็อกด้วย Jekyll กันเถอะ"
comments: True
tags:
- jekyll
- web
---

<a href="{{ page.url }}"><img src="/assets/jekylllogo.jpg" /></a>
<!--more-->
<strong>สวัสดีชาวโลก</strong> นี่เป็นโพสต์แรกของเว็บบล็อกแห่งนี้ขอประเดิมด้วยแนะนำการสร้างเว็บบล็อกด้วย [Jekyll](http://jekyllrb.com/) และโฮสต์เว็บด้วย [GitHub Pages](https://pages.github.com/) ซึ่งเว็บบล็อกแห่งนี้ก็สร้างและโฮสต์โดยทั้งสองอย่างที่กล่าวมา<br />

## รู้จักกับ [Jekyll](http://jekyllrb.com/)

> Jekyll คือ [ruby gem](https://rubygems.org/) ซึ่งทำหน้าที่เป็น parsing engine เพื่อใช้ในการสร้างเว็บไซต์ [static websites](https://en.wikipedia.org/wiki/Static_web_page) โดยการ parsing จากไฟล์ templates, HTML & CSS, markdown, รูปภาพ และ อื่นๆ โดย Jekyll นี้จัดว่าเป็นหนึ่งใน [static site generator](https://staticsitegenerators.net/) โดยมีสโลแกนว่า <strong>"Simple, blog-aware, static sites"</strong>

## ติดตั้ง [Jekyll](http://jekyllrb.com/)
ก่อนที่จะเริ่มสร้างเว็บไซต์ด้วย [Jekyll](http://jekyllrb.com/) มาดูกันก่อนว่าเราต้องใช้อะไรบ้าง

### สิ่งที่จำเป็นต้องมีก่อนการสร้างเว็บด้วย Jekyll (Dependencies)
- [Ruby](https://www.ruby-lang.org/en/).
  - การติดตั้ง ruby นั้นตรงไปตรงมาให้ดับเบิ้ลคลิกไฟล์ติดตั้ง ruby ที่ดาวน์โหลดมาแล้วทำตาม installation guide ได้เลย แต่ตอนติดตั้งให้เลือกด้วยว่าให้ เพิ่ม ruby เข้าไปที่ system path ของ windows ด้วย
- [Ruby Devkit](https://www.ruby-lang.org/en/).
  - การติดตั้ง ruby devkit นั้นยุ่งยากนิดหน่อยอันนี้จะบอกวิธีการทำทีละขั้นตอนตามนี้
  - เปิด command prompt ขึ้นมาแล้วใช้คำสั่ง `ruby -v` เพื่อตรวจสอบเวอร์ชันของ ruby
  - เมื่อรู้เวอร์ชันแล้วก้อเข้าไปดาวน์โหลดตัวติดตั้ง [Devkit](http://rubyinstaller.org/downloads/) ที่สอดคล้องกับ ruby
  - ติดตั้งโดยดับเบิ้ลคลิกไฟล์ดาวน์โหลดมาเพื่อติดตั้ง อันนี้แนะนำว่าให้ติดตั้งไว้ที่ C:\Devkit
  - จากนั้นพิมพ์คำสั่ง `cd c:\DevKit` เพื่อเข้าไปยังโฟลเดอร์ที่ติดตั้งและใช้คำสั่ง `ruby dk.rb init` และ `ruby dk.rb install` ตามลำดับ
  - เพื่อความแน่ใจว่าติดตั้งเรียบร้อย ลองใช้คำสั่ง `gem install json --platform=ruby` และลองรัน ๋JSON ดู `ruby -rubygems -e "require 'json'; puts JSON.load('[42]').inspect"`
  - ถ้าไม่มีอะไรผิดพลาดก็จะได้ผลลัพธ์ตามด้านล่างนี้
    {% highlight sh linenos %}
    C:\Devkit>ruby -rubygems -e "require 'jso
    n'; puts JSON.load('[42]').inspect"
    [42]
    {% endhighlight %}

### Install Jekyll
ถ้ามีตามข้างบนครบแล้วก็มาติดตั้ง Jekyll กันเลย โดยเปิด command prompt ขึ้นมาแล้วก็พิมพ์คำสั่งสำหรับติดตั้ง `gem install jekyll` จากนั้นก็รอจนกว่าจะติดตั้งเสร็จ อันนี้ใช้เวลาพอสมควรขึ้นอยู่กับความเร็วของเครื่องและอินเตอร์เน็ต


## สร้างเว็บไซต์ใน 1 นาทีด้วย [Jekyll](http://jekyllrb.com/)
หลังจากติดตั้งเสร็จเรียบร้อยเราสามารถทดลองรันเว็บไซต์ตัวอย่างของ Jekyll โดยเปิด command prompt ขึ้นมาแล้ว cd ไปยัง directory ที่เราจะใช้ทำงาน อย่างของผมใช้ D:\doucuments ก็สามารถใช้ `cd D:\doucuments` จากนั้นก็พิมพ์คำสั่งตามด้านล่าง
{% highlight sh linenos %}
> gem install jekyll
> jekyll new my-awesome-site
> cd my-awesome-site
> jekyll serve
{% endhighlight %}

หลังจากรันคำสั่งด้านบนเสร็จจะได้ผลลัพธ์ตามนี้
![Jekyll-serve](/assets/cmd-jekyll-serve.jpg)

<br />
จากนั้นให้เปิดเว็บเบราเซอร์แแล้วป้อน [http://localhost:4000](http://localhost:4000)
![awesome-site](/assets/awesome-site-localhost4000.jpg)

<br />
แค่นี้เราก็ได้เว็บไซต์แรกที่สร้างด้วย [Jekyll](http://jekyllrb.com/) แล้วเห็นไหมว่าง่ายและใช้เวลาน้อยกว่าต้มมาม่าซะอีก

ทีแรกกะว่าจะรวมการโฮสต์เว็บที่สร้างขึ้นมาจาก Jekyll ด้วยแต่ขอยกไปไว้บล็อกถัดไปดีกว่า เดี๋ยวผมจะมานำเสนอเกี่ยวกับการโฮสต์เว็บไซต์ด้วย [GitHub Pages](https://pages.github.com/) ต่อ...<3
