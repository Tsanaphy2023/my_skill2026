---
name: rbru-latex-textbook-builder
description: >-
  สร้าง พัฒนา และ format ตำราวิชาการ LaTeX มาตรฐานมหาวิทยาลัยราชภัฏรำไพพรรณี (RBRU)
  ด้วย XeLaTeX + ภาษาไทยวิชาการ ครอบคลุม: integrate งานวิจัยผู้เขียน, เพิ่มบทเรียนใหม่
  พร้อมภาพ TikZ, แก้ format แผนบริหารการสอน, ป้องกัน orphan word, เปลี่ยนชื่อตำราทั้งเล่ม
  และ Compile PDF ด้วย xelatex + makeindex สำหรับตำราระดับ Masterclass
---

# RBRU LaTeX Textbook Builder

## Overview

Skill นี้ช่วย agent ในการสร้างและพัฒนาตำราวิชาการ LaTeX สำหรับ มหาวิทยาลัยราชภัฏรำไพพรรณี (RBRU)
โดยใช้ XeLaTeX + Thai Unicode ครอบคลุมตั้งแต่การวิเคราะห์โครงสร้าง, integrate งานวิจัยผู้เขียน,
เพิ่มเนื้อหาพร้อมภาพ TikZ, format มาตรฐาน, ไปจนถึง Compile PDF สมบูรณ์

**Trigger:** ใช้เมื่อผู้ใช้บอกให้ "ปรับปรุง", "เพิ่มบท", "แก้ไขตำรา", "compile" โปรเจกต์
LaTeX ที่ใช้ XeLaTeX กับภาษาไทย โดยเฉพาะโปรเจกต์ใน `/04_Education_Exam/Latex2026/`

---

## Dependencies

- **modern-academic-textbook** — มาตรฐาน layout ตำราวิชาการ RBRU (Springer/MIT Press style)
- **rbru-academic-formatter** — ระเบียบวิชาการและรูปแบบเอกสารมาตรฐาน มรภ.รำไพพรรณี
- **tsana-writing-style** — รูปแบบการเขียนและภาษาไทยวิชาการของ ผศ.ดร.จิรภัทร จันทมาลี
- **physics-textbook-layout-architect** — สถาปัตยกรรม layout ตำราเรียนระดับสากล

---

## Quick Start

```
ผู้ใช้: ปรับปรุงตำรา จุลชีววิทยาการเกษตร
Agent: อ่าน SKILL.md → Phase 1 วิเคราะห์โครงสร้าง → Phase 2 เพิ่มเนื้อหา → Phase 3 format → Compile
```

---

## Workflow

### Phase 1: วิเคราะห์โครงสร้างโปรเจกต์

1. อ่าน `main.tex` เพื่อดูโครงสร้างบท ไฟล์ที่ `\include` และ packages ที่ใช้
2. อ่าน `styles/*.sty` เพื่อทำความเข้าใจ color palette, custom environments, font settings
3. ตรวจ `\definecolor` ทุกตัว — หาก TikZ node อ้างอิงสีที่ไม่ได้นิยาม ให้เพิ่มใน `.sty` ทันที
4. อ่าน chapter ที่เกี่ยวข้องกับ task ที่รับมา

**สิ่งที่ต้องตรวจก่อนเริ่ม:**
```bash
# ตรวจ compile error เบื้องต้น
xelatex -interaction=nonstopmode main.tex 2>&1 | grep "^!"
# ตรวจไฟล์ที่มีอยู่ใน chapters/
ls chapters/*.tex
```

---

### Phase 2: Integrate งานวิจัยผู้เขียน

1. **ค้นหางานวิจัย** จาก Google Scholar URL ของผู้เขียน — ใช้ `browser_subagent` เปิดหน้า Scholar
2. **Map งานวิจัยกับบท:** สร้างตาราง mapping ว่างานวิจัยชิ้นใดเกี่ยวข้องกับบทใด
3. **เพิ่ม citations ใน APA 7** รูปแบบ:
   ```latex
   % ในเนื้อหา
   (จันทมาลี, 2567)
   % ใน references.tex
   จันทมาลี, จ. (2567). ชื่อบทความ. \textit{ชื่อวารสาร}, \textit{เล่ม}(ฉบับ), หน้า--หน้า.
   \url{https://doi.org/...}
   ```
