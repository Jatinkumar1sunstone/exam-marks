# Exam Marks Dashboard (Apps Script + Vercel)

Do hi cheezein hain: `apps-script/Code.gs` (Google Sheet ke andar) aur `index.html` (Vercel par).
Login: email + shared password. Campus-wise data server (Apps Script) par hi filter hota hai.

## Part A: Apps Script (ek baar)
1. Wo Google Sheet kholo jisme subject-wise aur cumulative tabs hain.
2. Extensions -> Apps Script.
3. Jo code pehle se likha ho wo hata do, `Code.gs` ka poora content paste karo.
4. Upar `PASSWORD` badlo (sabke liye ek hi password).
5. Save (Ctrl+S).
6. Deploy -> New deployment -> gear icon -> **Web app**.
   - Execute as: **Me**
   - Who has access: **Anyone**
   - Deploy -> Authorize access (Google warning aaye to Advanced -> Go to project).
7. **Web app URL** copy karo.
8. Wo URL browser me kholo: "Exam dashboard API is running" dikhna chahiye.

## Part B: Vercel
1. `index.html` me `API_URL` me wo Web app URL paste karo.
2. `index.html` ko GitHub repo me daalo (private repo).
3. vercel.com -> Add New -> Project -> repo import (Framework: Other) -> Deploy.
4. Vercel URL kholo, email + password se login karo.

## Roz ka kaam
- Sheet me data badlo -> dashboard me **Refresh data** dabao. Kuch deploy nahi karna.
- Naya semester: `index.html` me `PLAN_ALL` badlo, GitHub me push, Vercel khud deploy karega.
- Access badalna (do tareeke):
  - Sheet me **Access** naam ka tab banao, columns: `email`, `role` (admin ya viewer), `campuses` (comma se alag, jaise `SAGE, SAGESELECT`). Turant chalta hai.
  - Ya `Code.gs` me ADMINS / CAMPUS_ACCESS badlo. **Zaroori:** phir Deploy -> Manage deployments -> pencil icon -> Version: **New version** -> Deploy. Bina iske purana code chalta rahega. URL wahi rehta hai.
- Password badalna: `Code.gs` me PASSWORD badlo, upar wala New version step karo.

## Sheet ke column names (wahi rehne chahiye)
- Subject-wise: id, Student_name, campus_name, admission_year, Semester, course_id, course_name, exam_type, obtained_grades_text, max_grades, Marks, cplm_id
- Cumulative: student_id, student_name, campus, batch, semester_label, exam_type, obtained_grades_text, marks_status
- Tab badle ya naya banaya to `Code.gs` me SUBJECT_GID / CUMULATIVE_GID badlo (tab kholne par URL me `gid=` hota hai).
