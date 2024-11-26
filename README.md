# Membuat Data Mahasiswa
## Langkah-langkah membuat 
### 1. Membuat database baru dengan entitas Mahasiswa dan Data akun

![image](https://github.com/user-attachments/assets/f9384b8a-1f9e-4b1a-aa19-28d717769da7)

### 2. Beralih ke netbeans, buat project baru dengan nama UASPB0
### 3. Tambahkan Library JDK, PostgreSQL dan JasperReport

![image](https://github.com/user-attachments/assets/daf43fcf-918a-4797-8ef8-9a85f81075f8)

### 4. Buat frame Mahasiswa, login dan register

![image](https://github.com/user-attachments/assets/6f07f2bf-1f0f-4c9b-b9e2-55b8873e9914)



![image](https://github.com/user-attachments/assets/f9384b8a-1f9e-4b1a-aa19-28d717769da7)

### 5. Buat persistence unit
Klik kanan package > New > Entity classes from database
Pilih database connection, kemudian pilih tabel yang dibutuhkan, klik add agar tabel yang dipilih pindah ke kotak selected tables, kemudian klik next hingga finish
Maka, secara otomatis akan terdapat package baru yaitu META-INF dan class baru
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


