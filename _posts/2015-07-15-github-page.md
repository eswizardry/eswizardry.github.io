---
layout: post
title: "การใช้งาน GitHub Page เพื่อโฮสเว็บไซต์ที่สร้างด้วย Jekyll"
comments: True
tags:
- github
- jekyll
- web
---

<a href="{{ page.url }}"><img src="/assets/github-pages-jekyll.jpg" /></a>
<!--more-->
หลังจากบล็อกที่แล้วได้นำเสนอการสร้างเว็บไซต์ด้วย [Jekyll](http://jekyllrb.com/) กันไปแล้วต่อไปเราจะมาดูวิธีการใช้งานและโฮสต์เว็บด้วย [GitHub Pages](https://pages.github.com/) กัน

## ทำไมต้องโฮสต์เว็บไซต์ที่ GitHub Page?
- <strong>ฟรี!</strong> GitHub ให้เราสามารถโฮสต์เว็บส่วนตัวได้แบบฟรีๆ 1 เว็บ
- <strong>ง่าย</strong> Jekyll นั้นถูกสร้างมาเพื่อใช้กับ GitHub เพราะว่าเว็บที่จะโฮสต์บน GitHub ได้ต้องเป็น static website (สร้างจาก HTML&CSS และ JavaScript เท่านั้น) ซึ่ง Jekyll เองก็เป็น static site genarator
- <strong>Git practicing</strong> ได้เรียนรู้การใช้งานใช้งาน Git และ GitHup ไปในตัว

<br />

## สิ่งที่จำเป็นต้องมีก่อนการใช้งาน GitHub Page
- Git ถ้ายังไม่มีให้ไป [Download](https://git-scm.com/download) และ install ก่อน
- GitHub user ถ้ายังไม่มีก็สามารถสมัครใช้งานใหม่ได้ที่ [GitHub](https://github.com/)

ถ้ามีครบแล้วก็ไปขั้นตอนต่อไปเลย

<br />

## สร้าง Repository บน GitHub
- ให้ล็อกอินเข้าไปที่ GitHup user ของเราเพื่อสร้าง repository ใหม่ <strong>+New repository</strong>

![new-repo](/assets/gh-page/new-repo.jpg)

- จากนั้นก็สร้าง repository โดยใช้ชื่อ reposotory เป็นไปตามรูปแบบนี้เท่านั้น `Username.github.io` ถ้าเป็นรูปแบอื่นไม่ได้ รวมทั้งต้องกำหนด public ด้วยเพราะว่าเราจะสร้างเว็บซึ่งต้องให้คนอื่นเข้าถึงด้วย

![create-repo](/assets/gh-page/create-repo.jpg)

<br />

## โคลน repository ที่เราพึ่งสร้างลงมาที่เครื่องเรา
- เปิด terminal ขึ้นมา (จะใช้ command prompt, Git bash อื่นๆ) แล้วสร้าง folder ที่จะใช้ทำงาน
{% highlight sh linenos %}
$ mkdir /path/to/source-code
$ cd /path/to/source-code
{% endhighlight %}
    
- ไปที่ GitHub repositoy ของเราแล้ว copy URL ของ repository ที่เราสร้างขึ้นมา

![copy-to-clipboard](/assets/gh-page/copy-to-clipboard.jpg)

<br />

- โคลน repository โดยใช้คำสั่ง Git
{% highlight sh linenos %}
$ git clone https://github.com/username/username.github.io.git
$ cd username.github.io
{% endhighlight %}

<br />

## ทดสอบการอัพโหลดไฟล์ขึ้น GitHub ด้วยคำสั่ง Git
- สร้างไฟล์ใหม่ไว้ใน folder ของที่เราทำงานอยู่ให้ชื่อ `index.html`
- โดยในไฟล์ให้พิมพ์ช้อความ `Hello World`เข้าไป
{% highlight sh linenos %}
$ git add index.html
...

$ git commit index.html -m “Initial commit with my Hello world”
...

$ git push origin master
...
{% endhighlight %}
    
- เสร็จเรียบร้อย ให้เปิดบราวเซอร์ขึ้นมาแล้วเข้าไปที่ URL ของ repository เรา "https://<strong>username</strong>.github.io"
ก็จะเจอกับข้อความ <br />

> Hello World

<br />

## อัพโหลดเว็บไซต์ที่สร้างด้วย [Jekyll](https://eswizardry.github.io/2015/07/12/introducing-jekyll/) จาก[บล็อก](https://eswizardry.github.io/2015/07/12/introducing-jekyll/)ที่แล้วไปที่ GitHup Page
- copy ไฟล์ที่อยู่ในโฟลเดอร์ "my-awesome-site" ทั้งหมดไปแทนที่ไฟล์ในโฟลเดอร์ที่เราโคลนมาเมื่อก่อนหน้าจากนั้นก็ใช้คำสั่ง Git เพื่ออัพไฟล์ไปที่ GitHub
{% highlight sh linenos %}
$ git add -A
...

$ git commit -m “Add Jekyll”
...

$ git push origin master
...
{% endhighlight %}
    
สำเร็จแล้ว!
