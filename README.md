# api-truewallet-gift-class
API TrueWallet Gift Class  By Hyper Studio

## สารบัญการใช้งาน
[เริ่มต้นใช้งาน](#เริ่มต้นใช้งาน) | 
[เกี่ยวกับเว็บไซต์](#เกี่ยวกับเว็บไซต์) | 
[การใช้งาน API](#การใช้งานAPI) | 
[วิธีการเติมเงิน](#วิธีการเติมเงิน) | 
[เพิ่มเติม](#เพิ่มเติม)

## เริ่มต้นใช้งาน
1. ไปที่เว็บไซต์ [hyperstudio.online](http://hyperstudio.online/)
2. ``` สมัครสมาชิก ``` และ ``` เข้าสู่ระบบ ```
* หมายเหตุ : หลังจากสมัครสมาชิกเสร็จระบบจะให้ ``` Request เริ่มต้น 50 Requests ``` โดยถ้าใช้ ``` Request จนเหลือ 0 ``` จะไม่สามารถส่งข้อมูลมา Server ได้ 

## เกี่ยวกับเว็บไซต์
- **API Key** คือกุญแจที่ใช้ในการเชื่อมต่อ **API** ระหว่าง **Server** ผู้ใช้ กับ **Server** ของระบบ โดยที่เราสามารถรับ **API Key** ได้หลังจาก **เข้าสู่ระบบ** และ คลิ้กที่ปุ่ม ***"คัดลอก KEY"***
 **API Key** จะไม่มีทางซ้ำกับของผู้ใช้งานอื่น
 ![Result](https://www.img.in.th/images/92d6efcf79eedef3f4196b787fe47e2f.png)
- **การอัพเดท ข้อมูล ของ Server** โดยที่ Server จะอัพเดทข้อมูลอัตโนมัติทุกๆ 1 นาที โดยที่ระบบจะอัพเดทข้อมูลคือ ***Log API*** , ***Request คงเหลือ*** , ***การใช้ Request ต่อวัน*** , ***รายได้ต่อวัน***

## การใช้งานAPI
1. ดาวน์โหลดไฟล์ [hyperclass.php](https://github.com/sharpaddroot/api-truewallet-gift-class/blob/master/hyperclass.php) จาก ***Github*** เพื่อเรียกใช้งาน ***Class***
2. ให้ไปที่ไฟล์ ``` hyperclass.php ``` และนำ ***API Key*** มาใส่
```php
  public $apikey = 'นำ API Key มาใส่ที่นี่'; 
```
3. สร้าง ``` Form ``` สำหรับไว้ส่งค่า ``` Link ``` ``` (การส่งค่าให้ใช้ Method="POST") ```
- รูปตัวอย่าง ***Form***
  - ![Result](https://www.img.in.th/images/c5b7983e1e61c6991587835d0c4ad3b2.png)
4. หลังจากสร้าง ``` Form ``` ให้นำ ``` Code ``` ด้านล่าง ไปใส่ในไฟล์ใช้ที่รับค่า
```php
<?php

  include('hyperclass.php');
  $useapi = new Hyper();
  $value = $_POST['link']; //ค่าลิ้งซองของขวัญ
  $mygiftlink = str_replace(' ','',$value);
  $result = $useapi->hyperRequest($mygiftlink);
  
  if($result['code'] == '200'){ //ทำรายการสำเร็จ	
  
	  $link =  $result['link']; //ลิ้งที่ใช้ในการเติมเงิน
	  $money =  $result['amount']; //จำนวนเงินที่เติม
	  $date =  $result['date']; //เวลาที่เติมเงิน		
    
  }else{ //ทำรายการไม่สำเร็จ		
  
	  $errormsg = $result['msg']; //แสดงข้อความ Error	
    
  }
  
 ?>
```

## วิธีการเติมเงิน
1. เข้าไปที่แอป ``` Truewallet ```
2. ไปที่ ``` บัตรเติมเงิน & ของขวัญ ``` -> ``` ส่งซองของขวัญ ``` [ดูรูปตัวอย่าง](https://www.img.in.th/images/78bc8881c2d195fdc3aa259ff1f7d278.jpg)
3. หลังจากเข้าที่ ``` ส่งซองของขวัญ ``` แล้วให้กรอก ``` จำนวนเงิน ``` และ ``` จำนวนผู้รับซอง ``` _แนะนำให้กรอกจำนวนแค่ 1 ไม่งั้นจะได้เงินไม่เต็มจำนวน_ [ดูรูปตัวอย่าง](https://www.img.in.th/images/7c4782d43a430c3f0de7388a5dba722a.jpg)
4. หลังจากกรอกข้อมูลแล้วให้กด ``` สร้างซองของขวัญ ``` และจะขึ้นหน้ายืนยันข้อมูลให้กด ``` ยืนยัน ``` [ดูรูปตัวอย่าง](https://www.img.in.th/images/1a264cbb4b8d7c0827466c33559dae32.jpg)
5. หลังจากกดยืนยันแล้วจะมี ``` Link ``` มาให้กด ``` คัดลอก ``` และนำไปเติมตามเว็บได้เลย [ดูรูปตัวอย่าง](https://www.img.in.th/images/89312ce1d42342befb9b7c1877c175ac.jpg)

## เพิ่มเติม
- ถ้ามีปัญหาในการใช้งานสามารถติดต่อได้ที่ [Hyper Studio](https://www.facebook.com/pagehyperstudio) ``` "หมายเหตู : ทำมาแจกฟรีห้ามนำไปจำหน่ายนะจ๊ะ" ```
- สามารถบริจาคค่ากาแฟที่เว็บไซต์ที่ให้บริการ API [hyperstudio.online](https://hyperstudio.online/)
