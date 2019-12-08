# Part 1: Bioinformatics analyses of genomics sequence
Written by Shikai Liu and Zhanjiang Liu.

## Chapter 1: Introduction to Linux and command line tools for bioinformatics
Chapter นี้จะพูดถึงการใช้ระบบปฏิบัติการ Linux (Linux Operating System) ในทางชีวสารสนเทศ ว่าทำไมต้องเป็น Linux รวมไปถึงการใช้งานพื้นฐาน โดยการพิมพ์คำสั่งลงไปแล้วให้ระบบปฏิบัติการรันออกมา

สาเหตุที่ต้องเป็น Linux OS เพราะว่าระบบปฏิบัติการนี้ถูกพัฒนาขึ้นมาให้มีความสเถียรกว่า Windows ตัวโปรแกรมชีวสารสนเทศหลายๆโปรแกรม พัฒนาขึ้นบนระบบปฏิบัติการ Linux เนื่องจาก มีความสามารถในการ handle ไฟล์ที่มีตัวอักษรมากๆๆๆๆ เป็นอย่างดี  เช่น พวกไปที่มี biological sequences หรือตัวเลข ไฟล์จากการวิเคราะห์ omics ต่างๆ หรืออะไรก็ตามที่ไม่ใช่ไฟล์รูปภาพหรือวีดิโอ ทำให้ผู้พัฒนาโปรแกรมชีวสารสนเทศส่วนใหญ่หันมาพัฒนาโปรแกรมบนระบบปฏิบัติการ Linux มากกว่า อีกทั้งการทำงานบนคอมพิวเตอร์ขั้นสูง (High Performance Computing units) เช่น server, computer cluster หรือ supercomputer ฯลฯ จะเป็นระบบ multiuser with multitasking คือ ในเครื่องเดียวกันสามารถมี user ได้หลายๆคน และทำงานได้พร้อมๆกัน 

### Overview of Linux
ระบบปฏิบัติการ Linux ประกอบด้วย 3 ส่วนหลักๆ คือ เปลือก (Shell),เนื้อใน (kernel) และโปรแกรม (Program) ทั้งสามส่วนนี้ถูกบรรจุลงในส่วนที่เรียกว่า hardware โดยผู้ใช้งาน (User) เป็นคนที่จะคอยสั่งให้ทำอะไรๆ ก็ตาม ลองนึกถึงเมล็ดพืชว่ามันจะมีส่วนประกอบประมาณนั้น ตามรูปนี้

![ส่วนประกอบของ Linux ได้แก่ Shell, Kernel, Program. ](https://github.com/prasert05/mbbtk/blob/master/Bioinformatics-in-Aquaculture_synopsis/img/linux_structure%402x.png)
