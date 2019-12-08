# Part 1: Bioinformatics analyses of genomics sequence
Written by Shikai Liu and Zhanjiang Liu.
Translated by Jiratchaya Nuanpirom

## Chapter 1: Introduction to Linux and command line tools for bioinformatics
Chapter นี้จะพูดถึงการใช้ระบบปฏิบัติการ Linux (Linux Operating System) ในทางชีวสารสนเทศ ว่าทำไมต้องเป็น Linux รวมไปถึงการใช้งานพื้นฐาน โดยการพิมพ์คำสั่งลงไปแล้วให้ระบบปฏิบัติการรันออกมา

สาเหตุที่ต้องเป็น Linux OS เพราะว่าระบบปฏิบัติการนี้ถูกพัฒนาขึ้นมาให้มีความสเถียรกว่า Windows ตัวโปรแกรมชีวสารสนเทศหลายๆโปรแกรม พัฒนาขึ้นบนระบบปฏิบัติการ Linux เนื่องจาก มีความสามารถในการ handle ไฟล์ที่มีตัวอักษรมากๆๆๆๆ เป็นอย่างดี  เช่น พวกไปที่มี biological sequences หรือตัวเลข ไฟล์จากการวิเคราะห์ omics ต่างๆ หรืออะไรก็ตามที่ไม่ใช่ไฟล์รูปภาพหรือวีดิโอ ทำให้ผู้พัฒนาโปรแกรมชีวสารสนเทศส่วนใหญ่หันมาพัฒนาโปรแกรมบนระบบปฏิบัติการ Linux มากกว่า อีกทั้งการทำงานบนคอมพิวเตอร์ขั้นสูง (High Performance Computing units) เช่น server, computer cluster หรือ supercomputer ฯลฯ จะเป็นระบบ multiuser with multitasking คือ ในเครื่องเดียวกันสามารถมี user ได้หลายๆคน และทำงานได้พร้อมๆกัน 

### Overview of Linux
ระบบปฏิบัติการ Linux ประกอบด้วย 3 ส่วนหลักๆ คือ เปลือก (Shell),เนื้อใน (kernel) และโปรแกรม (Program) ทั้งสามส่วนนี้ถูกบรรจุลงในส่วนที่เรียกว่า hardware โดยผู้ใช้งาน (User) เป็นคนที่จะคอยสั่งให้ทำอะไรๆ ก็ตาม ลองนึกถึงเมล็ดพืชว่ามันจะมีส่วนประกอบประมาณนั้น ตามรูปนี้

![ส่วนประกอบของ Linux ได้แก่ Shell, Kernel, Program. ](https://github.com/prasert05/mbbtk/blob/master/Bioinformatics-in-Aquaculture_synopsis/img/linux_structure%402x.png)

* __Kernel__ คือแกนกลางหรือสิ่งที่บ่งบอกว่าเป็น Linux กล่าวคือ ถ้าเป็น Windows kernel ของ Windows จะมีให้เห็นชัดๆ ใน drive C นั่นแหละ พวก Program file หรือ systems32 นั่นแหละ คือ kernel ของ windows ส่วนของ Linux kernel จะเก็บโปรแกรมในโฟลเดอร์ `opt/` และเก็บ shortcut ของโปรแกรมนั้นๆ ใน folder `bin/` เหมือนกับที่ windows เก็บ shortcut ใน start menu อะไรประมาณนั้นแหละ 

* __Program__ คือ ชุดคำสั่ง, code, script, software อะไรก็ตามที่รับคำสั่งมาจาก Shell ซึ่งตัว Program จะทำงานอะไรก็ได้เเล้วแต่ว่าจะไปยุ่งกับส่วน kernel หรือไม่ ซึ่งถ้าตัว Program เข้าไปยุ่งกับ kernel จะทำให้เกิดผลกระทบใหญ่ๆ เช่น การ update, การ format เครื่อง, การ set firewall เป็นต้น ซึ่งจะเห็นได้ว่าคำสั่งจาก Shell ที่สั่งให้ตัวโปรแกรมไปยุ่งกับ Kernel ทุกครั้ง จะต้องใช้รหัสผ่านของผู้ดูแลระบบหรือ root ทุกครั้ง

* __Shell__ ถ้าเป็น Windows ก็คือ command prompt หรือไม่ก็ PowerShell นั่นแหละ คือส่วนที่รับคำสั่งจากผู้ใช้งาน (User) ว่าต้องการให้ Program ทำอะไร มันก็จะทำตามที่รับคำสั่งมาจาก Shell นี่แหละ ซึ่งการสั่งงานระบบปฏบัติการ Linux จะต้องใช้ภาษาเฉพาะสำหรับ Linux ที่เรียกว่า ภาษา Bash (Bourne Again Shell) ซึ่งตัวอย่างภาษา Bash พื้นฐานจะกล่าวถึงเป็นลำดับถัดไป

### Bash Scripting
> ยกมาจาก https://files.fosswire.com/2007/08/fwunixref.pdf

* คำสั่งเกี่ยวกับการจัดการไฟล์
ต้องการ list ดูว่าใน directory ปัจจุบันมีอะไรด้านในบ้าง

```sh
ls
# หรือ
ll
```

ต้องการทราบที่อยู่ของเราตอนนี้ว่าเราอยู่ใน directory ไหน เป็น directory ย่อยของใคร

```sh
# print working directory
pwd
```

ต้องการสร้าง/ลบ/ file หรือ directory และการ copy/move file หรือ directory ไปอีกที่หนึ่ง

```sh
# ต้องการสร้าง directory ชื่อ my_dummy
mkdir my_dummy

# ต้องการลบ directory ชื่อ my_dummy
rm -rf my_dummy

# rm คือการ remove พารามิเตอร์ -r คือการบอกว่าสิ่งที่ต้องการลบเป็น directory, -f คือ force remove
# .

# ต้องการ duplicate file ชื่อ fish1 เป็น fish1.txt & fish2.txt
cp fish1.txt fish2.txt

# ต้องการ copy file fish1.txt ไปไว้ใน directory ชื่อ aquaculture แล้วตั้งชื่อเป็น aquacilture_fish.txt
cp fish1.txt aquaculture/aquaculture_fish.txt

# ต้องการลบไฟล์ fish1.txt
rm fish1.txt
```

ต้องการเปลี่ยน directory จากตอนนี้อยู่ที่ `home/jiratchaya/` ไปอยู่ที่ `home/jiratchaya/aquaculture`
```sh
cd aquaculture

# ถ้าต้องการ กลับขึ้นไป 1 ขั้น จากเมื่ออกี๊
cd ..

# ถ้ากลับไปหน้า Home
cd
```