# Boshqaruv Tizimi (DC Management Frontend)

**Boshqaruv Tizimi** — korxona, tashkilot va loyihalarni boshqarish, xodimlar faoliyatini nazorat qilish, topshiriqlar (Kanban), moliya, hisobotlar, arizalar hamda real-vaqt rejimida onlayn videokonferensiyalarni amalga oshirishga mo'ljallangan zamonaviy va keng qamrovli boshqaruv platformasi (CRM / ERP).

---

## 🛠 Ishlatilgan Texnologiyalar (Tech Stack)

### Asosiy Texnologiyalar:
- **React 19** (`react`, `react-dom` v19.1.1) — zamonaviy komponentli arxitektura.
- **Vite 7** (`vite` v7.1.7) — yuqori tezlikdagi yig'uvchi (build tool) va ishlab chiqish muhiti (dev server).
- **React Router v7** (`react-router-dom` v7.14.1) — marshrutlash va yo'llarni himoyalash (protected routes).

### UI & Styling:
- **Tailwind CSS v4** (`tailwindcss`, `@tailwindcss/vite` v4.2.4) — zamonaviy utility-first dizayn tizimi.
- **Ant Design 6** (`antd` v6.3.7) — jadval, modal, select, drawer va boshqa tayyor UI komponentlar.
- **Hugeicons & React Icons** (`@hugeicons/react`, `@hugeicons/core-free-icons`, `react-icons`) — professional piktogrammalar to'plami.
- **Light / Dark Mode** — to'liq moslashtirilgan qorong'u va yorug' rejim mavzulari (`ThemeContext`).

### Real-Time & Videokonferensiya:
- **LiveKit WebRTC** (`livekit-client` v2.22.3) — yuqori sifatli jonli video va audio uchrashuvlar xonasi.
- **Emoji Mart** (`emoji-mart`, `@emoji-mart/data`) — video uchrashuv vaqtida jonli emoji reaksiyalari va chat.
- **WebSocket** — ticket tizimi asosida ishlaydigan real-vaqt bildirishnomalari (`NotificationSocket.js`).
- **Firebase Cloud Messaging (FCM)** (`firebase` v12.13.0) — brauzer orqali veb push-xabarnomalarni qabul qilish (Service Worker orqali).

### Ma'lumotlarni boshqarish va vizualizatsiya:
- **@hello-pangea/dnd** (v18.0.1) — vazifalar va loyihalarni erkin surish uchun Drag-and-Drop (Kanban board).
- **Recharts** (v3.8.1) — dinamik grafiklar, diagrammalar va analitik ko'rsatkichlar.
- **Axios** (v1.15.2) — REST API so'rovlari, JWT token boshqaruvi va interceptorlar.
- **Day.js** (v1.11.20) — sanalar va vaqtlarni formatlash hamda hisoblash.

### Hisobot va Eksport:
- **ExcelJS & File-Saver** (`exceljs`, `file-saver`, `papaparse`) — ma'lumotlarni Excel (.xlsx) va CSV formatlariga eksport qilish.
- **jsPDF & AutoTable** (`jspdf`, `jspdf-autotable`) — jadval va hisobotlarni PDF shaklida shakllantirish va yuklab olish.
- **React Easy Crop** (`react-easy-crop`) — foydalanuvchi profil rasmini qirqish va moslashtirish.

---

## 👥 Foydalanuvchi Rollari (RBAC - Role-Based Access Control)

Tizim ko'p darajali rollar arxitekturasiga ega bo'lib, har bir rol uchun alohida ruxsatlar belgilangan:
1. **Admin** (`/admin/*`) — butun tizim, foydalanuvchilar, moliya, barcha hisobotlar va sozlamalarni to'liq boshqarish.
2. **Manager** (`/manager/*`) — loyihalar, topshiriqlar, arizalar va xodimlarni boshqarish.
3. **Employee (Xodim)** (`/employee/*`) — shaxsiy topshiriqlar, biriktirilgan loyihalar va uchrashuvlar bilan ishlash.
4. **Auditor (Nazoratchi)** (`/auditor/*`) — tizimdagi harakatlarni kuzatish (`AuditLog`), tekshirish va tahlil qilish.
5. **Accountant (Hisobchi)** (`/accountant/*`) — moliyaviy oqimlar, maoshlar, to'lovlar va moliyaviy hisobotlar.

---

## 🚀 Amalga oshirilgan Ishlar va Mavjud Imkoniyatlar (Modullar)

### 1. Autentifikatsiya va Xavfsizlik
- Login va sessiyalarni boshqarish (JWT Access & Refresh tokenlar).
- Rol tanlash sahifasi (`/role`) — bir nechta rolga ega bo'lgan foydalanuvchilar uchun qulay interfeys.
- `ProtectedRoute` orqali ruxsat etilmagan sahifalarga kirishni cheklash.

### 2. Onlayn Uchrashuvlar (Meeting Room)
- **LiveKit WebRTC** integratsiyasi: video, audio, ekran ulashish (screen sharing).
- Jonli ishtirokchilar ro'yxati va ularning holati (mikrofon, kamera).
- Jonli chat va xabarlashuv tizimi.
- Real-vaqt emoji reaksiyalari paneli (animatsiyali ekran reaksiyalari).
- Uchrashuv ma'lumotlari va tafsilotlari yon paneli (drawers).

