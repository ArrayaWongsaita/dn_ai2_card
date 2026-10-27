# นามบัตรออนไลน์

เว็บไซต์พื้นฐาน ใช้ HTML และ CSS เปิดดูได้ทันที ไม่มีขั้นตอน build
ข้อมูลชื่อ อาชีพ อีเมล และเบอร์โทรทั้งหมดเป็นข้อมูลสมมติ

## โครงสร้างไฟล์

```text
basic-git/
├── .git/          # Git repository หลัก
├── .gitignore     # ไฟล์ที่ไม่ต้องนำเข้า Git
├── .nojekyll      # ให้ GitHub Pages เสิร์ฟไฟล์ static โดยตรง
├── index.html     # ข้อมูลและโครงสร้างนามบัตร
├── styles.css     # รูปแบบและสี
└── README.md
```

แก้ไขข้อมูลที่ `index.html` และปรับรูปแบบที่ `styles.css`
เปิด `index.html` ในเบราว์เซอร์เพื่อดูตัวอย่าง
ลิงก์ CSS ใช้ path แบบ relative จึงรองรับ GitHub Pages ที่มีชื่อ repository ต่อท้าย URL

## Deploy ด้วย GitHub Pages

1. สร้าง repository บน GitHub แบบว่าง โดยไม่เพิ่ม README หรือไฟล์เริ่มต้น
2. รันคำสั่งจากโฟลเดอร์ `basic-git` เปลี่ยน `YOUR_USERNAME` และ `YOUR_REPOSITORY` เป็นค่าจริง:

   ```sh
   git add index.html styles.css README.md .gitignore .nojekyll
   git commit -m "Set up business card for GitHub Pages"
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
   git push -u origin main
   ```

3. บน GitHub ไปที่ **Settings → Pages** ของ repository
4. ใน **Build and deployment** ตั้งค่า:
   - **Source:** Deploy from a branch
   - **Branch:** main
   - **Folder:** /(root)
5. กด **Save** แล้วรอให้ deployment เสร็จ ลิงก์เว็บไซต์จะแสดงในหน้า Pages

สำหรับ repository ทั่วไป URL จะมีรูปแบบ `https://YOUR_USERNAME.github.io/YOUR_REPOSITORY/`
หากชื่อ repository เป็น `YOUR_USERNAME.github.io` URL จะเป็น `https://YOUR_USERNAME.github.io/`

เมื่อแก้เว็บครั้งถัดไป ให้ commit และ push ไปที่ `main` เพื่ออัปเดตเว็บ

อ้างอิง: [ตั้งค่า publishing source ของ GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

## สำรองจากโครงสร้างเดิม

Git repository ที่ซ้อนอยู่เดิมและ source ของ Sites ถูกสำรองไว้ที่ `.git/migration-backup/sites-source.tar.gz`
ไฟล์ deployment เดิมอยู่ที่ `.git/migration-backup/sites-deployment.tar.gz`
ข้อมูลสำรองนี้อยู่ภายใน `.git` จึงไม่ถูก commit หรือเผยแพร่ขึ้น GitHub Pages