4. **เพิ่มเนื้อหาที่เกี่ยวข้อง** เข้า section ที่เหมาะสมในแต่ละบท โดยอ้างอิงงานวิจัย

---

### Phase 3: เพิ่มบทเรียนใหม่

แต่ละบทต้องมีโครงสร้างมาตรฐาน:

```latex
\chapter{ชื่อบท}
\label{chap:chXX}

\section*{แผนบริหารการสอนประจำบทที่ XX}
\addcontentsline{toc}{section}{แผนบริหารการสอนประจำบทที่ XX}

\noindent\textbf{หัวข้อเนื้อหาประจำบท}
\begin{enumerate}
    \item ...
\end{enumerate}

\noindent\textbf{วัตถุประสงค์เชิงพฤติกรรม}
\begin{enumerate}
    \item ...
\end{enumerate}

\noindent\textbf{กิจกรรมการเรียนการสอน}
\begin{enumerate}
    \item ...
\end{enumerate}

\noindent\textbf{สื่อการเรียนการสอน}
\begin{enumerate}
    \item ...
\end{enumerate}

\noindent\textbf{การประเมินผล}
\begin{enumerate}
    \item ...
\end{enumerate}

\newpage

% เนื้อหา sections...

\section*{คำถามทบทวนท้ายบทที่ XX}
\addcontentsline{toc}{section}{คำถามทบทวนท้ายบทที่ XX}
\begin{enumerate}
    \item ...
\end{enumerate}
\clearpage
```

**กฎ TikZ สำหรับภาพประกอบ:**
- ตรวจว่าสีทุกตัวนิยามใน `.sty` ก่อนใช้ใน `\node` หรือ `\fill`
- ใช้ `[H]` สำหรับ float position: `\begin{figure}[H]`
- ใช้ `scale=0.88` หรือ `scale=0.90` เพื่อให้พอดีหน้า

---

### Phase 4: Format มาตรฐานภาษาไทยวิชาการ

#### 4.1 แผนบริหารการสอน — ปรับทั้งเล่มด้วย Python script:

```python
import os, re

PLAN_HEADERS = ["หัวข้อเนื้อหาประจำบท", "วัตถุประสงค์เชิงพฤติกรรม",
                "กิจกรรมการเรียนการสอน", "สื่อการเรียนการสอน", "การประเมินผล"]

def process(filepath):
    with open(filepath, 'r', encoding='utf-8') as f:
        content = f.read()
    for h in PLAN_HEADERS:
        content = re.sub(r'(?<!noindent\\)\\textbf\{' + re.escape(h) + r'\}',
                         r'\\noindent\\textbf{' + h + r'}', content)
    # itemize → enumerate ใน plan section
    def fix_plan(m):
        block = m.group(0)
        block = block.replace(r'\begin{itemize}', r'\begin{enumerate}')
        block = block.replace(r'\end{itemize}', r'\end{enumerate}')
        return block
    content = re.sub(r'(\\section\*\{แผนบริหารการสอน.*?\\newpage)', fix_plan,
                     content, flags=re.DOTALL)
    with open(filepath, 'w', encoding='utf-8') as f:
        f.write(content)
```

#### 4.2 ภาษาไทยวิชาการ — กฎที่ต้องปฏิบัติ:

| ผิด | ถูก |
|-----|-----|
| `ได้แก่:` | `ได้แก่` (ลบ colon) |
| `ดังนี้:` | `ดังนี้` (ลบ colon) |
| `\textbf{หัวข้อ}` (มี indent) | `\noindent\textbf{หัวข้อ}` |
| `\begin{itemize}` ในแผนบริหาร | `\begin{enumerate}` |

#### 4.3 ป้องกัน Orphan Word:

เพิ่มใน `styles/*.sty`:
```latex
\XeTeXlinebreakskip = 0pt plus 2pt minus 0.5pt
\setlength{\emergencystretch}{2.5em}
```

สำหรับ item ที่ลงท้ายด้วย "ได้" โดดๆ ให้ขยายเป็น "ได้อย่างถูกต้อง" หรือ "ได้อย่างครบถ้วน"

#### 4.4 การเปลี่ยนชื่อตำราทั้งเล่ม:

