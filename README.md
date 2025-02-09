# Nagios
ท่ามกลางคุณสมบัติมากมายของ Nagios Core สามารถกล่าวถึง 10 ต่อไปนี้:

1. ตรวจสอบบริการเครือข่าย (SMTP, POP3, HTTP, NNTP, PING เป็นต้น)
2. การมอนิเตอร์รีซอร์สของโฮสต์ที่ถูกมอนิเตอร์ที่แตกต่างกัน (โหลดโปรเซสเซอร์ การใช้ดิสก์ และอื่นๆ)
3. การออกแบบปลั๊กอินอย่างง่ายที่ช่วยให้ผู้ใช้สามารถพัฒนาการตรวจสอบบริการของตนเองได้อย่างง่ายดาย
4. การตรวจสอบบริการแบบขนาน
5. ความสามารถในการกำหนดลำดับชั้นของโฮสต์เครือข่ายโดยใช้โฮสต์ "พาเรนต์" ช่วยให้คุณตรวจจับและแยกแยะระหว่างโฮสต์ที่ไม่ทำงานกับโฮสต์ที่ไม่สามารถเข้าถึงได้
6. ติดต่อการแจ้งเตือนเมื่อเกิดปัญหาเกี่ยวกับโฮสต์หรือบริการและได้รับการแก้ไข (โดยอีเมล เพจเจอร์ หรือวิธีที่ผู้ใช้กำหนด)
7. ความสามารถในการกำหนดตัวจัดการเหตุการณ์ให้ทำงานระหว่างโฮสต์หรือเหตุการณ์บริการสำหรับการแก้ไขปัญหาเชิงรุก
8. การหมุนไฟล์บันทึกโดยอัตโนมัติ
9. รองรับการนำโฮสต์การตรวจสอบที่ซ้ำซ้อนไปใช้
10. เว็บอินเตอร์เฟสเสริมเพื่อดูสถานะปัจจุบันของเครือข่าย ประวัติการแจ้งเตือนและปัญหา ไฟล์บันทึก และอื่นๆ