### 3. Loyihalar va Vazifalar (Projects & Tasks)
- **Kanban doskasi**: Vazifalarni bosqichma-bosqich (Rejalashtirilgan, Jarayonda, Bajarildi va h.k.) surish (drag-and-drop).
- Loyihalar ro'yxati, filtrlash, muddatlarni kuzatish va bajaruvchilarni belgilash.
- Shaxsiy vazifalar bo'limi (`MyTasks`) — xodimning o'ziga biriktirilgan vazifalari.
- Vazifa yaratish, tahrirlash, biriktirilgan fayllar va izohlarni boshqarish.

### 4. Moliya Boshqaruvi (Finance)
- **To'lovlar (Payments)** — kirim va chiqim to'lovlarini ro'yxatga olish, filtrlash.
- **Oylik maoshlar (Salary)** — xodimlarning oylik maoshlari va avans hisob-kitoblari.
- **Moliya tarixi (Finance History)** — tranzaksiyalar tarixi va to'lovlar auditi.

### 5. Arizalar va Vakansiyalar (Applications)
- Kelib tushgan rezyume va arizalarni qabul qilish hamda ko'rib chiqish.
- Arizalar batafsil ko'rinishi (`ApplicationDetail`) va statuslarini o'zgartirish.
- Lavozimlar (`Positions`) va Hududlar (`Regions`) katalogini boshqarish.

### 6. Analitika va Hisobotlar (Analytics & Reports)
- **Dashboard / Analytics** — interaktiv diagrammalar (`Recharts`) orqali statistik ma'lumotlar.
- **Xodimlar bo'yicha hisobot (Employee Reports)**.
- **Loyihalar hisoboti (Project Reports)**.
- **Xarajat so'rovlari (Cost Inquiries)**.
- **Vazifalar hisoboti (Tasks Reports)**.
- Barcha hisobotlarni **Excel** va **PDF** formatlarida bir klik bilan yuklab olish.

### 7. Tizim Harakatlari Jurnali (Audit Log)
- Tizimda kim, qachon va qanday amal bajarganini kuzatib borish jurnali.

### 8. Savatcha (Trash)
- Tasodifan o'chirilgan ma'lumotlar (vazifalar, foydalanuvchilar, loyihalar)ni vaqtinchalik saqlash va qayta tiklash imkoniyati.

### 9. Real-Vaqt Bildirishnomalari va Telegram
- Ticket tizimi asosidagi **WebSocket** kanali orqali tezkor bildirishnomalar.
- **Firebase Web Push** integratsiyasi.
- Foydalanuvchining **Telegram** akkauntini tizimga bog'lash imkoniyati.

---

## 📁 Loyiha Tuzilmasi (Folder Structure)

```plaintext
dc-management-frontend/
├── public/                 # Statik fayllar, rasmlar va firebase-messaging-sw.js
├── src/
│   ├── components/         # Qayta ishlatiluvchi UI komponentlar (Sidebar, Layout, Modallar va h.k.)
│   ├── context/            # React kontekstlari (AuthContext, ThemeContext, PageActionContext)
│   ├── hooks/              # Maxsus hooklar (useImagePaste va h.k.)
│   ├── pages/              # Sahifalar:
│   │   ├── admin/          # Admin paneli (Analytics, Users, Finance, Tasks, Reports, Trash)
│   │   ├── MeetingRoom/    # Jonli video uchrashuv xonasi (LiveKit, Chat, Reaksiyalar)
│   │   ├── MyTasks/        # Shaxsiy vazifalar sahifasi
│   │   ├── Login.jsx       # Tizimga kirish sahifasi
│   │   └── SelectRore.jsx  # Rol tanlash sahifasi
│   ├── service/            # API xizmatlari (Axios so'rovlar, interceptorlar, xatolarni ushlash)
│   ├── styles/             # Global CSS va Tailwind sozlamalari
│   ├── Toast/              # Bildirishnoma (Toast) provayderi
│   ├── firebase.js         # Firebase konfiguratsiyasi va FCM sozlamalari
│   ├── NotificationSocket.js # WebSocket bildirishnomalari mantiqi
│   ├── App.jsx             # Asosiy marshrutlash (Routes) va ilova yadrosi
│   └── main.jsx            # Ilova kirish nuqtasi
├── .env                    # Muhit o'zgaruvchilari (API manzillari)
├── package.json            # Paketlar va bog'liqliklar ro'yxati
├── vite.config.js          # Vite konfiguratsiyasi
└── README.md               # Loyiha hujjatlari
```

---

## ⚙️ O'rnatish va Ishga Tushirish

### 1. Talablar
- **Node.js**: v18.0.0 yoki undan yuqori
- **npm** yoki **yarn**

### 2. Repozitoriy klonlash
```bash
git clone https://github.com/abduvosidvaliyev/boshqaruv.git
cd boshqaruv
```

### 3. Bog'liqliklarni o'rnatish
```bash
npm install
```

### 4. Muhit o'zgaruvchilarini sozlash
Loyiha ildizida `.env` faylini yarating va quyidagi manzilni kiriting:
```env
VITE_BASE_URL=https://backend.raqamlinazorat.uz/api
```

### 5. Loyihani ishga tushirish (Development rejimida)
```bash
npm run dev
```
Brauzerda `http://localhost:5173` manziliga o'ting.

### 6. Loyihani yig'ish (Production build)
```bash
npm run build
```
Yig'ilgan fayllar `dist/` jildiga tushadi va ularni istalgan serverga joylashtirish mumkin.