```python
REPLACEMENTS = [
    ("จุลชีววิทยาสำหรับการเกษตร", "จุลชีววิทยาการเกษตร"),
    ("MICROBIOLOGY FOR AGRICULTURE", "AGRICULTURAL MICROBIOLOGY"),
    ("Microbiology for Agriculture", "Agricultural Microbiology"),
]
# วน loop ทุก .tex และ .sty ใน project directory
```

#### 4.5 การย่อหน้า 1 Tab (1.25 cm) และการจัดตำแหน่งเนื้อหาให้ตรงกับชื่อหัวข้อ:
- ระเบียบวิชาการ มรภ.รำไพพรรณี กำหนดให้พารากราฟเนื้อหาย่อหน้า 1 Tab = `1.25cm`
- ต้องใช้ `\RequirePackage{indentfirst}` เพื่อบังคับให้ย่อหน้าตั้งแต่พารากราฟแรกใต้หัวข้อ (โดยปกติ LaTeX จะไม่ย่อหน้าพารากราฟแรก)
- กำหนด `\setlength{\parindent}{1.25cm}` และ `\setlength{\parskip}{4pt plus 1pt minus 1pt}`
- จัดกล่องเลขหัวข้อด้วย `\makebox[1.25cm][l]{\thesection}` ใน `\titleformat{\section}` เพื่อให้ตัวอักษรแรกของชื่อหัวข้อเริ่มที่ระยะ 1.25 cm พอดี ซึ่งจะตรงกับแนวขอบซ้ายของบรรทัดแรกของเนื้อหา (1 Tab) อย่างสมบูรณ์แบบ
- ต้องใช้ `\titlespacing{\section}` (แบบไม่มีเครื่องหมาย `*`) เพื่อป้องกันไม่ให้คำสั่ง suppress indent ไปยกเลิกการย่อหน้าของ `indentfirst`

#### 4.6 การจัดหัวข้อย่อย (Subsection เช่น 1.4.1) และการย่อหน้าเนื้อหาตามระดับลำดับชั้น (Hierarchical Indentation):
- **ตัดภาษาอังกฤษในวงเล็บออกจากชื่อบท (Chapter Titles):** ชื่อบทเรียนในกล่องแบนเนอร์ต้องเป็นภาษาไทยล้วน เช่น `\chapter{ทฤษฎีสัมพัทธภาพพิเศษ}` (ตัด `(Special Relativity)` ออก)
- **หัวข้อย่อยระดับที่ 2 (`\subsection` เช่น 1.4.1):**
  - กำหนดให้ตัวเลขหัวข้อย่อยย่อหน้าเข้าไป 1 Tab (`1.25cm`):
    ```latex
    \titlespacing{\subsection}{1.25cm}{14pt plus 3pt minus 2pt}{6pt plus 2pt minus 1pt}
    ```
  - จัดกล่องตัวเลขหัวข้อย่อยด้วย `\makebox[1.25cm][l]{\thesubsection}` ทำให้ตัวอักษรแรกของชื่อหัวข้อย่อยเริ่มที่ระยะ `2.50cm` (2 Tabs)
  - **ปรับย่อหน้าของเนื้อหาตามระดับหัวข้อย่อย (Dynamic Parindent):**
    เนื้อหาใต้ `\subsection` จะต้องย่อหน้า 2 Tabs (`2.50cm`) เพื่อให้ขอบซ้ายของบรรทัดแรกตรงกับตัวอักษรแรกของชื่อหัวข้อย่อย
    โดยใช้ Command Wrappers ครอบเพื่อป้องกันไม่ให้แพ็กเกจคณิตศาสตร์ (`mathtools`) รีเซ็ตค่า:
    ```latex
    \let\rbruorigchapter\chapter
    \renewcommand{\chapter}{\global\setlength{\parindent}{1.25cm}\rbruorigchapter}

    \let\rbruorigsection\section
    \renewcommand{\section}{\global\setlength{\parindent}{1.25cm}\rbruorigsection}

    \let\rbruorigsubsection\subsection
    \renewcommand{\subsection}{\global\setlength{\parindent}{2.50cm}\rbruorigsubsection}

    \let\rbruorigsubsubsection\subsubsection
    \renewcommand{\subsubsection}{\global\setlength{\parindent}{3.75cm}\rbruorigsubsubsection}
    ```

