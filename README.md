# CafeManagement

CafeManagement เป็นโปรแกรมจัดการออเดอร์ร้านคาเฟ่แบบ Desktop Application พัฒนาด้วย Java Swing สำหรับเลือกเมนูอาหาร เครื่องดื่ม และเบเกอรี่ คำนวณยอดรวม/ส่วนลด บันทึกบิลลงฐานข้อมูล MySQL/MariaDB และดูรายงานยอดขายประจำวันได้

## ฟีเจอร์หลัก

- หน้า Welcome ก่อนเข้าสู่หน้ารายการเมนู
- แยกหมวดเมนูเป็น อาหาร, เครื่องดื่ม และเบเกอรี่
- เพิ่มสินค้าเข้ารายการออเดอร์พร้อมกำหนดจำนวน
- ลบสินค้าออกจากออเดอร์ หรือล้างรายการทั้งหมด
- คำนวณราคารวม ส่วนลด และยอดสุทธิอัตโนมัติ
- Checkout เพื่อบันทึกบิลและรายการสินค้าเข้าฐานข้อมูล
- หน้ารายงานผลประจำวันสำหรับดูประวัติบิล
- ค้นหารายงานตามวันที่
- ลบประวัติบิลที่บันทึกไว้
- ใช้ FlatLaf เพื่อปรับหน้าตา Swing ให้ดูทันสมัยขึ้น

## ตัวอย่างเมนูในระบบ

### อาหาร

- กะเพราไก่
- ข้าวกะเพราทะเล
- กุ้งอบวุ้นเส้น
- มักกะโรนี
- สปาเก็ตตี้คาโบนาร่า

### เครื่องดื่ม

- โกโก้
- ชาไทย
- น้ำอัดลม
- น้ำเปล่า
- คาปูชิโน่
- ลาเต้

### เบเกอรี่

- เค้กเรดเวลเวท
- เค้กลูกส้ม
- เค้กบานอฟฟี่
- เค้กช็อกโกแลตหน้านิ่ม
- ชีสเค้กบลูเบอร์รี่

## เทคโนโลยีที่ใช้

- Java 21
- Java Swing
- NetBeans GUI Builder
- Apache Ant / NetBeans Project
- MySQL หรือ MariaDB
- JDBC
- FlatLaf 3.4
- AbsoluteLayout

## โครงสร้างโปรเจกต์

```text
CafeManagement/
|-- SQL/
|   `-- cafe.sql
|-- src/
|   |-- cafemanagement/
|   |   |-- Database.java
|   |   |-- menuPage.java
|   |   `-- welcome.java
|   `-- img/
|-- nbproject/
|-- dist/
|   |-- CafeManagement.jar
|   `-- lib/
|-- build.xml
`-- manifest.mf
```

## ฐานข้อมูล

โปรแกรมเชื่อมต่อฐานข้อมูลผ่านไฟล์ `src/cafemanagement/Database.java` โดยค่าเริ่มต้นคือ:

```text
Database: cafe_management_system
Host: 127.0.0.1
Port: 3306
Username: root
Password: ว่าง
```

ไฟล์ `SQL/cafe.sql` จะสร้างฐานข้อมูลและตารางหลัก 2 ตาราง:

- `bills` สำหรับเก็บวันที่ออกบิลและยอดรวม
- `bill_items` สำหรับเก็บรายการสินค้า จำนวน ราคา และเลขบิลที่เกี่ยวข้อง

## วิธีติดตั้งและรันโปรเจกต์

1. Clone repository

```bash
git clone https://github.com/jxyluvcode/CafeManagement.git
cd CafeManagement
```

2. Import ฐานข้อมูล

นำไฟล์นี้ไป import ใน MySQL/MariaDB:

```text
SQL/cafe.sql
```

3. เปิดโปรเจกต์ด้วย NetBeans

4. เพิ่ม Library ที่จำเป็น หาก NetBeans แจ้งว่าไม่พบไฟล์

- `flatlaf-3.4.jar`
- `AbsoluteLayout.jar`
- `mysql-connector-j-8.3.0.jar`

5. Run Project

Main class ของโปรเจกต์คือ:

```text
cafemanagement.welcome
```

## การรันจากไฟล์ JAR

ใน repository มีไฟล์ JAR อยู่ที่:

```text
dist/CafeManagement.jar
```

สามารถรันด้วยคำสั่ง:

```bash
java -jar dist/CafeManagement.jar
```

ก่อนรันให้เปิด MySQL/MariaDB และ import ฐานข้อมูล `cafe_management_system` ให้เรียบร้อยก่อน

## หมายเหตุ

- หาก username, password, host หรือ port ของฐานข้อมูลไม่ตรงกับเครื่องของคุณ ให้แก้ไขใน `src/cafemanagement/Database.java`
- โปรเจกต์นี้สร้างด้วย NetBeans GUI Builder จึงควรเก็บไฟล์ `.form` ไว้คู่กับไฟล์ `.java`
- ถ้ารันผ่าน NetBeans แล้วเจอปัญหา library หาย ให้ตรวจสอบ path ของ JAR ใน Project Libraries

## ผู้พัฒนา

พัฒนาโดย [jxyluvcode](https://github.com/jxyluvcode)
