# 💰 แอพออมเงิน (Save Money App)

แอปพลิเคชันจัดการการเงินส่วนบุคคลที่ช่วยให้คุณติดตามรายรับ-รายจ่าย ตั้งเป้าหมายการออม และดูสถิติการเงินของคุณ

## 🌟 คุณสมบัติหลัก

- **📊 แดชบอร์ดแบบ Real-time** - ดูสรุปการเงินของคุณทันที
- **📝 จัดการรายการ** - เพิ่ม แก้ไข ลบรายการรายรับ-รายจ่าย
- **📈 กราฟและสถิติ** - ดูแนวโน้มการเงินรายเดือน
- **🎯 เป้าหมายการออม** - ตั้งและติดตามเป้าหมายการออม
- **📱 Responsive Design** - ใช้งานได้ทั้งบนมือถือและคอมพิวเตอร์
- **🔐 ระบบความปลอดภัย** - เข้าสู่ระบบด้วย Firebase Authentication
- **📤 ส่งออกข้อมูล** - ส่งออกเป็น CSV หรือ Excel

## 🚀 การใช้งาน

### เว็บไซต์ที่ Deploy แล้ว
**https://spyit2025.github.io/save-money-app/**

### การใช้งานในเครื่อง (Local Development)
1. Clone repository
2. เปิดไฟล์ `index.html` ใน browser
3. สมัครสมาชิกและเริ่มใช้งาน

## 🛠️ เทคโนโลยีที่ใช้

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Backend**: Firebase (Authentication, Firestore)
- **UI Framework**: Bootstrap 5
- **Charts**: Chart.js
- **Tables**: DataTables
- **Icons**: Font Awesome
- **Deployment**: GitHub Pages

## 📁 โครงสร้างไฟล์

```
Save money app/
├── index.html              # หน้า Login/Register
├── dashboard.html          # หน้า Dashboard หลัก
├── 404.html               # หน้า Error 404
├── css/
│   └── style.css          # CSS หลัก
├── js/
│   ├── app.js             # ฟังก์ชันหลักของแอพ
│   ├── auth.js            # ระบบ Authentication
│   ├── dashboard.js       # ฟังก์ชัน Dashboard
│   ├── firebase-config.js # การตั้งค่า Firebase
│   └── date-helper.js     # ฟังก์ชันจัดการวันที่
├── README.md              # คู่มือนี้
├── CHANGELOG.md           # ประวัติการเปลี่ยนแปลง
├── TROUBLESHOOTING.md     # แก้ไขปัญหา
├── FIREBASE-GITHUB-SETUP.md # การตั้งค่า Firebase
├── deploy-github.bat      # Script deploy สำหรับ Windows
├── deploy-github.sh       # Script deploy สำหรับ Linux/Mac
├── setup-github.bat       # Script setup สำหรับ Windows
├── setup-github.sh        # Script setup สำหรับ Linux/Mac
└── quick-setup.bat        # Script setup เร็ว
```

## 🔧 การตั้งค่า Firebase

### 1. สร้างโปรเจค Firebase
1. ไปที่ [Firebase Console](https://console.firebase.google.com/)
2. สร้างโปรเจคใหม่
3. เปิดใช้งาน Authentication และ Firestore

### 2. ตั้งค่า Domain
1. ไปที่ **Authentication** > **Settings** > **Authorized domains**
2. เพิ่ม domain: `spyit2025.github.io` และ `*.github.io`

### 3. ตั้งค่า Firestore Security Rules
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
    match /users/{userId}/transactions/{transactionId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
    match /users/{userId}/goals/{goalId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
    match /users/{userId}/categories/{categoryId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## 🚀 การ Deploy

### วิธีที่ 1: ใช้ Script (แนะนำ)
```bash
# Windows
deploy-github.bat

# Linux/Mac
./deploy-github.sh
```

### วิธีที่ 2: ใช้ Git โดยตรง
```bash
git add .
git commit -m "Update: description"
git push origin main
```

## 📱 การใช้งาน

### 1. สมัครสมาชิก
- ไปที่หน้า Login
- คลิก "สมัครสมาชิก"
- กรอกข้อมูลและสร้างบัญชี

### 2. เพิ่มรายการ
- คลิกปุ่ม "เพิ่มรายการ"
- เลือกประเภท (รายรับ/รายจ่าย)
- กรอกจำนวนเงิน หมวดหมู่ และรายละเอียด
- คลิก "บันทึก"

### 3. ดูสถิติ
- ดูสรุปใน Dashboard
- ดูกราฟรายเดือน
- ดูรายการล่าสุด

### 4. ตั้งเป้าหมาย
- ไปที่หน้า "เป้าหมาย"
- คลิก "เพิ่มเป้าหมาย"
- ตั้งจำนวนเงินและวันที่เป้าหมาย

## 🔍 การแก้ไขปัญหา

หากพบปัญหา ให้ดูในไฟล์ `TROUBLESHOOTING.md` หรือตรวจสอบ:

1. **การเชื่อมต่อ Firebase** - ตรวจสอบ console logs
2. **การตั้งค่า Domain** - ตรวจสอบ Firebase Console
3. **Cache Browser** - ล้าง cache และลองใหม่

## 📞 การติดต่อ

หากมีปัญหาหรือข้อเสนอแนะ:
- ตรวจสอบ `TROUBLESHOOTING.md`
- ดู `CHANGELOG.md` สำหรับการอัปเดตล่าสุด
- ตรวจสอบ console logs ใน browser

## 📄 License

โปรเจคนี้เป็น Open Source และสามารถใช้งานได้ฟรี

---

**🎉 ขอบคุณที่ใช้แอพออมเงิน!**