#### 4.7 แผนบริหารการสอนประจำบท (Lesson Plan per Chapter):
- ทุกบทเรียนต้องมี **แผนบริหารการสอนประจำบทที่ X** (`\section*{แผนบริหารการสอนประจำบทที่ X}`) พร้อม `\addcontentsline{toc}{section}{แผนบริหารการสอนประจำบทที่ X}`
- ประกอบด้วย 5 องค์ประกอบหลักตามมาตรฐาน RBRU (ห้ามใส่เครื่องหมาย `:` ท้ายหัวข้อ):
  1. `\noindent\textbf{หัวข้อเนื้อหาประจำบท}` (ใช้ `\begin{enumerate}`)
  2. `\noindent\textbf{วัตถุประสงค์เชิงพฤติกรรม}` (ใช้ `\begin{enumerate}`)
  3. `\noindent\textbf{กิจกรรมการเรียนการสอน}` (ใช้ `\begin{enumerate}`)
  4. `\noindent\textbf{สื่อการเรียนการสอน}` (ใช้ `\begin{enumerate}`)
  5. `\noindent\textbf{การประเมินผล}` (ใช้ `\begin{enumerate}`)
- จบด้วย `\newpage` ก่อนเริ่มเนื้อหาหัวข้อแรกของบทเรียน

#### 4.8 รูปแบบคำบรรยายภาพและตาราง (Caption Typography):
- **มาตรฐานตัวอักษร:** คำนำหน้า (Label) เช่น "ภาพที่ X.X" หรือ "ตารางที่ X.X" ต้องเป็น **ตัวหนา** (`labelfont={bf}`) ส่วนข้อความชื่อภาพและตาราง ต้องเป็น **ตัวบางปกติ** (`textfont={normalfont}`)
- ไม่ใส่เครื่องหมายทวิภาค (`:`) ให้ใช้การเว้นวรรค 1 quad (`labelsep=thaisep` ที่นิยาม `\DeclareCaptionLabelSeparator{thaisep}{\quad}`)
- กำหนดใน `styles/*.sty`:
```latex
\RequirePackage{caption}
\DeclareCaptionLabelSeparator{thaisep}{\quad}
\captionsetup{labelsep=thaisep}
\captionsetup[table]{position=top, skip=6pt, labelfont={bf,color=primaryThemeColor}, textfont={normalfont}, labelsep=thaisep}
\captionsetup[figure]{position=bottom, skip=8pt, labelfont={bf,color=primaryThemeColor}, textfont={normalfont}, labelsep=thaisep}
```

#### 4.9 การจัดการชื่อหัวข้อและการตัดคำ (Section Title Formatting & Word Binding):
- **ลบเครื่องหมายทวิภาค (`:`) ออกจากชื่อหัวข้อ:** ห้ามใส่เครื่องหมาย `:` ใน `\section`, `\subsection`, รวมถึงข้อความนำ เช่น "ตามความสัมพันธ์", "ดังนี้", "ประกอบด้วย"
- **ลบภาษาอังกฤษในวงเล็บออกจากชื่อหัวข้อ:** หัวข้อหลักและหัวข้อย่อยต้องเป็นภาษาไทยวิชาการที่กระชับและสง่างาม โดยให้นำคำศัพท์ภาษาอังกฤษในวงเล็บไปใส่ไว้ในประโยคเปิดของเนื้อหาใต้หัวข้อนั้นในรูปตัวหนาแทน เช่น:
  ```latex
  % ในหัวข้อ (ไม่มีภาษาอังกฤษในวงเล็บ)
  \subsection{การยืดออกของเวลา}
  % ในเนื้อหาบรรทัดแรก
  ปรากฏการณ์\textbf{การยืดออกของเวลา (Time Dilation)} พิจารณานาฬิกาแสง...
  ```
