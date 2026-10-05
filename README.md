# TPIAS Energy Management System (Web)

หน้าเว็บ EMS ของ TPI All Seasons · ไฟล์เดียว `index.html` ไม่ต้อง build

## เปิดใช้งานด้วย GitHub Pages
1. อัปโหลดไฟล์ทั้งหมดในโฟลเดอร์นี้ขึ้น repo (เช่น `tpias-ems`)
2. Settings → Pages → Source: `Deploy from a branch` → Branch `main` / `(root)` → Save
3. รอ 1–2 นาที จะได้ URL `https://<username>.github.io/tpias-ems/`

## หน้าในระบบ
Plants · Dashboard · Power Flow (2D/3D) · Solar · BESS · Meter · EMS (schedule) · Analytics · Alarm · Calendar · Plant Info · Data Logs · Settings

## แหล่งข้อมูล
ตอนนี้เป็น **ข้อมูลจำลอง (mock)** แก้ใน `index.html` ส่วนต้นของ `<script>`:

```js
const DATA_SOURCE = 'mock';   // เปลี่ยนเป็น 'api' เมื่อมี backend
const API_URL = '/api/live';
```

API ต้องคืน JSON:
```json
{ "ts": "2026-10-05T14:30:00+07:00",
  "solar": 236.5, "bess": 0.0, "load": 434.6, "grid": 198.1,
  "soc": 9.4, "recloserOpen": false }
```
Sign convention: `Load = Grid + Solar + BESS` · BESS + = discharge · Grid + = import

## ความปลอดภัย
- ห้าม commit IP, register map, รหัสผ่าน หรือ key ที่เขียนข้อมูลได้
- ก่อนต่อข้อมูลจริง ต้องเพิ่ม login และใช้ key แบบอ่านอย่างเดียว
- หน้าเว็บนี้ **ไม่สั่งงาน** PLC / BESS / Recloser

## ใช้ภายนอก
- Google Fonts (IBM Plex Sans Thai)
- three.js r128 จาก cdnjs (หน้า Power Flow 3D)
