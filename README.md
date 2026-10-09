# Bài thực hành: Hàm & GROUP BY nâng cao

## 📋 Thông tin
- **Database:** QuanLySinhVien
- **Công cụ:** MySQL Workbench
- **Số lượng truy vấn:** 3

## 📝 Danh sách các truy vấn

### Truy vấn 1: Môn học có Credit lớn nhất
```sql
SELECT * FROM Subject WHERE Credit = (SELECT MAX(Credit) FROM Subject);
Truy vấn 2: Môn học có điểm thi lớn nhất
sql
SELECT Sub.SubID, Sub.SubName, Sub.Credit, Sub.Status
FROM Subject Sub
WHERE Sub.SubID IN (
    SELECT M.SubID FROM Mark M 
    WHERE M.Mark = (SELECT MAX(Mark) FROM Mark)
);
Truy vấn 3: Sinh viên + Điểm TB, sắp xếp giảm dần
sql
SELECT S.StudentId, S.StudentName, S.Address, AVG(M.Mark) AS 'Điểm trung bình'
FROM Student S 
JOIN Mark M ON S.StudentId = M.StudentId
GROUP BY S.StudentId, S.StudentName, S.Address
ORDER BY AVG(M.Mark) DESC;