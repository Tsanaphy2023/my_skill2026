# my_skill2026

คลังรวมชุดทักษะความเชี่ยวชาญ (Agent Skills & Plugins) ฉบับสมบูรณ์ พ.ศ. 2569 (2026) สำหรับการพัฒนาตำราวิชาการ หนังสือเรียน งานวิจัยวิทยาศาสตร์ ชีววิทยา ฟิสิกส์ การจำลองระบบเสมือนจริง AR/XR และการพัฒนาซอฟต์แวร์ระดับ Masterclass โดย **ผู้ช่วยศาสตราจารย์ ดร.ชีวะ ทัศนา**

---

## 📂 โครงสร้างการจัดเก็บ (Repository Structure)

```
my_skill2026/
├── skills/                     # ทักษะระดับสากลและงานวิชาการทั่วไป (Global Custom Skills)
│   ├── academic-content-architect/
│   ├── anti-ai-slop/
│   ├── ar-simulation-builder/
│   ├── citation-formatter/
│   ├── doc-summary/
│   ├── editing-pass/
│   ├── feedback-synthesizer/
│   ├── flashcard-generation/
│   ├── interactive-3d-lab-builder/
│   ├── literature-review/
│   ├── modern-academic-textbook/
│   ├── note-taking/
│   ├── outline-generator/
│   ├── physics-course-visual-builder/
│   ├── physics-textbook-layout-architect/
│   ├── rbru-mooc-course-builder/
│   ├── research-synthesis/
│   ├── source-analysis/
│   └── voice-matching/
└── plugins/                    # ปลั๊กอินและทักษะเฉพาะทาง (Specialized Domain Plugins)
    ├── google-antigravity-sdk/ # Google Antigravity & RBRU Academic Formatter
    ├── science/                # ชีววิทยาศาสตร์ ชีวสารสนเทศ และสไตล์ อ.ชีวะ ทัศนา
    ├── modern-web-guidance-plugin/ # เทคโนโลยีเว็บสมัยใหม่และ Chrome Extensions
    ├── flutter/                # Flutter & Dart Engineering
    ├── firebase/               # Firebase Suite (Firestore, Auth, AI Logic)
    ├── chrome-devtools-plugin/ # การดีบักและวัดประสิทธิภาพเว็บ
    └── android-cli-plugin/     # เครื่องมือพัฒนา Android CLI
```

---

## 🌟 หมวดหมู่ทักษะสำคัญ (Key Skill Categories)

### 1. 🎓 สถาปัตยกรรมตำราวิชาการและระบบการสอน (Academic & Textbook Architecture)
* **`rbru-academic-formatter`**: มาตรฐานการจัดรูปแบบหนังสือวิชาการ เอกสารคำสอน และคู่มือของมหาวิทยาลัยราชภัฏรำไพพรรณี (RBRU) พร้อมระบบกล่องแบนเนอร์หัวบทวิชาการ (Chapter Banner Box) ขนาดฟอนต์ 44pt/25pt/29pt, ภาคผนวก ก, และหน้าประวัติผู้เขียน ผศ.ดร.ชีวะ ทัศนา แบบ Executive Monograph จบใน 1 หน้าเดียว
* **`physics-textbook-layout-architect`**: ระบบสถาปัตยกรรมและมาตรฐานการจัดรูปแบบตำราฟิสิกส์ระดับมหาวิทยาลัย สกัดจาก Serway & Jewett และ Tipler & Mosca
* **`modern-academic-textbook`**: การจัดทำตำราวิชาการระดับ Masterclass สไตล์ MIT Press, Springer, Cambridge
* **`academic-content-architect`**: กรอบการออกแบบเนื้อหาเชิงระบบตาม Bloom's Taxonomy, Active Learning Cycle (Input → Process → Output) และ OBE
* **`tsana-writing-style`**: มาตรฐานภาษา สไตล์การสอน ประวัติศาสตร์วิทยาศาสตร์ และการไม่ใช้เครื่องหมายทวิภาค (`:`) ของ ดร.ชีวะ ทัศนา
* **`rbru-mooc-course-builder`**: ระบบสร้างและเชื่อมโยงรายวิชาบน RBRU E-Learning / MOOC

### 2. 🔬 วิทยาศาสตร์ ชีววิทยา และชีวสารสนเทศ (Science & Bio-Informatics)
* รวบรวมระบบสืบค้นและวิเคราะห์ข้อมูลพันธุกรรม โครงสร้างโปรตีน ยา และวรรณกรรมวิชาการสากล:
  * **AlphaFold & Foldseek**: ดึงและวิเคราะห์โครงสร้าง 3 มิติของโปรตีน
  * **ChEMBL, PubChem & OpenFDA**: ฐานข้อมูลสารชีวโมเลกุล ยา และความปลอดภัย
  * **Ensembl, ClinVar, dbSNP & gnomAD**: จีโนมมนุษย์ ตัวแปรพันธุกรรม และความสัมพันธ์ทางคลินิก
  * **PyMOL**: การเรนเดอร์ภาพโครงสร้าง 3 มิติโมเลกุลระดับสูง
  * **PubMed, Europe PMC, arXiv, bioRxiv & OpenAlex**: เครื่องมือสืบค้นงานวิจัยขั้นสูง

### 3. 🌐 การจำลองเสมือนจริง 3 มิติ และเว็บสมัยใหม่ (AR / 3D Simulation & Modern Web)
* **`ar-simulation-builder`**: สร้างแบบจำลองฟิสิกส์ AR บนเว็บด้วย MediaPipe Hands และ Three.js/A-Frame PBR Shaders
* **`interactive-3d-lab-builder`**: แล็บจำลอง 3D ไร้สัมผัสพร้อมเครื่องสังเคราะห์เสียง Web Audio API
* **`modern-web-guidance` & `chrome-extensions`**: แนวปฏิบัติสากลสำหรับ Front-end และการพัฒนาส่วนขยาย Chrome

### 4. 📱 การพัฒนาแอปพลิเคชัน (Mobile & Cloud Engineering)
* **`flutter` & `dart` (20+ skills)**: สถาปัตยกรรมแอปพลิเคชัน, ทดสอบยูนิตเทสต์, Reactive State Management, FFI Native Assets
* **`firebase` (10+ skills)**: Firestore, Security Rules, Firebase AI Logic, App Hosting

### 5. ✍️ วิจัยและการประพันธ์เชิงวิชาการ (Research & Academic Writing)
* **`anti-ai-slop`**: ขจัดคำฟุ่มเฟือย AI และคืนความเป็นธรรมชาติให้ภาษาไทยวิชาการ
* **`research-synthesis` & `literature-review`**: ตารางเมทริกซ์สังเคราะห์งานวิจัยและวิเคราะห์ช่องว่างทางวิชาการ
* **`citation-formatter`**: จัดรูปแบบการอ้างอิงและบรรณานุกรมมาตรฐานสากล (APA, MLA, Chicago)

---

## 🛠️ วิธีการติดตั้งและใช้งาน (Installation)

คัดลอกโฟลเดอร์ไปยังระบบการตั้งค่าของ Antigravity / Gemini:

```bash
# ติดตั้งไปยัง Global Configuration
cp -R skills/* ~/.gemini/config/skills/
cp -R plugins/* ~/.gemini/config/plugins/
```

---

© 2026 ผู้ช่วยศาสตราจารย์ ดร.ชีวะ ทัศนา (Asst. Prof. Dr. Chewa Thassana)  
สาขาวิชาฟิสิกส์ คณะวิทยาศาสตร์และเทคโนโลยี มหาวิทยาลัยราชภัฏรำไพพรรณี
