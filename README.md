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

![Screenshot (593)](https://github.com/user-attachments/assets/0ace351a-26df-40a5-8dc6-c6dc9d616602)

Maka, secara otomatis akan terdapat package baru yaitu META-INF dan class baru

![image](https://github.com/user-attachments/assets/f6e88665-d94d-47df-8ea5-28edf5b44599)

### 6. Source code untuk button Insert pada frame Mahasiswa

    private void btnInsertActionPerformed(java.awt.event.ActionEvent evt) {                                          
        EntityManagerFactory manfact = Persistence.createEntityManagerFactory("UASPBOPU");
        EntityManager man = manfact.createEntityManager();

        try {
            man.getTransaction().begin();
            Mahasiswa_1 mhs = new Mahasiswa_1();
            mhs.setNama(txtNama.getText());
            mhs.setNim(txtNIM.getText());
            mhs.setAlamat(txtAlamat.getText());
            mhs.setAsalsma(txtSMA.getText());
            mhs.setNamaorangtua(txtOrtu.getText());

            man.persist(mhs);
            man.getTransaction().commit();

            JOptionPane.showMessageDialog(null, "Data berhasil ditambahkan");
            tampil();
        } catch (Exception e) {
            man.getTransaction().rollback();
            JOptionPane.showMessageDialog(null, "Input Data Gagal: " + e.getMessage());
        } finally {
            man.close();
            manfact.close();
        }
    }                                         

### 7. Source code untuk button Update pada frame Mahasiswa

     private void btnUpdateActionPerformed(java.awt.event.ActionEvent evt) {                                          
        EntityManagerFactory manfact = Persistence.createEntityManagerFactory("UASPBOPU");
        EntityManager man = manfact.createEntityManager();

        try {
            man.getTransaction().begin();
            Mahasiswa_1 mhs = man.find(Mahasiswa_1.class, txtNIM.getText());

            if (mhs != null) {
                mhs.setNama(txtNama.getText());
                mhs.setNim(txtNIM.getText());
                mhs.setAlamat(txtAlamat.getText());
                mhs.setAsalsma(txtSMA.getText());
                mhs.setNamaorangtua(txtOrtu.getText());

                man.getTransaction().commit();
                JOptionPane.showMessageDialog(null, "Data berhasil diupdate");
                tampil();
            } else {
                JOptionPane.showMessageDialog(null, "Data tidak ditemukan");
                man.getTransaction().rollback();
            }
        } catch (Exception e) {
            man.getTransaction().rollback();
            JOptionPane.showMessageDialog(null, "Update Data Gagal: " + e.getMessage());
        } finally {
            man.close();
            manfact.close();
        }
    }         
    
### 8. Source code untuk button Delete pada frame Mahasiswa

    private void btnDeleteActionPerformed(java.awt.event.ActionEvent evt) {                                          
        EntityManagerFactory manfact = Persistence.createEntityManagerFactory("UASPBOPU");
        EntityManager man = manfact.createEntityManager();

        try {
            man.getTransaction().begin();
            Mahasiswa_1 mhs = man.find(Mahasiswa_1.class, txtNIM.getText());

            if (mhs != null) {
                man.remove(mhs);
                man.getTransaction().commit();
                JOptionPane.showMessageDialog(null, "Data berhasil dihapus");
                tampil();
            } else {
                JOptionPane.showMessageDialog(null, "Data tidak ditemukan");
                man.getTransaction().rollback();
            }
        } catch (Exception e) {
            man.getTransaction().rollback();
            JOptionPane.showMessageDialog(null, "Data gagal dihapus: " + e.getMessage());
        } finally {
            man.close();
            manfact.close();
        }
    }          
    
### 9. Button Report pada frame Mahasiswa
Klik kanan package > new > Report wizard

![uas6](https://github.com/user-attachments/assets/a3722e83-5399-4bed-b2f1-27681f992142)

Pilih layout

![Screenshot (586)](https://github.com/user-attachments/assets/0c191058-9b40-43eb-9813-5d4ed56ed5e5)

Buat datasource baru, dengan cara klik new, pilih Database JDBC connection, klik next, beri nama UASPBO, pilih driver PostgreSQL, dengan URL nama database yang digunakan untuk project ini, klik save

![Screenshot (588)](https://github.com/user-attachments/assets/d8463f17-d684-466d-a215-535b4cd5d924)

Isi query seperti di bawah, klik next	

![Screenshot (589)](https://github.com/user-attachments/assets/d144acbb-4cd1-47eb-8197-aa6ad05f56ea)

![Screenshot (590)](https://github.com/user-attachments/assets/7c3fcb03-b3d5-40ad-a355-0dd4ff5e8a0f)

Atur fields, klik next, lewati bagian group by, klik next hinga finish

![Screenshot (591)](https://github.com/user-attachments/assets/14e9a1f0-b1b9-4d6f-856c-6109af845359)

Buat desain report sekreatif kita, klik preview untuk mendapatkan file versi .jasper

![image](https://github.com/user-attachments/assets/956cefd4-4417-4ec9-a737-72c430eab680)

### Source code button report

    private void btnReportActionPerformed(java.awt.event.ActionEvent evt) {                                          
        try {
            EntityManagerFactory manfact = Persistence.createEntityManagerFactory("UASPBOPU");
            EntityManager man = manfact.createEntityManager();

            if (man == null) {
                JOptionPane.showMessageDialog(null, "EntityManager gagal dibuat");
                return;
            }

            String query = "SELECT m FROM Mahasiswa_1 m";
            List<Mahasiswa_1> mhs = man.createQuery(query, Mahasiswa_1.class).getResultList();

            if (mhs.isEmpty()) {
                JOptionPane.showMessageDialog(null, "Data tidak ditemukan");
                return;
            }

            Map<String, Object> parameters = new HashMap<>();
            parameters.put("dataList", mhs);

            String ReportPath = "C:\\Users\\USER\\Documents\\NetBeansProjects\\UASPBO\\src\\uaspbo\\report1.jasper";
            JasperReport report = (JasperReport) JRLoader.loadObjectFromFile(ReportPath);

            JasperPrint print = JasperFillManager.fillReport(report, parameters, new JRBeanCollectionDataSource(mhs));

            JasperViewer viewer = new JasperViewer(print, false);
            viewer.setDefaultCloseOperation(DISPOSE_ON_CLOSE);
            viewer.setVisible(true);

            man.close();
            manfact.close();

        } catch (JRException | PersistenceException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Terjadi kesalahan saat mencetak laporan: " + e.getMessage());
        }
    }           

### 10. Source code untuk button Upload pada frame Mahasiswa

    private void btnUploadActionPerformed(java.awt.event.ActionEvent evt) {                                          
        JFileChooser jfc = new JFileChooser(FileSystemView.getFileSystemView().getHomeDirectory());
        int returnValue = jfc.showOpenDialog(null);
        if (returnValue == JFileChooser.APPROVE_OPTION) {
            File filePilihan = jfc.getSelectedFile();
            System.out.println("File yang dipilih: " + filePilihan.getAbsolutePath());
            try (BufferedReader buff = new BufferedReader(new FileReader(filePilihan))) {
                String baris;
                String pemisah = ";";

                EntityManagerFactory manfact = Persistence.createEntityManagerFactory("UASPBOPU");
                EntityManager man = manfact.createEntityManager();

                man.getTransaction().begin();

                while ((baris = buff.readLine()) != null) {
                    String[] mahasiswa = baris.split(pemisah);

                    if (mahasiswa.length == 5) {
                        String nama = mahasiswa[0];
                        String nim = mahasiswa[1];
                        String alamat = mahasiswa[2];
                        String asalsma = mahasiswa[3];
                        String namaorangtua = mahasiswa[4];

                        if (!nama.isEmpty() && !nim.isEmpty() && !alamat.isEmpty() && !asalsma.isEmpty() && !namaorangtua.isEmpty()) {
                            try {
                                Mahasiswa_1 mhs = new Mahasiswa_1();
                                mhs.setNama(nama);
                                mhs.setNim(nim);
                                mhs.setAlamat(alamat);
                                mhs.setAsalsma(asalsma);
                                mhs.setNamaorangtua(namaorangtua);

                                man.persist(mhs);
                            } catch (Exception e) {
                                JOptionPane.showMessageDialog(null, "Data gagal disimpan: " + e.getMessage());
                            }
                        }
                    }
                }

                man.getTransaction().commit();
                JOptionPane.showMessageDialog(null, "Data berhasil ditambahkan");
                man.close();
                manfact.close();

            } catch (FileNotFoundException ex) {
                JOptionPane.showMessageDialog(null, "File tidak ditemukan: " + ex.getMessage());
            } catch (IOException ex) {
                JOptionPane.showMessageDialog(null, "Error Membaca File: " + ex.getMessage());
            }
        }
        tampil();
    }                
    
### 9. Source code untuk button Login pada frame LoginPage

      private void btnLoginActionPerformed(java.awt.event.ActionEvent evt) {                                         
        String username = txtUser.getText();
        String password = new String(pw.getPassword());
        
        EntityManagerFactory manfact = Persistence.createEntityManagerFactory("UASPBOPU");
        EntityManager man = manfact.createEntityManager();

        try {
            man.getTransaction().begin();

            Query query = man.createQuery("SELECT l FROM Dataakun l WHERE l.username = :username");
            query.setParameter("username", username);

            if (!query.getResultList().isEmpty()) {
                Dataakun user = (Dataakun) query.getSingleResult();

                if (password.equals(user.getPassword())) {
                    JOptionPane.showMessageDialog(this, "Login berhasil. Selamat Datang!");

                    new Mahasiswa().setVisible(true);
                    this.dispose();

                    txtUser.setText("");
                    pw.setText("");
                } else {
                    JOptionPane.showMessageDialog(this, "Password salah, Silakan coba lagi!");
                    pw.setText("");
                }
            } else {
                JOptionPane.showMessageDialog(this, "Username tidak ditemukan. Periksa kembali.");
                txtUser.setText("");
                pw.setText("");
            }

            man.getTransaction().commit();
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            man.close();
            manfact.close();
        }
    }                      

### 10. Source code untuk button Register pada frame LoginPage

   private void lblRegistMouseClicked(java.awt.event.MouseEvent evt) {                                       
        Regist akunbaru = new Regist();
        akunbaru.setVisible(true);
        this.dispose();
    }                      
    
### 11. Source code untuk Checkbox Show password pada frame LoginPage

     private void cbPwActionPerformed(java.awt.event.ActionEvent evt) {                                     
        if (cbPw.isSelected()) {
            pw.setEchoChar((char) 0);
        } else {
            pw.setEchoChar('*');
        }
    }     
    
### 12. Source code untuk button Create pada frame Regsist
Syarat membuat password berdasarkan source codenya adalah, harus memiliki minimal 8 karakter, yang mengandung huruf besar, huruf kecil, dan angka 

  
    private void btnCreateActionPerformed(java.awt.event.ActionEvent evt) {                                          
        if (txtUser.getText().equals("") || txtPW.getText().equals("")) {
            JOptionPane.showMessageDialog(null, "Isi username dan password");
        } else {
            String username, pw;
            username = txtUser.getText();
            pw = txtPW.getText();

            if (pw.length() < 8) {
                JOptionPane.showMessageDialog(null, "Password minimal 8 karakter.");
                return;
            }

            if (!pw.matches(".*[A-Z].*")) {
                JOptionPane.showMessageDialog(null, "Password harus mengandung huruf besar.");
                return;
            }
            if (!pw.matches(".*[a-z].*")) {
                JOptionPane.showMessageDialog(null, "Password harus mengandung huruf kecil.");
                return;
            }
            if (!pw.matches(".*\\d.*")) {
                JOptionPane.showMessageDialog(null, "Password harus mengandung angka.");
                return;
            }

            EntityManagerFactory emf = Persistence.createEntityManagerFactory("UASPBOPU");
            EntityManager em = emf.createEntityManager();
            em.getTransaction().begin();

            Dataakun akun = em.find(Dataakun.class, username);
            if (akun != null) {
                JOptionPane.showMessageDialog(null, "Username sudah terdaftar, buat username lain");
                txtUser.requestFocus();
            } else {
                Dataakun account = new Dataakun();
                account.setUsername(username);
                account.setPassword(pw);
                em.persist(account);
                em.getTransaction().commit();

                JOptionPane.showMessageDialog(null, "Akun berhasil dibuat");
                this.dispose();
                LoginPage1 frame = new LoginPage1();
                frame.setVisible(true);
            }
            em.close();
            emf.close();
        }
    }           
    
### 13. Source code untuk Checkbox Show password pada frame LoginPage

      private void cbPwActionPerformed(java.awt.event.ActionEvent evt) {                                     
        if (cbPw.isSelected()) {
            txtPW.setEchoChar((char) 0);
        } else {
            txtPW.setEchoChar('*');
        }
    }       
    