- **การจัดบรรทัดชื่อหัวข้อยาวและป้องกันการตัดคำ (Title Line Breaks & Word Binding):** ในกรณีที่ชื่อหัวข้อยาวจนตัดขึ้นบรรทัดใหม่ ให้ใช้ optional argument ของ `\section` โดยกำหนดชื่อเต็มสำหรับสารบัญ และจัดตัดบรรทัดด้วย `\\` ด้วยตนเอง เพื่อป้องกันคำสำคัญขาดออกจากกัน เช่น:
  ```latex
  \section[ผลสืบเนื่องทางจลนศาสตร์ การยืดออกของเวลาและการหดสั้นของความยาว]{ผลสืบเนื่องทางจลนศาสตร์ การยืดออกของเวลา\\และการหดสั้นของความยาว}
  ```
  เพื่อบังคับให้คำว่า "การ" และ "หดสั้น" อยู่บรรทัดเดียวกันเสมอ

---

### Phase 5: Compile PDF

```bash
# Pass 1 — สร้าง .aux, .idx
xelatex -interaction=nonstopmode main.tex

# Pass 2 — สร้าง index
makeindex main.idx

# Pass 3 — รวม index เข้า PDF
xelatex -interaction=nonstopmode main.tex

# ตรวจ error
xelatex -interaction=nonstopmode main.tex 2>&1 | grep -E "(Output written|^!|Fatal)"
```

**Error ที่พบบ่อยและวิธีแก้:**

| Error | สาเหตุ | วิธีแก้ |
|-------|--------|---------|
| `Undefined color agriXxx` | ใช้ชื่อสีที่ไม่ได้นิยาม | เพิ่ม `\definecolor{agriXxx}{HTML}{RRGGBB}` ใน `.sty` |
| `! Package fontspec Error` | Font ไม่มีในระบบ | ตรวจ `fc-list | grep Sarabun` |
| `Runaway argument` | `\\` ซ้ำซ้อนใน TikZ node | ตรวจ `\\\\` ใน node text |
| `Missing $ inserted` | ตัวอักษรพิเศษใน text mode | ใส่ `$...$` หรือ `\text{...}` |

---

### Phase 6: Push GitHub

```bash
cd /path/to/Latex2026
git add 07_*/
git commit -m "feat(microbio): สรุปการเปลี่ยนแปลง"
git push origin main
```

---

## โครงสร้างไฟล์มาตรฐาน RBRU

```
ProjectName_LaTeX/
├── main.tex                    # Entry point — \include chapters
├── styles/
│   └── projectname_style.sty   # สี, fonts, custom environments
├── frontmatter/
│   ├── cover.tex               # ปก TikZ
│   ├── title.tex               # หน้าชื่อเรื่อง
│   ├── preface.tex             # คำนำ
│   ├── acknowledgements.tex    # กิตติกรรมประกาศ
│   └── syllabus.tex            # คำอธิบายรายวิชา
├── chapters/
│   ├── introduction.tex        # บทนำ
│   ├── chapter1.tex ... chapterN.tex
│   └── chapter10.tex           # บทใหม่ล่าสุด
├── appendices/
│   └── appendixA.tex ...
└── backmatter/
    ├── references.tex          # บรรณานุกรม APA 7
    └── biography.tex           # ประวัติผู้เขียน
```

---

## Custom Environments ที่ใช้บ่อย

```latex
\begin{definitionbox}{ชื่อกล่อง}   % กล่องนิยามศัพท์
\begin{casestudy}{ชื่อกรณีศึกษา}  % กล่องกรณีศึกษา
\begin{agribox}{ชื่อกล่อง}        % กล่องข้อมูลเกษตร/วิทยาศาสตร์
```

---

---

### Phase 7: การปรับโครงสร้างตำรา (Re-architecting Chapters & Introduction)

เมื่อต้องการปรับโครงสร้างบทเรียน เช่น การยกระดับบทเทคโนโลยี/กรอบแนวคิดให้เป็น **บทนำ (Introduction)** และจัดลำดับบทใหม่:
1. **การสร้างบทนำ (Introduction):**
   - ใช้ `\chapter*{บทนำ\\ชื่อหัวข้อย่อย}` ร่วมกับ `\addcontentsline{toc}{chapter}{บทนำ: ...}` และ `\markboth{...}{...}`
   - บรรจุภาพรวมสถาปัตยกรรม (Architecture), แผนผังบูรณาการเทคโนโลยีรายบท (Curriculum Technology Roadmap Table), และข้อกำหนดประสิทธิภาพ (เช่น Zero-GC Loop, Memory Management)
