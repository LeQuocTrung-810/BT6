# Bài tập 6: Hệ quản trị CSDL
Chủ đề: Câu lệnh Select
Yêu cầu bài tập: 
Cho file sv_tnut.sql (1.6MB)
1. Hãy nêu các bước để import được dữ liệu trong sv_tnut.sql vào sql server của em
2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
6. nhập sql để tìm xem có những sv nào trùng tên với em?
7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.
8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.
9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)

DEADLINE: 23H59:59 NGÀY 25/4/2025

Ghi chú: Giải thích tại sao lại có SQL như vậy.
# Bài làm
## 1. Hãy nêu các bước để import được dữ liệu trong sv_tnut.sql vào sql server của em
- Vào phần File >> Open >> Files >> chọn file sv_tnut.sql đã tải từ thầy trước đó
![image](https://github.com/user-attachments/assets/58b251e5-fa3d-4f3f-8845-36a99ff35013)
![image](https://github.com/user-attachments/assets/c86e60b4-06fe-4af7-a495-13b661eae3cc)
## 2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
- Sau khi chạy file sv_tnut.sql của thày ta được bảng dữ liệu dài 9000 dòng như sau:  
![image](https://github.com/user-attachments/assets/32d6de5e-78c5-46bf-ab03-016354712d5c)
## 3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?  
![image](https://github.com/user-attachments/assets/002085ca-13d7-4834-b294-a9ad6c1349c2)
```
Select * From dbo.SV
Where ns = '2004-10-08'
```
Dùng lệnh select để lấy các trường thuộc tính có trong bảng dbo.SV  
Và sử dụng lệnh Where để tìm những người có cùng ngày tháng năm sinh với em
## 4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?  
![image](https://github.com/user-attachments/assets/fbe591c2-a074-4a3a-8be8-e39a45d7787c)
```
Where Day(ns) = 08 AND Month(ns) = 10;
```
Khác với câu trên câu này em thay đổi việc tìm kiếm đầy đủ ngày tháng năm sinh bằng việc tìm những người có cúng ngày sinh và tháng sinh  
## 5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?  
![image](https://github.com/user-attachments/assets/d3e9958f-cd02-4fb1-bcb4-229687d1e588)
Giống với câu 4, nhưng câu này em chỉ việc tìm kiếm các dữ liệu giống năm sinh thay cho việc tìm kiếm ngày sinh  
## 6. nhập sql để tìm xem có những sv nào trùng tên với em?  
![image](https://github.com/user-attachments/assets/3cae1644-e9ca-497e-bf46-c2092eab27c3)
Thay thế việc tìm kiếm ngày sinh thành tìm kiếm tên 
## 7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.  
![image](https://github.com/user-attachments/assets/533c6bbf-384b-4cfd-ae56-ec2248a93d65)
Thay thế thành tìm họ đệm
## 8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.  
![image](https://github.com/user-attachments/assets/44a9758c-87c9-4dda-a75c-6a44b7bd48f9)
```
Where (
    (Case When SubString(sdt,1,1) <> SubString('0968128503',1,1) Then 1 Else 0 End +
     Case When SubString(sdt,2,1) <> SubString('0968128503',2,1) Then 1 Else 0 End +
     Case When SubString(sdt,3,1) <> SubString('0968128503',3,1) Then 1 Else 0 End +
     Case When SubString(sdt,4,1) <> SubString('0968128503',4,1) Then 1 Else 0 End +
     Case When SubString(sdt,5,1) <> SubString('0968128503',5,1) Then 1 Else 0 End +
     Case When SubString(sdt,6,1) <> SubString('0968128503',6,1) Then 1 Else 0 End +
     Case When SubString(sdt,7,1) <> SubString('0968128503',7,1) Then 1 Else 0 End +
     Case When SubString(sdt,8,1) <> SubString('0968128503',8,1) Then 1 Else 0 End +
     Case When SubString(sdt,9,1) <> SubString('0968128503',9,1) Then 1 Else 0 End +
     Case When SubString(sdt,10,1) <> SubString('0968128503',10,1) Then 1 Else 0 End)
) = 1
```
Sử dụng hàm lệnh Case When SubString để so sánh từng kí tự số trong sdt của em và kiểm tra xem có ai có số điện thoại chỉ khác 1 số (ký tự số)
## 9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
![image](https://github.com/user-attachments/assets/30792c8d-babb-433a-abfd-df85ba53a85d)
``` WHERE lop LIKE '%KTP%' ```
Được dùng để lọc ra các thông tin có chứa ký tự liên quan đến KTP
```
ORDER BY 
    ten COLLATE Vietnamese_CI_AS, 
    hodem COLLATE Vietnamese_CI_AS; 
```
Được dùng để sắp xếp theo tên và họ đệm thay vì sắp xếp theo các trình tự khác và Vietnamese_CI_AS để định dạng kiểu tiếng việt
## 10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)
Câu này là bất khả thi bởi vì trong cơ sở dữ liệu đang thiếu trường giới tính nên không thể truy xuất thông tin về các sv nữ trong ngành KMT. Em có thấy những ý kiến như tìm những người có tên giống với tên nữ giới nhưng như vậy sẽ dẫn đến sai lầm trong quản lý (Ví dụ như bạn Phạm Khắc Linh trong lớp là con trai), nên em không làm do có thể dẫn đến những sai làm lớn hơn. Phần này chỉ khả thi khi có đủ trường dữ liệu trong yêu cầu đề bài.  
## Giải thích tại sao lại có SQL như vậy.  
SQL như này được tạo ra nhằm quản lý thông tin của sinh viên trong trường tuy vậy trong bảng thông tin còn thiếu trường dữ liệu giới tính có thể là một bẫy của thầy để kiểm tra sự nhanh nhạy của chúng em trong việc nhìn ra lỗi sai, thiếu sót trong cơ sở dữ liệu.
