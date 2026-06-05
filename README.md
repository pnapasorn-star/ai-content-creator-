# AI Creator for Students

เว็บแอปสร้างคอนเทนต์ด้วย Claude AI สำหรับนักศึกษา

## โครงสร้างไฟล์

```
ai-content-creator/
├── api/
│   └── chat.js        ← Vercel Edge Function (proxy to Anthropic API)
├── public/
│   └── index.html     ← หน้าเว็บหลัก
├── vercel.json        ← Vercel config
└── package.json
```

## วิธี Deploy บน Vercel

### 1. สมัคร / Login Vercel
ไปที่ https://vercel.com และ login ด้วย GitHub

### 2. อัปโหลดโปรเจกต์

**วิธี A — ผ่าน GitHub (แนะนำ)**
1. สร้าง repo ใหม่บน GitHub แล้ว push ไฟล์ทั้งหมดขึ้นไป
2. ใน Vercel กด **Add New Project** → เลือก repo
3. กด **Deploy** ได้เลย (ไม่ต้องตั้งค่า build command)

**วิธี B — ผ่าน Vercel CLI**
```bash
npm install -g vercel
cd ai-content-creator
vercel
```

### 3. ตั้งค่า API Key (สำคัญมาก!)

ใน Vercel Dashboard:
1. เข้าไปที่โปรเจกต์ → **Settings** → **Environment Variables**
2. กด **Add New**
3. ใส่ค่า:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-xxxxxxxxxx` (API key ของคุณ)
   - **Environment:** เลือก Production, Preview, Development
4. กด **Save**
5. ไปที่ **Deployments** → กด **Redeploy**

### 4. รับ API Key จาก Anthropic
ไปที่ https://console.anthropic.com → API Keys → Create Key

---

## หมายเหตุ
- API key จะถูกเก็บใน environment variable ของ Vercel อย่างปลอดภัย
- ไม่มีใครเห็น key จากหน้าเว็บ เพราะ Edge Function รันฝั่ง server
- Vercel ให้ใช้ฟรี 100,000 requests/เดือน (Hobby plan)
