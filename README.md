# แอพออมเงิน (Save Money App)

แอปพลิเคชันสำหรับการจัดการการออมเงินและติดตามรายรับ-รายจ่าย

## คุณสมบัติหลัก

- 🔐 ระบบล็อกอินและสมัครสมาชิกด้วย Firebase Authentication
- 💰 บันทึกรายรับ-รายจ่ายพร้อมหมวดหมู่
- 📊 แดชบอร์ดแสดงสถิติและกราฟ
- 🎯 ตั้งเป้าหมายการออมเงิน
- 📈 รายงานสรุปข้อมูลรายเดือน
- 📤 ส่งออกข้อมูลเป็น CSV และ Excel
- 📱 Responsive Design รองรับทุกอุปกรณ์

## การแก้ไขปัญหาภาษาไทยในการส่งออกข้อมูล

### ปัญหาเดิม
ไฟล์ Excel ที่ส่งออกมาแสดงภาษาไทยเป็นภาษาที่อ่านไม่ได้ (mojibake) เนื่องจาก:
- ไม่มี BOM (Byte Order Mark) สำหรับ UTF-8
- Excel ไม่สามารถระบุ encoding ได้อย่างถูกต้อง

### การแก้ไข
1. **เพิ่ม BOM สำหรับ UTF-8**
   ```javascript
   const BOM = '\uFEFF';
   const csvWithBOM = BOM + csvContent;
   ```

2. **ปรับปรุงการจัดรูปแบบข้อมูล**
   - วันที่: ใช้ `toLocaleDateString('th-TH')`
   - จำนวนเงิน: ใช้ `Intl.NumberFormat('th-TH')`

3. **เพิ่มการส่งออกเป็น Excel (.xlsx)**
   - ใช้ไลบรารี SheetJS
   - รองรับภาษาไทยได้อย่างสมบูรณ์
   - ตั้งค่าความกว้างคอลัมน์อัตโนมัติ

### วิธีการใช้งาน
1. คลิกปุ่ม "ส่งออก" ในหน้า Transactions
2. เลือก "ส่งออกเป็น CSV" หรือ "ส่งออกเป็น Excel"
3. ไฟล์จะถูกดาวน์โหลดพร้อมชื่อไฟล์ที่มีวันที่

## การติดตั้ง

1. Clone repository
2. เปิดไฟล์ `index.html` ในเบราว์เซอร์
3. สมัครสมาชิกและเริ่มใช้งาน

## การรันแอปพลิเคชัน

### วิธีที่ 1: เปิดไฟล์โดยตรง (สำหรับการทดสอบ)
1. เปิดไฟล์ `index.html` ในเบราว์เซอร์
2. แอปจะทำงานในโหมด local file

### วิธีที่ 2: ใช้ Local Server (แนะนำ)
#### ใช้ Python (Windows/Linux/Mac)
```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

#### ใช้ Node.js
```bash
# ติดตั้ง http-server globally
npm install -g http-server

# รันเซิร์ฟเวอร์
http-server -p 8000
```

#### ใช้ PHP
```bash
php -S localhost:8000
```

### การเข้าถึงจากเครื่องอื่นในเครือข่าย

#### ขั้นตอนที่ 1: หา IP Address ของเครื่อง
**Windows:**
```cmd
ipconfig
```
หา IPv4 Address (เช่น 192.168.1.100)

**Linux/Mac:**
```bash
ifconfig
# หรือ
ip addr show
```

#### ขั้นตอนที่ 2: รันเซิร์ฟเวอร์ให้รับการเชื่อมต่อจากภายนอก
**Python:**
```bash
python -m http.server 8000 --bind 0.0.0.0
```

**Node.js:**
```bash
http-server -p 8000 -a 0.0.0.0
```

**PHP:**
```bash
php -S 0.0.0.0:8000
```

#### ขั้นตอนที่ 3: เข้าถึงจากเครื่องอื่น
เปิดเบราว์เซอร์ในเครื่องอื่นและไปที่:
```
http://[IP_ADDRESS]:8000
```
ตัวอย่าง: `http://192.168.1.100:8000`

### การตั้งค่า Firewall (Windows)
1. เปิด Windows Defender Firewall
2. คลิก "Allow an app or feature through Windows Defender Firewall"
3. คลิก "Change settings" และ "Allow another app"
4. เลือก Python/Node.js/PHP หรือเพิ่ม port 8000
5. เลือก "Private" และ "Public" networks

### การตั้งค่า Firewall (Linux)
```bash
# Ubuntu/Debian
sudo ufw allow 8000

# CentOS/RHEL
sudo firewall-cmd --permanent --add-port=8000/tcp
sudo firewall-cmd --reload
```

จากเครื่องเดียวกัน:
http://localhost:8000
http://127.0.0.1:8000

จากเครื่องอื่นในเครือข่าย:
http://10.1.1.200:8000


การอัปเดตในอนาคต:
git add .
git commit -m "Update: description"
git push origin main


### หมายเหตุสำคัญ
- ตรวจสอบให้แน่ใจว่าเครื่องอยู่ในเครือข่ายเดียวกัน
- Port 8000 สามารถเปลี่ยนเป็น port อื่นได้
- สำหรับการใช้งานจริง ควรใช้ HTTPS และการรักษาความปลอดภัยที่เหมาะสม
- แอปนี้ใช้ Firebase ดังนั้นต้องมีการเชื่อมต่ออินเทอร์เน็ต

## เทคโนโลยีที่ใช้

- HTML5, CSS3, JavaScript (ES6+)
- Bootstrap 5
- Firebase (Authentication, Firestore)
- Chart.js
- DataTables
- SheetJS (สำหรับการส่งออก Excel)

## การพัฒนา

- ใช้ Firebase เป็น Backend
- รองรับการทำงานแบบ Offline
- มีระบบ Cache เพื่อประสิทธิภาพ
- รองรับการนำเข้า-ส่งออกข้อมูล

## การสนับสนุน

หากพบปัญหาในการใช้งาน กรุณาแจ้งผ่าน Issues ใน GitHub repository
