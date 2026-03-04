# 📘 CPE Senior Project Report (Blockchain & IoT in Supply Chain)

คลังเก็บซอร์สโค้ดสำหรับรูปเล่มโครงงานปริญญานิพนธ์ (CPE492)
พัฒนาโดยใช้เทมเพลตของภาควิชาวิศวกรรมคอมพิวเตอร์ มหาวิทยาลัยเชียงใหม่ (CPE CMU)

---

## 🛠️ 1. สิ่งที่ต้องติดตั้งก่อนเริ่มทำงาน (Prerequisites)

ทุกคนในกลุ่มต้องติดตั้งโปรแกรมพื้นฐานเหล่านี้ในเครื่องตัวเองให้เรียบร้อยก่อน:

### 🪟 สำหรับผู้ใช้ Windows
1. **[MiKTeX](https://miktex.org/download)** (ตัวแปลงโค้ด LaTeX)
   * 🚨 **สำคัญมาก:** ตอนติดตั้ง หน้า Settings จะมีหัวข้อ *Install missing packages on-the-fly* ให้เปลี่ยนเป็น **"Yes"** เท่านั้น!
2. **[Strawberry Perl](https://strawberryperl.com/)** (ต้องใช้รันแพ็กเกจ latexmk)
3. **[Git for Windows](https://git-scm.com/downloads)** (สำหรับจัดการเวอร์ชันโค้ด)
4. **[Visual Studio Code (VS Code)](https://code.visualstudio.com/)** พร้อมติดตั้ง Extension ชื่อ **LaTeX Workshop**

### 🍎 สำหรับผู้ใช้ Mac (macOS)
1. **[MacTeX](https://www.tug.org/mactex/)** (ดาวน์โหลดตัวเต็ม MacTeX.pkg)
   * *หมายเหตุ: Mac มี Perl ติดตั้งมาให้ในเครื่องแล้ว ไม่ต้องโหลดเพิ่ม*
2. **Git** (ปกติมีในเครื่องแล้ว หรือสามารถติดตั้งผ่าน Terminal โดยพิมพ์ `git --version` ระบบจะเด้งให้ติดตั้งถ้ายังไม่มี)
3. **[Visual Studio Code (VS Code)](https://code.visualstudio.com/)** พร้อมติดตั้ง Extension ชื่อ **LaTeX Workshop**

---

## ⚙️ 2. การดาวน์โหลดและการตั้งค่า (Setup)

### Step 2.1: โหลดโปรเจกต์ลงเครื่อง (Clone)
เปิด Terminal (Mac) หรือ Git Bash / Command Prompt (Windows) แล้วพิมพ์คำสั่ง:
```bash
git clone [https://github.com/phuennae/261492-TempTrack-Report.git](https://github.com/phuennae/261492-TempTrack-Report.git)
```

### Step 2.2: ติดตั้งฟอนต์ภาษาไทยและแพ็กเกจของเล่ม
เพื่อให้เล่มแสดงภาษาไทยได้ถูกต้อง ให้เปิด Terminal หรือ Command Prompt แล้วพิมพ์คำสั่งตามระบบปฏิบัติการของตัวเอง:

**👉 สำหรับ Windows (ใช้คำสั่งของ MiKTeX):**
```cmd
miktex packages require latexmk fonts-tlwg fonts-arundina tex-gyre tex-gyre-math
```

**👉 สำหรับ Mac (ใช้คำสั่งของ TeX Live):**
```bash
sudo tlmgr update --self
sudo tlmgr install latexmk fonts-tlwg fonts-arundina tex-gyre tex-gyre-math
```

### Step 2.3: ตั้งค่า VS Code ให้รองรับภาษาไทย (XeLaTeX)
1. เปิดโปรแกรม VS Code 
2. กด `F1` หรือ `Ctrl+Shift+P` (Mac ใช้ `Cmd+Shift+P`)
3. พิมพ์ค้นหาคำว่า `Open User Settings (JSON)` แล้วกด Enter
4. ก๊อปปี้โค้ดด้านล่างนี้ ไปวางแทรกไว้ **ด้านในสุด** ของวงเล็บปีกกา `{ ... }` ในไฟล์นั้น แล้วกด Save:

```json
    "latex-workshop.latex.tools": [
      {
        "name": "latexmk",
        "command": "latexmk",
        "args": [
          "-pdfxe",
          "-synctex=1",
          "-interaction=nonstopmode",
          "-file-line-error",
          "%DOC%"
        ]
      }
    ],
    "latex-workshop.latex.recipes": [
      {
        "name": "Compile with latexmk (XeLaTeX)",
        "tools": [
          "latexmk"
        ]
      }
    ],
    "latex-workshop.latex.recipe.default": "first"
```

---

## 🚀 3. วิธีการรันดูไฟล์เล่ม (How to Compile)
1. เปิดโฟลเดอร์โปรเจกต์ที่ Clone มาใน VS Code
2. ไปที่แถบเมนูด้านซ้ายสุด คลิกที่ไอคอน **TEX (LaTeX Workshop)**
3. ในหัวข้อ *Build LaTeX project* ให้คลิกที่คำว่า **Compile with latexmk (XeLaTeX)** 4. เมื่อโปรแกรมรันเสร็จ (สังเกตเครื่องหมายติ๊กถูกสีเขียวที่แถบด้านล่าง) ให้กดปุ่มรูปแว่นขยาย **View LaTeX PDF** ที่มุมขวาบนของหน้าจอเพื่อดูเล่ม

---

## 🤝 4. กฎการทำงานร่วมกันด้วย Git (Workflow)
เพื่อป้องกันไฟล์พังและเนื้อหาชนกัน ขอให้ทุกคนในกลุ่มทำตามสเต็ปนี้อย่างเคร่งครัด:

1. **ก่อนเริ่มพิมพ์เนื้อหาทุกครั้ง:** ต้องดึงอัปเดตล่าสุดจากเพื่อนก่อนเสมอ
   ```bash
   git pull origin main
   ```
2. **เมื่อทำงานของตัวเองเสร็จ (ต้องการส่งขึ้น GitHub):**
   ```bash
   git add .
   git commit -m "อัปเดตบทที่... เรื่อง..."
   git push -u origin main
   ```
3. 🚫 **ข้อห้ามเด็ดขาด:** โปรเจกต์นี้ตั้งค่า `.gitignore` ไว้แล้ว **ห้าม** บังคับฝืนเอาไฟล์ขยะที่เกิดจากการ Compile (เช่น ไฟล์นามสกุล `.aux`, `.log`, `.fls`, `.pdf`) ขึ้น GitHub เด็ดขาด เพราะจะทำให้เวลาเพื่อนดึงโค้ดไปแล้วรันไม่ผ่าน