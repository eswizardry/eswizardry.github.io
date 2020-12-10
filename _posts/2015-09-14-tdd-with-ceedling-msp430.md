---
layout: post
title: "TDD for Embedded C using Ceedling with MSP430"
comments: True
description: "Ceedling เป็นเครื่งมือที่ช่วยในการ build โปรเจ็คของภาษา C ซึ่งใช้ rake (make ไฟล์ของภาษา Ruby) เป็นตัว build โดย Ceedling จะรวบรวมเครื่องมือที่จำเป็นสำหรับการพัฒนาซอฟแวร์ตามแบบ TDD มารวมกันเพื่อความสะดวกและง่ายในการใช้งาน โดยประกอบไปด้วย Unity (unit test framework), CMock (mock up generator สำหรับภาษา C) และ CException (Exeption handler สำหรับภาษา C)"
tags:
- tdd
- msp430
---

<a href="{{ page.url }}"><img src="/assets/try-tdd-msp430/tdd-circle-of-life.jpg" /></a>
<!--more-->

หลังจากที่ก่อนหน้านี้ได้ลอง TDD บน MSP430 โดยใช้ ASSERT มาโครแบบง่ายๆ กันไปแล้ววันนี้จะมาแนะนำ framework ตัวหนึ่งที่หน้าสนใจสำหรับใช้ในการพัฒนาแบบ TDD และถึงแม้ว่าจะไม่ได้พัฒนาโดยใช้ TDD ก็ยังสามารถใช้ framework ตัวนี้ในการสร้าง Unit test ได้สำหรับทดสอบโค้ดหรือแม้แต่ใช้เป็น  build tool ก็ได้เช่นกัน

##[CEEDLING](http://www.throwtheswitch.org/ceedling/) คืออะไร?
Ceedling เป็นเครื่งมือที่ช่วยในการ build โปรเจ็คของภาษา C ซึ่งใช้ rake (make ไฟล์ของภาษา Ruby) เป็นตัว build โดย Ceedling จะรวบรวมเครื่องมือที่จำเป็นสำหรับการพัฒนาซอฟแวร์ตามแบบ TDD มารวมกันเพื่อความสะดวกและง่ายในการใช้งาน โดยประกอบไปด้วย Unity (unit test framework), CMock (mock up generator สำหรับภาษา C) และ CException (Exeption handler สำหรับภาษา C)