2. **การกระจายเนื้อหาเฉพาะทาง (Content Distribution):**
   - นำโค้ดเต็มและตัวอย่างการจำลองเฉพาะเรื่อง ย้ายไปรวมไว้ในบททฤษฎีที่ตรงกัน (เช่น ย้ายแบบจำลองอะตอมบอร์ WebXR ไปไว้ในบทกลศาสตร์ควอนตัม)
   - กระจายตัวอย่างการแก้ปัญหาเชิงเทคนิค P-S-C-T ไปเสริมในบทที่เหมาะสม
3. **การจัดลำดับบทใหม่ (Chapter Renumbering):**
   - แก้ไขหมายเลขใน `\section*{แผนบริหารการสอนประจำบทที่ X}` และ `\addcontentsline{toc}{section}{แผนบริหารการสอนประจำบทที่ X}`
   - ตรวจทานและแก้ไขข้อความในเอกสารคำสอน แบบประเมิน และแบบฝึกหัดท้ายบทให้เป็นหมายเลขใหม่
   - ซิงค์เอกสารประกอบทั้งหมดให้ตรงกัน: `main.tex`, `syllabus.tex`, `preface.tex`, `cover.tex`, และ `README.md`
4. **Compile & Index:** รัน `xelatex -> makeindex -> xelatex` ซ้ำ 2--3 รอบ เพื่อให้ TOC, LOF, LOT, และ Index อัปเดตครบถ้วน 100%

---

### Phase 8: มาตรฐานการจัดรูปแบบตาราง (Academic Table Standards: X.X Above & Bold/Regular)

1. **ตำแหน่งแคปชันตาราง (Caption Placement Above Table):**
   - แคปชันตารางต้องอยู่ **ด้านบนของตารางเสมอ** (ต่างจากรูปภาพที่อยู่ด้านล่าง) โดยวางคำสั่ง `\caption{ชื่อตาราง}` และ `\label{tab:...}` ไว้ก่อนหน้า `\begin{tabularx}` หรือ `\begin{tabular}`
2. **รูปแบบหมายเลขตาราง (Chapter-based X.X Numbering):**
   - ตารางในเนื้อหาทุกบทต้องแสดงเป็นลำดับตามบทเรียน เช่น **ตารางที่ 1.1**, **ตารางที่ 1.2**, **ตารางที่ 2.1**
   - กำหนดใน `.sty`: `\renewcommand{\thetable}{\thechapter.\arabic{table}}`
3. **การจัดสไตล์ตัวอักษรแคปชันตาราง (Bold Label & Regular Title):**
   - คำว่า **ตารางที่ X.X** ต้องเป็น **ตัวหนา** (`labelfont={bf}`)
   - **ชื่อตาราง** ต้องเป็น **ตัวบาง/ตัวปกติ** (`textfont={normalfont}`)
   - เว้นวรรคระหว่างเลขตารางกับชื่อตารางด้วย `\quad` (`\DeclareCaptionLabelSeparator{thaisep}{\quad}`)
   - ตั้งค่าใน `.sty`:
     ```latex
     \captionsetup[table]{position=top, skip=6pt, labelfont={bf}, textfont={normalfont}, labelsep=thaisep}
     ```
4. **ตารางส่วนหน้าเล่ม (Frontmatter Tables):**
   - สำหรับตารางที่ไม่ใช่เนื้อหาบทเรียน (เช่น ตารางแผนการสอน 15 สัปดาห์ ใน `syllabus.tex`) ให้ใช้ `\caption*{...}` เพื่อไม่ให้ถูกนับเป็นหมายเลขเดี่ยว (เช่น ตารางที่ 1) ปะปนในสารบัญตาราง (`\listoftables`)

---

### Phase 9: ภาพประกอบหัวบทเฉพาะแต่ละบทด้วย TikZ (Unique Chapter Banner Motifs)

