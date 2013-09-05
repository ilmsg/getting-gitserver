getting-gitserver
=================

วิธีสร้าง git server สำหรับรัน nodejs 

ข้อมูลเบื้องต้น
==========
เซิร์ฟเวอร์สำหรับ git : git.ilmsg.com
ผู้ใช้คนที่ 1 : user1
ผู้ใช้คนที่ 2 : user2


อันดับแรก สร้าง user สำหรับ ssh เข้า server ก่อน ถ้าใช้ user คนเดียวเราจะสร้าง directory ของ project ไว้ที่ /home/user ก็ได้
ถ้าต้องการใช้งานสำหรับ user หลายคน ( Share ) ก็อาจจะเก็บไว้ที่ /opt/git

วิธีสร้าง git directory จะต้องเป็นชื่อที่มี .git ต่อท้ายด้วย อย่างเช่น 

ตัวอย่างสำหรับ user คนเดียว ใน home ของ user จะเป็น path นี้ /home/user
  
  
    $ mkdir myproject.git
    $ cd myproject.git
    $ git init --bare
    
หลังจากนั้นลอง clone myproject.git จากเครื่อง client ด้วยคำสั่งประมาณนี้

    $ git clone user1@git.ilmsg.com:myproject.git 


ตัวอย่างสำหรับ user หลายคน  เราจะสร้างไว้ที่ /opt/git เพื่อให้หลายๆคนเข้าถึงได้
    
    $ mkdir myproject.git
    $ cd myproject.git
    $ git init --bare --shared

ทดสอบคำสั่ง clone project มาที่ client

    $ git clone user1@git.ilmsg.com:/opt/git/myproject.git
    
ผู้ใช้อีกคนนึงก็จะใช้คำสั่งคล้ายๆแบบนี้

    $ git clone user2@git.ilmsg.com/opt/git/myproject.git
    



License
=======
The MIT License (MIT)

Copyright (c) 2013 Eak Netpanya

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
