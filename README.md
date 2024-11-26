# Membuat Data Mahasiswa
## Langkah-langkah membuat 
### 1. Membuat database baru dengan entitas Mahasiswa dan Data akun

![image](https://github.com/user-attachments/assets/f9384b8a-1f9e-4b1a-aa19-28d717769da7)

### 2. Beralih ke netbeans, buat project baru dengan nama UASPB0
### 3. Tambahkan Library JDK, PostgreSQL dan JasperReport

![image](https://github.com/user-attachments/assets/daf43fcf-918a-4797-8ef8-9a85f81075f8)

### 4. Buat frame Mahasiswa, login dan register

![image](https://github.com/user-attachments/assets/6f07f2bf-1f0f-4c9b-b9e2-55b8873e9914)

![image](https://github.com/user-attachments/assets/d5c01918-ae7f-4324-81bb-0cdaf47ec020)

![image](https://github.com/user-attachments/assets/2d3e0bb1-a92a-4963-8359-beee4022af3f)

### 5. Buat persistence unit
Klik kanan package > New > Entity classes from database

![uas7](https://github.com/user-attachments/assets/02282d26-b824-47e0-89d8-e9ed4f65b7db)

Pilih database connection, kemudian pilih tabel yang dibutuhkan, klik add agar tabel yang dipilih pindah ke kotak selected tables, kemudian klik next hingga finish

![Screenshot (591)](https://github.com/user-attachments/assets/1bf3d960-8f73-4fc8-bb94-54bf9158c6d9)

![Screenshot (589)](https://github.com/user-attachments/assets/d461299a-dc8b-4436-ab77-848cd53c8156)

![Screenshot (590)](https://github.com/user-attachments/assets/7c3fcb03-b3d5-40ad-a355-0dd4ff5e8a0f)

![Screenshot (591)](https://github.com/user-attachments/assets/14e9a1f0-b1b9-4d6f-856c-6109af845359)

![Screenshot (592)](https://github.com/user-attachments/assets/d1e63db7-5ffe-4dca-8b21-627c837619aa)

![Screenshot (593)](https://github.com/user-attachments/assets/0ace351a-26df-40a5-8dc6-c6dc9d616602)

Maka, secara otomatis akan terdapat package baru yaitu META-INF dan class baru

![image](https://github.com/user-attachments/assets/f6e88665-d94d-47df-8ea5-28edf5b44599)

### 5. Source code untuk button Insert pada frame Mahasiswa
### 6. Source code untuk button Update pada frame Mahasiswa
### 7. Source code untuk button Delete pada frame Mahasiswa
### 8. Button Report pada frame Mahasiswa
Klik kanan package > new > Report wizard
Pilih layout
Buat datasource baru, dengan cara klik new, pilih Database JDBC connection, klik next, beri nama UASPBO, pilih driver PostgreSQL, dengan URL nama database yang digunakan untuk project ini, klik save
Isi query seperti di bawah, klik next	
Atur fields, klik next, lewati bagian group by, klik next hinga finish
Buat desain report sekreatif kita, klik preview untuk mendapatkan file versi .jasper
### 9. Source code untuk button Upload pada frame Mahasiswa
### 9. Source code untuk button Login pada frame LoginPage
### 10. Source code untuk button Register pada frame LoginPage
### 11. Source code untuk Checkbox Show password pada frame LoginPage
### 12. Source code untuk button Create pada frame Regsist
### 13. Source code untuk Checkbox Show password pada frame LoginPage


