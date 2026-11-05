# كرك شات — Karak Chat

## وثائق التحليل الهندسي
- `docs/SYSTEM_ANALYSIS.md` — الوثيقة الرسمية: النطاق + SRS + NFR + ERD + Backend
- `docs/COMPREHENSIVE_ANALYSIS.md` — التحليل الشامل (8 مستخدمين + 12 وحدة + UML)
- `docs/BUSINESS_RULES.md` — قواعد العمل (BR-1..BR-5)
- `docs/UML_DESIGN.md` — Use Case, Activity, Sequence, Component, Deployment
- `docs/SRS_Karak_Chat_v2.md` — مخطط المتطلبات
- `docs/ERD.md` — مخطط العلاقات (40+ جدولاً)
- `docs/ERD_MERMAID.md` — ERD كامل بصيغة Mermaid (10 وحدات)
- `docs/UML_PLANTUML.md` — Use Case, Activity, Sequence, Component, Deployment (PlantUML)
- `docs/API_SPEC.md` — مواصفات API

## الهيكل
```
karak_chat/
├── mobile_app/Flutter/{auth,home,rooms,voice_chat,messages,profile,wallet,gifts,vip,settings}
├── backend/{authentication,users,rooms,audio,messaging,wallet,gifts,ranking,notifications,app}
├── admin_dashboard/
└── database/{migrations,seeds}
```

## Backend (Python FastAPI + PostgreSQL)
```bash
cp backend/.env.example backend/.env
pip install -r backend/requirements.txt
uvicorn backend.app.main:app --reload --port 8000
```
Endpoints: `/api/v1/auth/*`, `/rooms/*`, `/wallet/*`, `/gifts/*`, `/messages/*`, WebSockets: `/audio/ws/room/{id}`, `/messages/ws/chat/{id}`

## Mobile (Flutter)
```bash
cd mobile_app/Flutter
flutter pub get
flutter run
```

## Admin (Next.js React)
```bash
cd admin_dashboard
npm install
npm run dev
```

## Database
```bash
psql -U user -d karak_chat -f database/migrations/001_initial_schema.sql
psql -U user -d karak_chat -f database/migrations/002_extended_schema.sql
psql -U user -d karak_chat -f database/migrations/003_system_analysis_schema.sql
psql -U user -d karak_chat -f database/migrations/004_comprehensive_schema.sql
psql -U user -d karak_chat -f database/seeds/seed.sql
```

## Docker
```bash
docker-compose up -d
```