##เตรียมความพร้อม
ก่อนจะไปต่อขอให้ติดตั้ง Ceedling ตามลิงค์ข้างล่างนี้ก่อนครับ
[http://www.throwtheswitch.org/ceedling/](http://www.throwtheswitch.org/ceedling/)

##มาลองใช้งานกันเลย
หลังจากติดตั้ง [CEEDLING](http://www.throwtheswitch.org/ceedling/)  เสร็จแล้วก็ให้เปิด terminal ขึ้นมาแล้ว cd ไปที่ฟลเดอร์ที่เราจะใช้ทำงานแล้วก็ป้อนคำสั่ง `ceedling example temp_sensor` เพื่อลองเล่นกับตัวอย่างกันก่อนโดย [CEEDLING](http://www.throwtheswitch.org/ceedling/) จะทำการสร้างตัวอย่างขึ้นมาแล้วได้เอาต์พุตตามนี้

{% highlight sh %}
eswizardry@eswizardry-PC/d/Documents/temp_sensor
$ ceedling example temp_sensor
      create  temp_sensor/vendor/ceedling/docs/CeedlingPacket.pdf
      create  temp_sensor/vendor/ceedling/docs/CExceptionSummary.pdf
      create  temp_sensor/vendor/ceedling/docs/CMock Summary.pdf
      create  temp_sensor/vendor/ceedling/docs/Unity Summary.pdf
      create  temp_sensor/vendor/ceedling/plugins
      create  temp_sensor/vendor/ceedling/plugins/bullseye/assets/template.erb
      create  temp_sensor/vendor/ceedling/plugins/bullseye/bullseye.rake
      create  temp_sensor/vendor/ceedling/plugins/bullseye/config/defaults.yml
      create  temp_sensor/vendor/ceedling/plugins/bullseye/lib/bullseye.rb
................................
Example project 'temp_sensor' created!
 - Tool documentation is located in vendor/ceedling/docs
 - Execute 'rake -T' to view available test & build tasks

{% endhighlight %}

จากนั้นให้ cd เข้าไปที่โฟลเดอร์ที่ ceedling สร้างขึ้น
`cd temp_sensor`
แล้วก็สั่งรันคำสั่ง `rake -T` เพื่อที่จะดูว่าเราสามารถทำอะไรกับโปรเจ็คนี้ได้บ้าง

{% highlight sh %}
eswizardry@eswizardry-PC/d/Documents/temp_sensor
$ cd temp_sensor/

eswizardry@eswizardry-PC/d/Documents/temp_sensor
$ rake -T
rake clean                # Delete all build artifacts and temporary products
rake clobber              # Delete all generated files (and build artifacts)
rake environment          # List all configured environment variables
rake files:header         # List all collected header files
rake files:source         # List all collected source files
rake files:test           # List all collected test files
rake logging              # Enable logging
rake paths:source         # List all collected source paths
rake paths:support        # List all collected support paths
rake paths:test           # List all collected test paths
rake summary              # Execute plugin result summaries (no build trigg...
rake test:*               # Run single test ([*] real test or source file n...
rake test:all             # Run all unit tests
rake test:delta           # Run tests for changed files
rake test:path[dir]       # Run tests whose test path contains [dir] or [di...
rake test:pattern[regex]  # Run tests by matching regular expression pattern
rake verbosity[level]     # Set verbose output (silent:[0] - obnoxious:[4])
rake version              # Display build environment version info

{% endhighlight %}

 จากนั้นลองคำสั่ง `rake test:all` เพื่อทดสอบการทดสอบทั้งหมด

{% highlight sh %}
eswizardry@eswizardry-PC/d/Documents/temp_sensor
$ rake test:all


Test 'TestAdcConductor.c'
-------------------------
Creating mock for AdcModel...
...

Test 'TestAdcHardware.c'
------------------------
Creating mock for AdcHardwareConfigurator...
...

Test 'TestAdcModel.c'
---------------------
Creating mock for TaskScheduler...
...

Test 'TestExecutor.c'
---------------------
Creating mock for Model...
...


Test 'TestMain.c'
-----------------
Creating mock for Executor...
Generating runner for TestMain.c...
Compiling TestMain_runner.c...
Compiling TestMain.c...
Compiling MockExecutor.c...
Compiling Main.c...
Linking TestMain.out...
build/test/out/Main.o: In function `main':
d:\Documents\temp_sensor/src/Main.c:43: multiple definition of `main'
build/test/out/TestMain_runner.o:d:\Documents\temp_sensor/build/test/runners/Tes
tMain_runner.c:72: first defined here
collect2.exe: error: ld returned 1 exit status
ERROR: Shell command failed.
> Shell executed command:
'gcc.exe "build/test/out/TestMain_runner.o" "build/test/out/TestMain.o" "build/t
est/out/MockExecutor.o" "build/test/out/unity.o" "build/test/out/Main.o" "build/
test/out/cmock.o" -o "build/test/out/TestMain.out" -lm'
> And exited with status: [1].
...

-----------
TEST OUTPUT
-----------
[TestAdcConductor.c]
  - ""

[TestAdcHardware.c]
  - ""

[TestAdcModel.c]
  - ""

[TestExecutor.c]
  - ""

--------------------
OVERALL TEST SUMMARY
--------------------
TESTED:  17
PASSED:  17
FAILED:   0
IGNORED:  0

{% endhighlight %}

ceedling จะทำการ build และสั่งรันการทดสอบทั้งหมดและแจ้งผลการทดสอบตามเอาต์พุตด้านบน


##มาสร้างโปรเจ็คใหม่ด้วย Ceedling กัน
หลังจากลองทดสอบกับตัวอย่างกันไปแล้วทีนี้เรามาสร้างโปรเจ็คใหม่ตั้งแต่เริ่มต้นกันเลย
ขั้นแรกให้ cd ออกจากโปรเจ็คตัวอย่างก่อน `cd ..` จากนั้นให้ป้อนคำสั่ง `cd temp_sensor`
ceedling ก็จะทำการสร้างไฟล์ที่จำเป็นสำหรับโปรเจ็คใหม่ของเรา

{% highlight sh %}
eswizardry@eswizardry-PC/d/Documents/
$ ceedling new try-embedded-tdd
      create  try-embedded-tdd/vendor/ceedling/docs/CeedlingPacket.pdf
      create  try-embedded-tdd/vendor/ceedling/docs/CExceptionSummary.pdf
      create  try-embedded-tdd/vendor/ceedling/docs/CMock Summary.pdf
      create  try-embedded-tdd/vendor/ceedling/docs/Unity Summary.pdf
      create  try-embedded-tdd/vendor/ceedling/plugins
...................................

Project 'try-embedded-tdd' created!
 - Tool documentation is located in vendor/ceedling/docs
 - Execute 'rake -T' to view available test & build tasks

{% endhighlight %}

หลังจากนั้นก็ cd เข้าไปที่โปรเจ็คที่เราพึ่งสร้างขึ้นมา `cd try-embedded-tdd/`
ถัดมาก็ป้อนคำสั่ง `rake module:create[led_driver]`เพื่อสร้างไฟล์หรือโมดูลที่จะใช้ในการพัฒนา งานของเราโดยในที่นี้ผมจะขอยกตัวอย่างการพัฒนา led driver แบบง่ายละกันโดยให้ module นี้ชื่อว่า led_driver
หลังจากป้อนคำสั่ง ceedling ก็จะทำการสร้างไฟล์ `led_driver.c`, `led_driver.h` และ ไฟล์ `test_led_driver.c` เพื่อเอาไว้พัฒนาและเขียนการทดสอบสำหรับโมดูลที่สร้างขึ้น

{% highlight sh %}
eswizardry@eswizardry-PC/d/Documents/try-embedded-tdd
$ rake module:create[led_driver]
Generating 'led_driver'...
mkdir -p ./test/.
mkdir -p ./src/.
File ./test/./test_led_driver.c created
File ./src/./led_driver.c created
File ./src/./led_driver.h created

{% endhighlight %}


ทีนี้เราก็มาลองสั่งรันการทดสอบโมดูลที่เราพึ่งสร้างขึ้นมาโดยใช้คำสั่ง
`rake test:all`

{% highlight sh %}
eswizardry@eswizardry-PC/d/Documents/try-embedded-tdd
$ rake test:all


Test 'test_led_driver.c'
------------------------
Generating runner for test_led_driver.c...
Compiling test_led_driver_runner.c...
Compiling test_led_driver.c...
Compiling unity.c...
Compiling led_driver.c...
Compiling cmock.c...
Linking test_led_driver.out...
Running test_led_driver.out...

-----------
TEST OUTPUT
-----------
[test_led_driver.c]
  - ""

--------------------
IGNORED TEST SUMMARY
--------------------
[test_led_driver.c]
  Test: test_module_generator_needs_to_be_implemented
  At line (14): "Implement me!"

--------------------
OVERALL TEST SUMMARY
--------------------
TESTED:  1
PASSED:  0
FAILED:  0
IGNORED: 1

{% endhighlight %}

โดยผลทดสอบที่ได้จะเห็นว่าไม่มีการทดสอบเกิดขึ้นเพราะเรายังไม่ได้สร้างการทดสอบใดๆ เลยยกเว้นการทดสอบที่ ceedling สร้างขึ้นโดยอัตโนมัติ และใส่สถานะว่าให้ทำการข้ามการทดสอบนี้ไว้และมีการเจ้งเตือนรายละเอียดไว้ที่ดังนี้

{% highlight sh %}

--------------------
IGNORED TEST SUMMARY
--------------------
[test_led_driver.c]
  Test: test_module_generator_needs_to_be_implemented
  At line (14): "Implement me!"

--------------------
OVERALL TEST SUMMARY
--------------------
TESTED:  1
PASSED:  0
FAILED:  0
IGNORED: 1

{% endhighlight %}

โดยถ้าเราไปเปิดไฟล์ `test_led_drive.c` ดูก็จะพบกับโค้ดที่ ceedling สร้างขึ้นดังนี้

###test_led_driver.c
{% highlight c %}
#include "unity.h"
#include "led_driver.h"

void setUp(void)
{
}

void tearDown(void)
{
}

void test_module_generator_needs_to_be_implemented(void)
{
    TEST_IGNORE_MESSAGE("Implement me!");
}

{% endhighlight %}


ต่อไปก็แก้ไขไฟล์ `test_led_driver.c` ตามตัวอย่างข้างล่างเพื่อเพิ่มการทดสอบเข้าไปโดยผมได้ทำการเขียนโค้ดสำหรับการทดสอบก่อนตามหลักการของ TDD โดยจากการทดสอบที่สร้างขึ้นผมได้เขียนเพื่อทดว่าหลังจากที่เรียกฟังก์ชัน `ledDriver_Initial()` แล้วสถานะ `LED` ต้องเป็น `0` เท่านั้นนอกเหนือจากนี้คือไม่ผ่าน (fail)

###test_led_driver.c
{% highlight c %}
#include "unity.h"
#include "led_driver.h"

void setUp(void)
{
}

void tearDown(void)
{
}

void test_LedOffAfterInitial(void)
{
    unsigned char ledPort;

    ledPort = 0xFF;
    ledDeriver_Initial(&ledPort);
    TEST_ASSERT_EQUAL(0, ledPort);
}

{% endhighlight %}

จากนั้นก็แก้ไข header ไฟล์ `led_driver.c` และ `led_driver.h` เพื่อให้ไฟล์ `test_led_driver.c` สามารถเรียกใช้งานฟังก์ชัน `ledDeriver_Initial()` ได้

###led_driver.c
{% highlight c %}
#include "led_driver.h"


void ledDeriver_Initial(unsigned char  *ledAddress) {

}

{% endhighlight %}

###led_driver.h
{% highlight c %}
#ifndef led_driver_H
#define led_driver_H

void ledDeriver_Initial(unsigned char  *ledAddress);

#endif // led_driver_H

{% endhighlight %}

และหลังจากเขียนการทดสอบเสร็จเราจะทำการทดสอบกันโดยคาดหวังว่าผลการทดสอบต้องไม่ผ่าน (fail) เพราะเรายังไม่ได้เขียนโค้ดให้กับ `ledDeriver_Initial()` เลยมีแค่ prototype ให้เรียกใช้งานเท่านั้น
แต่ก็อาจมีกรณีที่มันผ่านโดยเราไม่ได้ตั้งใจอยู่เหมือนกันถ้าเราเขียนการทดสอบผิด อย่างเช่นลืมให้ค่าตั้งต้น (initial) กับตัวแปรที่ทำการทดสอบเราก็อาจจะได้ค่าที่สุ่มมาหรือไม่เป็นไปตามความคาดหมาย

<br>

> "การเขียนการทดสอบให้ไม่ผ่าน (fail) นี้ถือเป็นหัวใจของ TDD เลยทีเดียวหากไม่ได้เขียนการทดสอบและทดสอบให้ไม่ผ่าน (fail) ก่อนไปเขียนโค้ดที่ใช้งาน (production code) แล้ว ก็คงไม่สามารถเรียกการพัฒนาของเราว่าทำตามหลักการ TDD ได้เลย"

<br>

{% highlight sh %}
eswizardry@eswizardry-PC/d/Documents/try-embedded-tdd
$ rake test:all


Test 'test_led_driver.c'
------------------------
Generating runner for test_led_driver.c...
Compiling test_led_driver_runner.c...
Compiling test_led_driver.c...
Compiling led_driver.c...
Linking test_led_driver.out...
Running test_led_driver.out...

-----------
TEST OUTPUT
-----------
[test_led_driver.c]
  - ""

-------------------
FAILED TEST SUMMARY
-------------------
[test_led_driver.c]
  Test: test_LedOffAfterInitial
  At line (18): "Expected 0 Was 255"

--------------------
OVERALL TEST SUMMARY
--------------------
TESTED:  1
PASSED:  0
FAILED:  1
IGNORED: 0

---------------------
BUILD FAILURE SUMMARY
---------------------
Unit test failures.

{% endhighlight %}


ทีนี้เราก็มาถึงขั้นตอนการเขียนโค้ด (production code) เพื่อให้ผ่านการทดสอบกันแล้ว
โดยตามหลัการของ TDD เริ่มแรกให้เราเขียนโค้ดที่น้อยที่สุดที่สามารถผ่านการทดสอบได้เข้าไปหากเราทดสอบได้ผ่านแล้วค่อยมาทำการ refactor กันทีหลัง
โดยผมเพิ่มโค้ดเข้าไปใน `led_driver.c`ดังนี้

###led_driver.c
{% highlight c %}
#include "led_driver.h"


void ledDeriver_Initial(unsigned char  *ledAddress) {
    *ledAddress = 0;
}

{% endhighlight %}


ต่อไปเรามาลองทำการทดสอบโค้ดที่เราเพิ่มเข้าไปดูว่าสามารถผ่านการทดสอบได้หรือไม่
โดยป้อนคำสั่ง `rake test:all`

{% highlight sh %}
eswizardry@eswizardry-PC/d/Documents/try-embedded-tdd
$ rake test:all


Test 'test_led_driver.c'
------------------------
Compiling led_driver.c...
Linking test_led_driver.out...
Running test_led_driver.out...

-----------
TEST OUTPUT
-----------
[test_led_driver.c]
  - ""

--------------------
OVERALL TEST SUMMARY
--------------------
TESTED:  1
PASSED:  1
FAILED:  0
IGNORED: 0

{% endhighlight %}

หลังจากนั้นก็ให้เราทำการเพิ่มโค้ดการทดสอบและโค้ดการทำงานในส่วนที่เหลือไปเรื่อยๆ จนกว่าจะได้ฟังก์ชันการทำงานทั้งหมดที่เราต้องการโดยสำหรับโค้ดตัวอย่างทั้งหมดสามรถดูเพิ่มเติมได้ที่ [GitHub](https://github.com/eswizardry/try-embedded-tdd)


<br>

##แก้ไขให้โปรเจ็คคอมไพล์และทดสอบบน IAR-MSP430 คอมไพเลอร์และ C-spy simulator
ให้เปิดไฟล์ `project.yml`ขึ้นมาแก้ไขโดยผมจะนำเสนอแค่ในส่วนหลักๆ ที่น่าสนใจเท่านั้นส่วนที่เหลือให้ดูได้จากไฟล์ที่ [GitHub](https://github.com/eswizardry/try-embedded-tdd)

โดยหลักๆ ที่ต้องทำการแก้ไขก็จะเป็นการเพิ่ม complier option ของ IAR เข้าไปแค่นั้นเองโดยเราสามารถใช้ compiler option ที่มาจาก output เวลาที่เราทำการ build โดย IAR ได้เลย
ซึ่งก่อนที่จะกด build ให้เราเปิด option ของ IAR IDE ที่ `IAR Embedded Workbench IDE > Tools > Options... > IDE Options > Messages > Show build messages > select 'All'`

รายละเอียดเพิ่มเติมดูได้จาก [IAR Technical Note 47884](http://supp.iar.com/Support/?note=47884)

###test compiler
{% highlight ruby %}
  :test_compiler:
    :executable: icc430.exe
    :arguments:
    - "${1}"
    - -o "${2}"
    - --no_cse
    - --no_unroll
    - --no_inline
    - --no_code_motion
    - --no_tbaa
    - --debug
    - -D__MSP430GENERIC__
    - -e
    - --double=32
    - --dlib_config "C:\Program Files (x86)\IAR Systems\Embedded Workbench 6.5\430\LIB\DLIB\dl430fn.h"
    - -I"$": COLLECTION_PATHS_TEST_SUPPORT_SOURCE_INCLUDE_VENDOR
    - -Ol
    - --multiplier=16
    - --segment __data16=DATA16
    - --segment __data20=DATA20
    - --diag_suppress Pa050
    - --diag_suppress Pe111
    - -DTEST
{% endhighlight %}


###test linker
{% highlight ruby %}
:test_linker:
    :executable: xlink.exe
    :arguments:
    - "${1}"
    - -o "${2}"
    - -s __program_start
    - -f "C:\Program Files (x86)\IAR Systems\Embedded Workbench 6.5\430\config\lnk430f5438.xcl"
    - -f "C:\Program Files (x86)\IAR Systems\Embedded Workbench 6.5\430\config\multiplier.xcl"
    - -D_STACK_SIZE=50
    - -rt "C:\Program Files (x86)\IAR Systems\Embedded Workbench 6.5\430\lib\dlib\dl430fn.r43"
    - -D_DATA16_HEAP_SIZE=50
    - -s __program_start
    - -D_DATA20_HEAP_SIZE=50
{% endhighlight %}



ส่วนสุดท้ายสำหรับการทดสอบคือการแก้ไขค่าให้ การทดสอบของเรารันบน IAR simulator (IAR c-spy)

###test fixture
{% highlight ruby %}
  :test_fixture:
    :executable: D:\Documents\try-embedded-tdd\TestProj.cspy.bat
    :name: "msp430 simulator test fixture"
    :stderr_redirect: :win #inform Ceedling what model of $stderr capture to use
    :arguments:
    - "${1}"
{% endhighlight %}

และอีกส่วนหนึ่งที่ต้องแก้ไขคือ executable ไฟล์ นี้เราต้องแก้ไขค่าให้เป็น `.d43` ไม่อย่างนั้นจะไม่สามารถรันบน IAR c-spy ได้

{% highlight ruby %}
:extension:
  :executable: .d43
{% endhighlight %}


ต่อไปเรามาลองทำการทดสอบอีกครั้งกับ compiler และ simulator ของ IAR
ก่อนอื่นให้ทำการ clean build ก่อนหน้านี้ที่ใช้ GCC ก่อน

{% highlight sh %}
eswizardry@eswizardry-PC/d/Documents/try-embedded-tdd
$ rake clean

Cleaning build artifacts...
(For large projects, this task may take a long time to complete)


eswizardry@eswizardry-PC/d/Documents/try-embedded-tdd
$ rake clobber

Clobbering all generated files...
(For large projects, this task may take a long time to complete)

eswizardry@eswizardry-PC/d/Documents/try-embedded-tdd
$
{% endhighlight %}

จากนั้นป้อนคำสั่ง `rake test:all`
ก็จะพบกับ test output ที่เปลี่ยนไปโดยบอกรายละเอียดการทดสอบ โดยใช้ IAR c-spy แทน

{% highlight sh %}
eswizardry@eswizardry-PC/d/Documents/try-embedded-tdd
$ rake test:all


Test 'test_led_driver.c'
------------------------
Generating runner for test_led_driver.c...
Compiling test_led_driver_runner.c...
Compiling test_led_driver.c...
Compiling unity.c...
Compiling led_driver.c...
Compiling cmock.c...
Linking test_led_driver.d43...
Running test_led_driver.d43...

-----------
TEST OUTPUT
-----------
[test_led_driver.c]
  - ""
  - "d:\Documents\try-embedded-tdd>"C:\Program Files (x86)\IAR Systems\Embedde
Workbench 6.5\common\bin\cspybat" "C:\Program Files (x86)\IAR Systems\Embedded
orkbench 6.5\430\bin\430proc.dll" "C:\Program Files (x86)\IAR Systems\Embedded
orkbench 6.5\430\bin\430sim.dll"  build/test/out/test_led_driver.d43 --plugin
:\Program Files (x86)\IAR Systems\Embedded Workbench 6.5\430\bin\430bat.dll" -
ackend -B "--hardware_multiplier" "32" "--hwmult_type" "8" "-p" "C:\Program Fi
s (x86)\IAR Systems\Embedded Workbench 6.5\430\config\msp430fr5739.ddf" "--cor
430Xv2" "--data_model=small" "--iv_base" "0xFF90" "--odd_word_check" "-d" "sim
"--derivativeSim" "MSP430FR5739" "
  - ""
  - "     IAR C-SPY Command Line Utility V6.6.3.2839"
  - "     Copyright 2000-2013 IAR Systems AB."
  - ""
  - ""

--------------------
OVERALL TEST SUMMARY
--------------------
TESTED:  3
PASSED:  3
FAILED:  0
IGNORED: 0


eswizardry@eswizardry-PC/d/Documents/try-embedded-tdd
$
{% endhighlight %}

<br>

สำหรับไฟล์ทั้งหมดที่ใช้ในบทความนี้สามารถดาวน์โหลดไปลองเล่นกันได้ที่ [GitHub](https://github.com/eswizardry/try-embedded-tdd)

...<3
