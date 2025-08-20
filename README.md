# แอพออมเงิน (Save Money App)

แอปพลิเคชันสำหรับการจัดการการเงินส่วนบุคคล พัฒนาด้วย HTML, CSS, JavaScript และ Firebase

## ✨ ฟีเจอร์หลัก

- 📊 **แดชบอร์ด** - แสดงสถิติการเงินแบบเรียลไทม์
- 💰 **จัดการรายการ** - เพิ่ม/แก้ไข/ลบรายรับ-รายจ่าย
- 📈 **รายงาน** - กราฟและสถิติรายเดือน
- 🎯 **เป้าหมายการออม** - ตั้งเป้าหมายและติดตามความคืบหน้า
- 👤 **ระบบสมาชิก** - ลงทะเบียนและเข้าสู่ระบบ
- 📱 **Responsive Design** - ใช้งานได้ทุกอุปกรณ์

## 🚀 การ Deploy

### GitHub Pages (แนะนำ)
```bash
# ใช้ script ที่มีอยู่แล้ว
./deploy-github.bat
# หรือ
./deploy-github.sh
```

### Netlify
```bash
# ใช้ script ที่มีอยู่แล้ว
./quick-setup.bat
```

### Vercel
- อัปโหลดไฟล์ไปยัง Vercel
- ใช้ไฟล์ `vercel.json` ที่มีอยู่แล้ว

## 🐛 การแก้ไขล่าสุด

### ปัญหา: `data.date.toDate is not a function`
**สาเหตุ:** ข้อมูล date จาก Firestore อาจไม่ใช่ Firestore Timestamp object เสมอไป

**การแก้ไข:** อัปเดตโค้ดใน `js/dashboard.js` เพื่อตรวจสอบประเภทข้อมูลก่อนเรียกใช้ `.toDate()`

```javascript
// ก่อน
date: data.date.toDate()

// หลัง
date: data.date && typeof data.date.toDate === 'function' ? data.date.toDate() : 
      data.date ? new Date(data.date) : new Date()
```

## 🔧 การติดตั้ง

1. Clone repository
2. เปิดไฟล์ `js/firebase-config.js`
3. แก้ไข Firebase configuration
4. เปิดไฟล์ `index.html` ในเบราว์เซอร์

## 📁 โครงสร้างไฟล์

```
save-money-app/
├── index.html          # หน้าล็อกอิน
├── dashboard.html      # หน้าแดชบอร์ดหลัก
├── css/
│   └── style.css      # สไตล์หลัก
├── js/
│   ├── app.js         # ไฟล์หลัก
│   ├── auth.js        # ระบบ Authentication
│   ├── dashboard.js   # ฟังก์ชันแดชบอร์ด
│   └── firebase-config.js # การตั้งค่า Firebase
├── deploy-github.bat  # Script deploy GitHub Pages
├── netlify.toml       # การตั้งค่า Netlify
└── vercel.json        # การตั้งค่า Vercel
```

## 🔐 การตั้งค่า Firebase

1. สร้างโปรเจกต์ Firebase ใหม่
2. เปิดใช้งาน Authentication (Email/Password)
3. สร้าง Firestore Database
4. แก้ไขไฟล์ `js/firebase-config.js` ด้วยข้อมูลของคุณ

## 📱 การใช้งาน

1. **สมัครสมาชิก** - สร้างบัญชีใหม่
2. **เข้าสู่ระบบ** - ใช้อีเมลและรหัสผ่าน
3. **เพิ่มรายการ** - บันทึกรายรับ-รายจ่าย
4. **ตั้งเป้าหมาย** - กำหนดเป้าหมายการออม
5. **ดูรายงาน** - ตรวจสอบสถิติการเงิน

## 🌐 ลิงก์ที่เกี่ยวข้อง

- [เว็บไซต์หลัก](https://spyit2025.github.io/save-money-app/)
- [หน้าแดชบอร์ด](https://spyit2025.github.io/save-money-app/dashboard.html)

## 📄 License

MIT License - ดูรายละเอียดในไฟล์ LICENSE

## 🤝 การสนับสนุน

หากพบปัญหาหรือต้องการฟีเจอร์ใหม่ กรุณาสร้าง Issue ใน GitHub repository