1. **การจำแนกภาพประกอบตามหมายเลขบท (`\value{chapter}`):**
   - กล่องแบนเนอร์หัวบท `chapterbannerbox` ต้องไม่ใช้ภาพซ้ำกันทุกบท แต่ต้องสร้างสัญลักษณ์และภาพเวกเตอร์ TikZ ที่สะท้อนเนื้อหาของบทนั้นโดยเฉพาะ
   - กำหนดมาโคร `\renderchaptermotif` โดยใช้เงื่อนไข `\ifcase\value{chapter}`:
     - **บทที่ 1 (Spatial XR / AI / Python):** โครงข่ายประสาทเทียมหลายชั้น (DNN nodes/synapses), ข้อต่อกระดูกมือ MediaPipe Hands 21 จุด, พิกัด 3 มิติ และสมการ $\mathcal{L}_{\text{PINN}}$
     - **บทที่ 2 (Special Relativity):** กรวยแสงปริภูมิ-เวลา (Spacetime Light Cone: $ct$ vs $x$), เส้นไฮเพอร์โบลา $s^2$, เส้นทางโฟตอน $45^\circ$, และตัวคูณลอเรนซ์ $\gamma$
     - **บทที่ 3 (Quantum Mechanics):** บ่อศักย์พร้อมระดับชั้นพลังงานควอนไทซ์ $E_n$, ฟังก์ชันคลื่นไซนูซอยด์, กลุ่มหมอกออร์บิทัล $p_z, d$ และเวกเตอร์สปิน $\vec{S}$
     - **บทที่ 4 (Particle Physics):** แผนภาพไฟน์แมน (Feynman Diagram: $q\bar{q} \to g \to \ell^+\ell^-$), เส้นสปริงกลูออน, โครงตาข่ายสมมาตรเกจ และรอยทางอนุภาคชนกัน
     - **บทที่ 5 (Nuclear Physics):** เส้นโค้งพลังงานยึดเหนี่ยวนิวเคลียส $B/A$ vs $A$ จุดสูงสุดที่ $^{56}\text{Fe}$, นิวเคลียสแตกตัวฟิชชัน และการปลดปล่อยนิวตรอนทุติยภูมิ
     - **บทที่ 6 (Quantum Computing):** ทรงกลมบล็อค 3 มิติ (Bloch Sphere) แสดงเวกเตอร์สถานะ $|\psi\rangle$, วงจรเกตควอนตัม Hadamard $[H]$ และ CNOT $[\oplus]$
     - **บทที่ 7 (Astrophysics):** หลุมดำชวาร์ซชิลด์พร้อมจานพอกพูนมวลบิดเบี้ยวจากเลนส์ความโน้มถ่วง, ระบบดาวคู่สัมผัส (DF Hydrae), และระลอกคลื่นความโน้มถ่วง
     - **ส่วนหน้า/หลังเล่ม (Case 0 / Unnumbered):** ตาข่ายกาล-อวกาศไซเบอร์และระลอกคลื่นควอนตัม

---

### Phase 10: การบูรณาการปัญญาประดิษฐ์และการเรียนรู้เชิงลึกในฟิสิกส์ (AI & Deep Learning Integration)

1. **โครงข่ายประสาทเทียมที่รู้ฟิสิกส์ (Physics-Informed Neural Networks: PINNs):**
   - การฝังสมการเชิงอนุพันธ์ย่อย (PDEs) และกฎการอนุรักษ์ลงใน Loss Function: $\mathcal{L} = \mathcal{L}_{\text{data}} + \lambda_{\text{phys}} \mathcal{L}_{\text{physics}}$
   - การประยุกต์ใช้ในพลศาสตร์สัมพัทธภาพและการเรนเดอร์ทัศนศาสตร์เชิงสัมพัทธภาพ (Relativistic Ray Tracing)
2. **การเรียนรู้เชิงลึกในกลศาสตร์ควอนตัม (Neural Network Quantum States: NQS):**
   - การใช้โครงข่ายประสาท (RBM, FermiNet, PauliNet) แก้สมการชเรอดิงเงอร์สำหรับระบบหลายอนุภาค
3. **ฟิสิกส์อนุภาคพลังงานสูง (High-Energy Physics):**
   - การจำแนกเจ็ตอนุภาค (Jet Tagging) ด้วย CNNs และการประกอบรอยทางอนุภาคด้วย Graph Neural Networks (GNNs) ที่ LHC/CERN
