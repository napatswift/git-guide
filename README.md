# Git
เป็นซอฟต์แวร์ที่ใช้ใน "ระบบควบคุมรุ่นของซอฟต์แวร์" ในรุ่นแรกสุดของ git [[git README]](https://github.com/git/git/blob/e83c5163316f89bfbde7d9ab23ca2e25604af290/README) ผู้พัฒนาบอกว่า git คือ "the stupid content tracker"
ความหมายของ git เปลี่ยนไปตามอารมณ์ของคุณขณะนั้น
- ตัวอักษร 3 ตัวที่ไม่เกี่ยวข้องกัน รวมกันแล้วอ่านออกเสียงได้ และยังไม่มี command ชื่อนี้ใน UNIX
- ความหมายสแลงคือ ไง่ ไร้ความสามารถ น่ารังเกียจ
- "global information tracker" ถ้ายังอารมณ์ดีเพราะ git ยังใช้ คงเป็นตอนที่ทูตสวรรค์ร้องบรรเลง และคงจะมีแสงส่องลงมา
- "goddamn idiotic truckload of sh*t" เวลาใช้ไม่ได้

"This is a stupid (but extremely fast) directory content manager.  It
doesn't do a whole lot, but what it _does_ do is track directory
contents efficiently."

## 👋🏽 Hello world

เริ่มจากการนำงานของเราเข้าไปใน git ด้วยการใช้คำสั่ง
```bash
git init
```
โดยที่ git จะสร้าง "กรุ" หรือ "repository" ของ git ไว้
และหากสังเกตุจะเห็นว่าจะมี directory ที่ชื่อว่า `.git` อยู่

ถัดมาจะติดตามการเปลี่ยนแปลงไฟล์ใน repository ของเรา 
เพื่อบันทึกสถานะของไฟล์ปัจจุบันให้ใช้ `git add`
เพื่อเพิ่มไฟล์ที่ต้องการติดตาม

```bash
git add file [...file]
```

หากว่าต้องการติดตามไฟล์ทั้งหมดใน directory ปัจจุบันก็ให้ใช้

```bash
git add .
```

โดย `.` จะหมายถัง directory ปัจจุบัน (directory ก็นับว่าเป็นไฟล์)
และเราต้องการให้ git ติดตามไฟล์ทั้งหมดที่อยู่ใน directory นั้น

หลังจากนั้นก็บันทึกถาวรให้กับ snapshot นั้นด้วย

```bash
git commit
```

เมื่อมีการแก้ไขไฟล์แล้วต้องการตรวจดูว่าไฟล์ใน directory มีการสถานะเป็นอย่างไรบ้าง
ขณะนี้อยู่บน branch ไหน สามารถใช้

```bash
git status
```

หากว่าต้องการ commit โดยไม่ต้องใช้คำสั่ง `git add` ก่อนก็ให้ใช้

```bash
git commit -a
```

โดยโปรแกรมจะค้นหาไฟล์ที่มีการแก้ไขโดยอัตโนมัติ (เฉพาะไฟล์ที่เคยติดตามการเปลี่ยนแปลง)

# 👯‍♂️โคลน

เราสามารถโคลน repository ที่เหมือนกันเดะ โดยใช้คำสั่ง

```
git clone <repository> [<directory>]
```

เพื่อทำการโคลน respository จาก `<repository>` มาไว้ที่ `<directory>` โดยที่สามารถละไม่ใส่ได้
จะมี default เป็นชื่อของ repository ที่ต้องการโคลน

ตัวอย่างการโคลนจากบนเว็บ

```bash
$ git clone git://git.kernel.org/pub/scm/.../linux.git my-linux
$ cd my-linux
$ make
```

จะโคลน `git://git.kernel.org/pub/scm/.../linux.git` มาที่ `my-linux`


## ☘️ ก้าน

ในหนึ่ง git repository สามารถมีได้หลายกิ่งสาขา หรือ "branches" 
สำหรับการสร้างกิ่งใหม่ด้วยชื่อว่า "experimental" สามารถใช้คำสั่ง

```bash
git branch experimental
```

หลังจากนั้นหากว่าใช้คำสั่ง
```bash
git branch
```

โปรแกรมจะแสดงชื่อของ branches ทั้งหมดที่มีมาให้เห็น

### คำสั่ง

`git branch (-m | -M) [<oldbranch>] <newbranch>` ย้าย (move) หรือพูดอีกอย่างคือการเปลี่ยนชื่อ จาก oldbranch ไป newbranch หากว่า newbranch ซ้ำกับที่มีอยู่แล้วและต้องการบังคับให้ทำต่อให้ใช้ `-M` แทน `-m`

`git branch (-c | -C) [<oldbranch>] <newbranch>` ลอก (copy) จาก oldbranch ไปเป็น newbranch

`git branch (-d | -D) [-r] <branchname>…​` ลบ (delete) branchname โดยสามารถใส่ได้หลาย branchname
หากว่าต้องการลบ branch นี้บน remote ก็ให้ใส่ `-r`


