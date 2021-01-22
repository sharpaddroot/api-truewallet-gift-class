<style>
 h3{border-bottom: 1px solid rgba(13,17,23,0.1) !important; padding-bottom:10px !important;}
 a{font-weight: bold !important; font-style: italic !important; text-decoration: underline !important;}
 .t-red{color:#E8175D !important;}
 .t-green{color:#2F9599 !important;}
 .t-org{color:#F26B38  !important;}
 .t-blue{color:#3598DB  !important;}
 small{color:rgba(71,71,71,0.7) !important;}
</style>

# API TrueWallet Gift Class

<h3 class="t-black"><b>สารบัญ การใช้งาน</b></h3>
<ul>
    <li><a href="#start" class="t-red">เริ่มต้นใช้งาน</a></li>
    <li><a href="#web" class="t-green">เกี่ยวกับเว็บไซต์</a></li>
    <li><a href="#api" class="t-blue">การใช้งาน API</a></li>
    <li><a href="#pay" class="t-org">วิธีการเติมเงิน</a></li>
</ul>

<h3 class="t-red" id="start" style="padding-top:30px !important;"><b>เริ่มต้นใช้งาน</b></h3>
<ol>
    <li>ไปที่เว็บไซต์ <a href="https://hyperstu.tk" class="t-org">hyperstu.tk</a></li>
    <li><font class="t-blue">สมัครสมาชิก</font> และ <font class="t-green">เข้าสู่ระบบ</font></li>
    <small><b>
        หมายเหตุ : หลังจากสมัครสมาชิกเสร็จระบบจะให้ Request เริ่มต้น 50 Requests</br>
        <font style="padding-left:8%">โดยถ้าใช้ Request จนเหลือ 0 จะไม่สามารถส่งข้อมูลมา Server ได้</font></br>
        <font style="padding-left:8%">สามารขอ Request เพิ่มได้ที่ Facebook : <a href="https://www.facebook.com/pagehyperstudio" class="t-blue">Hyper Studio</a> โดยแจ้ง <font class="t-red">Username</font> กับ แอดมินเพจ</font>
     </b></small>
</ol>

<h3 class="t-green" id="web" style="padding-top:30px !important;"><b>เกี่ยวกับเว็บไซต์</b></h3>
<ol>
    <font class="t-red"><b>API Key</b></font> 
        <font>คือกุญแจที่ใช้ในการเชื่อมต่อ <b>API</b> ระหว่าง <b>Server</b> ผู้ใช้ กับ <b>Server</b> ของระบบ<font></br>
        <font style="padding-left:7%">โดยที่เราสามารถรับ <font class="t-red"><b>API Key</b></font>  ได้หลังจาก <font class="t-green">เข้าสู่ระบบ</font> และ คลิ้กที่ปุ่ม <b>"คัดลอก KEY"</b><font></br>
        <font style="padding-left:7%"><font class="t-red"><b>API Key</b></font> จะไม่มีทางซ้ำกับของผู้ใช้งานอื่น<font></br>
        <img style="padding-left:7%;margin-top:10px;" src="https://www.img.in.th/images/92d6efcf79eedef3f4196b787fe47e2f.png" width="60%"/></p>
    <font class="t-blue"><b>การอัพเดท ข้อมูล ของ Server</b></font> โดยที่ Server จะอัพเดทข้อมูลอัตโนมัติทุกๆ 1 นาที โดยที่ระบบจะอัพเดทข้อมูลคือ <font class="t-green"><b>Log API</b></font> , <font class="t-red"><b>Request คงเหลือ</b></font> , <font class="t-org"><b>การใช้ Request ต่อวัน</b></font> , <font class="t-blue"><b>รายได้ต่อวัน</b></font>
</ol>

<h3 class="t-blue" id="api" style="padding-top:30px !important;"><b>การใช้งาน API</b></h3>
<ol>
    <li>ดาวน์โหลดไฟล์ <a href="https://github.com/sharpaddroot/api-truewallet-gift-class/blob/master/hyperclass.php" class="t-org">hyperclass.php</a> จาก <font class="t-red"><b>Github</b></font> เพื่อเรียกใช้งาน <font class="t-green"><b>Class</b></font></li>
    <li>ให้ไปที่ไฟล์ <font class="t-org"><b>hyperclass.php</b></font> และนำ <font class="t-red"><b>API Key</b></font> มาใส่
    <code>
        $apikey = 'นำ API Key มาใส่ที่นี่'; 
    </code>
    </li>
    <li>สร้าง <font class="t-blue"><b>Form</b></font> สำหรับไว้ส่งค่า <font class="t-green"><b>Link</b></font> <small>(การส่งค่าให้ใช้ Method="POST")</small></br>
    รูปตัวอย่าง <font class="t-blue"><b>Form</b></font></br>
    <img style="margin-top:10px;" src="https://www.img.in.th/images/052e270cd6fa1e954113d8811ed781c4.png" width="30%"/>
    </li>
    <li>หลังจากสร้าง <font class="t-blue"><b>Form</b></font> ให้นำ <font class="t-red"><b>Code</b></font> ด้านล่าง ไปใส่ในไฟล์ใช้ที่รับค่า</br>
    <pre>
    include('hyperclass.php');
    $useapi = new Hyper();
    $value = $_POST['link']; //ค่าลิ้งซองของขวัญ
    $mygiftlink = str_replace(' ','',$value);
    $result = $useapi->hyperRequest($mygiftlink);
    if($result['code'] == '200'){
        print_r($result);  //ทำรายการสำเร็จ
    }else{
        print_r($result);  //ทำรายการไม่สำเร็จ
    }
    </pre>
    </li>
</ol>