เราสามารถติดตั้ง Nagios ได้หลายระบบปฎิบัติการ ทางกลุ่มเลือก ubuntu วิธีการติดตั้งมีขั้นตอนดังนี้
1. ขั้นตอนในการเตรียมระบบปฏิบัติการ อัพเดต Repositories และติดตั้งแพ็คเกจที่จำเป็นและจำเป็นเพื่อใช้งาน Nagios Core.
โดยพิมพ์คำสั่ง sudo apt update  
พิมพ์คำสั่ง sudo apt install autoconf gcc libc6 make wget unzip apache2 apache2-utils php libgd-dev
![1](https://user-images.githubusercontent.com/119097663/210220857-ef1be291-7e7e-419e-a1e7-526d567d8ea2.jpg)
![imgpsh_mobile_save](https://user-images.githubusercontent.com/119097663/210221017-95b6c702-ddd0-417a-b5d9-e204d0221c97.jpg)

2. ดาวน์โหลดซอฟต์แวร์ปัจจุบัน
โดยพิมพ์คำสั่ง cd /tmp

![fcc117c0-d4e9-4f1b-bdb9-15968e39f2a9](https://user-images.githubusercontent.com/119097663/210221295-aa9de632-3097-4d60-a6d5-c516068d12b1.jpg)

พิมพ์คำสั่ง wget -O nagioscore.tar.gz

![091ef26d-f0c5-4197-a597-763a82883125](https://user-images.githubusercontent.com/119097663/210221472-e97ee7c2-74a6-42f8-bac8-45c634d7ceb6.jpg)

พิมพ์คำสั่ง tar xzf nagioscore.tar.gz

![image](https://user-images.githubusercontent.com/119097663/210221636-6e1e4d42-5365-46cb-957a-28f0cf501c7b.png)

3. รวบรวมซอฟต์แวร์ปัจจุบัน

พิมพ์คำสั่ง cd /tmp/nagioscore-nagios-4.4.6/


พิมพ์คำสั่ง sudo ./configure --with-httpd-conf=/etc/apache2/sites-enabled

![fcc117c0-d4e9-4f1b-bdb9-15968e39f2a9](https://user-images.githubusercontent.com/119097663/210221735-5208a6fb-5479-42ed-a7ce-a97ce38f116b.jpg)

พิมพ์คำสั่ง sudo make all

![265284c8-f718-4161-9524-5ab4df068867](https://user-images.githubusercontent.com/119097663/210221893-5267cec2-5712-49e1-b401-f5f6de1a4f36.jpg)

4. สร้างผู้ใช้และกลุ่ม

พิมพ์คำสั่ง sudo make install-groups-users และ sudo usermod -a -G nagios www-data
![68bbe1c5-a53e-4feb-9f03-351e64069f59](https://user-images.githubusercontent.com/119097663/210222021-db50df4a-8c2e-4b8b-b511-d552e80ee109.jpg)

5. ติดตั้งแพ็คเกจที่จำเป็นต่างๆ

พิมพ์คำสั่ง sudo make install

![9d3a9747-7823-48a5-a2c7-d4e768040e18](https://user-images.githubusercontent.com/119097663/210222147-afee7c2c-1d56-4cc5-8735-a81d37e71c89.jpg)


พิมพ์คำสั่ง sudo make install-daemoninit 

พิมพ์คำสั่ง sudo make install-commandmode 

พิมพ์คำสั่ง sudo make install-config

![f2000ebb-e9aa-48d9-b7df-4eea2aa5ba86](https://user-images.githubusercontent.com/119097663/210222213-504c2455-8da8-4d18-ad2a-48220df104c0.jpg)

6. ติดตั้งและกำหนดค่าไฟร์วอลล์ผ่าน IPTables

พิมพ์คำสั่ง sudo apt install iptables

พิมพ์คำสั่ง sudo iptables -I INPUT -p tcp --destination-port 80 -j ACCEPT

พิมพ์คำสั่ง sudo apt install -y iptables-persistent
![38daeabe-ec4b-4625-ba05-188ce02252b8](https://user-images.githubusercontent.com/119097663/210222466-3a45a764-524a-43cd-91e5-19258f813066.jpg)

7. สร้างบัญชีผู้ใช้ใน Apache เพื่อเริ่มต้นใน Nagios Core

พิมพ์คำสั่ง sudo htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin

8.  รีสตาร์ท / เริ่มบริการที่จำเป็น

พิมพ์คำสั่ง systemctl restart apache2.service

พิมพ์คำสั่ง systemctl start nagios.service
![4f2623bb-1c66-4ec4-9024-baeada159610](https://user-images.githubusercontent.com/119097663/210223008-4757a317-96a5-43a4-9812-6f37dda0d1cd.jpg)

9. เข้าสู่ระบบ Nagios Core 
ด้วย IP 172.31.0.214
ล็อคอินด้วย Username เเละ Password
![eb1bf9da-7dcd-41d3-9307-8fa9172bb998](https://user-images.githubusercontent.com/119097663/210223237-3db6680f-3441-42af-828b-7407bec69bf6.jpg)

เป็นอันเสร็จขั้นตอนการติดตั้ง ขั้นตอนต่อไปจะเป็นการติดตั้งปลั๊กอินหลักของ Nagios
การติดตั้งปลั๊กอินของ Nagios มีขั้นตอนการติดตั้งดังนี้

1. อัพเดต Repositories และติดตั้งแพ็คเกจที่จำเป็นและจำเป็นเพื่อใช้งาน ปลั๊กอิน Nagios.

พิมพ์คำสั่ง sudo apt update

พิมพ์คำสั่ง sudo apt install autoconf gcc libc6 libmcrypt-dev make libssl-dev wget bc gawk dc build-essential snmp libnet-snmp-perl gettext
![6db2ec87-0646-4ffe-b703-6365e82d644a](https://user-images.githubusercontent.com/119097663/210223568-8b12aa0b-ccc9-4075-ae74-ea2745ac9492.jpg)

2. ดาวน์โหลดและเปิดเครื่องรูดแพ็คเกจปัจจุบันด้วย "ปลั๊กอิน Nagios"

พิมพ์คำสั่ง cd /tmp

พิมพ์คำสั่ง wget --no-check-certificate -O nagios-plugins.tar.gz
![31541dce-9617-491f-9664-91719c3f5554](https://user-images.githubusercontent.com/119097663/210223717-c6c1689e-bc28-47b6-97b2-a2d98d9db4be.jpg)

พิมพ์คำสั่ง tar zxf nagios-plugins.tar.gz
![1a5deaa3-6417-4108-b381-8ff0bade8719](https://user-images.githubusercontent.com/119097663/210223849-1486481c-0846-4eb5-8187-fd4303ef3a30.jpg)

3. รวบรวมและติดตั้ง "ปลั๊กอิน Nagios"

พิมพ์คำสั่ง cd /tmp/nagios-plugins-release-2.2.1/


พิมพ์คำสั่ง ./tools/setup

![1a5deaa3-6417-4108-b381-8ff0bade8719](https://user-images.githubusercontent.com/119097663/210223849-1486481c-0846-4eb5-8187-fd4303ef3a30.jpg)

พิมพ์คำสั่ง sudo ./configure

![cb3b6676-8f1c-490e-bbed-030e727a3206](https://user-images.githubusercontent.com/119097663/210224025-93bd57d8-c97d-46f9-8b6e-7ae91faf2b22.jpg)

พิมพ์คำสั่ง sudo make

พิมพ์คำสั่ง sudo make instal

![38ee74da-768f-4b77-9ce4-3e091e75d471](https://user-images.githubusercontent.com/119097663/210224058-f7dc376f-aea5-4457-ad78-e3ad9c8caf36.jpg)

เสร็จสิ้นขั้นตอนการติดตั้งปลั๊กอินของ Nagios