4. **ฟิสิกส์นิวเคลียร์และพลังงานฟิวชัน:**
   - การใช้ Deep Reinforcement Learning (DRL) ในการควบคุมสนามแม่เหล็กกักเก็บพลาสมาในเตาปฏิกรณ์โทคาแมก (Tokamak Plasma Control)
5. **การเรียนรู้ของเครื่องเชิงควอนตัม (Quantum Machine Learning: QML):**
   - วงจรควอนตัมมีตัวแปรเสริม (PQC), Variational Quantum Eigensolver (VQE), และสปินคิวบิตสถานะของแข็ง
6. **ฟิสิกส์ดาราศาสตร์ (Astrophysics & Gravitational Waves):**
   - การใช้ 1D/2D CNNs ตรวจจับคลื่นความโน้มถ่วงจากสัญญาณ LIGO/Virgo แบบเรียลไทม์ และการประมวลผลภาพถ่ายดาราศาสตร์ JWST

---

### Phase 11: มาตรฐานการบูรณาการงานวิจัยของผู้เขียน (Author Research Integration Standard)

1. **การเชื่อมโยงผลงานวิจัยจริงของผู้เขียน (ผศ.ดร.ชีวะ ทัศนา / Dr. Chewa Thassana):**
   - นำผลงานวิจัยที่ได้รับการตีพิมพ์ในระดับสากลและวารสารวิชาการ มาสกัดเป็นเนื้อหาและกรณีศึกษาในบทที่ตรงกันอย่างลึกซึ้ง:
     - **ฟิสิกส์ดาราศาสตร์ (Astrophysics):** งานวิจัยระบบดาวคู่สัมผัส DF Hydrae (Thassana et al., 2014, 2016), การวิเคราะห์กระจุกดาวเปิดและทรงกลม M3, M35, M67, M45 ด้วยเทคนิค CCD Photometry และ Isochrone Fitting (Thassana et al., 2012, 2015; ทัศนา, 2558), และตำราการวิเคราะห์ข้อมูลดาราศาสตร์/Astrometry (ทัศนา, 2557)
     - **กลศาสตร์ควอนตัมและสถานะของแข็ง (Quantum Mechanics & Solid-State):** งานวิจัยการจำลองโครงสร้างอิเล็กทรอนิกส์ด้วยระเบียบวิธี $\text{LSDA}+U$ การศึกษาอันตรกิริยาแลกเปลี่ยน $J$ และพลังงานคูลอมบ์ $U$ ในสารประกอบแม่เหล็ก $\text{MnO}$ และ $\text{NiO}$ (Thassana et al., 2011, 2012, 2013)
     - **สารสนเทศควอนตัม (Quantum Information):** การเชื่อมโยงอันตรกิริยาแลกเปลี่ยนสปินควอนตัม $J$ สู่การพัฒนาฮาร์ดแวร์สปินคิวบิตในสถานะของแข็ง (Solid-State Spin Qubits)
2. **การอ้างอิงและบรรณานุกรมวิชาการ:**
   - อ้างอิงในเนื้อหาด้วยรูปแบบวิชาการสากล (Author, Year) หรือ (ผู้แต่ง, ปี พ.ศ.)
   - บรรจุรายการอ้างอิงฉบับสมบูรณ์ใน `backmatter/references.tex` พร้อม DOI หรือชื่อการประชุมวิชาการ

---

## Common Mistakes

1. **ลืมตรวจสีก่อน compile** — ทุกครั้งที่เพิ่ม TikZ ใหม่ ให้ grep หาชื่อสีและตรวจใน `.sty`
2. **Colon ท้ายประโยค** — ภาษาไทยวิชาการไม่ใช้ `:` ท้าย `ได้แก่` และ `ดังนี้`
3. **itemize แทน enumerate** ในแผนบริหารการสอน — ใช้ enumerate เสมอสำหรับ 4 หัวข้อหลัก
4. **ลืม \noindent** — หัวข้อในแผนบริหารการสอนต้องชิดซ้ายเสมอ
5. **Compile ครั้งเดียว** — ต้อง compile อย่างน้อย 2 รอบเพื่อให้ ToC, index และ references ถูกต้อง
6. **ลืมซิงค์แผนการสอนใน syllabus.tex** เมื่อมีการปรับลำดับบท — ต้องตรวจเช็กตารางสัปดาห์ใน syllabus ทุกครั้ง
