# Penilaian Sumatif Akhir Tahun
## Mapil DevOps XI TJKT 1 - Penilaian Praktek
### SMKN 1 Banyumas - TA. 2024 2025

# README

## Panduan Instalasi dan Konfigurasi

1. **Unduh dan Ekstrak File Paknux**
   - Download file Paknux dari repositorinya.
   - Ekstrak file yang telah diunduh ke folder di drive D.

2. **Buka Visual Studio Code**
   - Buka Visual Studio Code untuk membuat terminal.
   - Klik menu **File** di pojok kiri atas.
   - Pilih **Open Folder** dan pilih folder yang telah diekstrak.

3. **Simpan File**
   - Simpan setiap file dengan menekan `Ctrl + S`.

4. **Buat File `.env`**
   - Buat file baru dengan nama `.env`.

5. **Buat Repository di GitHub**
   - Masuk ke akun GitHub Anda.
   - Buat repository baru dengan mengklik **Create**.

6. **Inisialisasi Git di Visual Studio Code**
   - Buka terminal baru di Visual Studio Code.
   - Jalankan perintah berikut satu per satu:
     ```bash
     git --version
     git config --global user.name "Nama Anda"
     git config --global user.email "email@domain.com"
     git init
     git remote add origin [URL repository GitHub]
     git branch -M main
     git add .
     git commit -m "first commit"
     git push -u origin main
     ```

7. **Login ke AWS Academy**
   - Masuk ke AWS Academy Canvas menggunakan akun yang telah Anda miliki.
   - Di dashboard, klik **AWS Academy Learnebleb**.
   - Klik **Modules** dan pilih **Meluncurkan AWS**.
   - Klik **Start Lab**.

8. **Konfigurasi Database**
   - Pilih **Aurora** dan **RDS**.
   - Jika sudah ada database, Anda tidak perlu membuat yang baru.

9. **Konfigurasi EC2**
   - Masuk ke **EC2** dan pilih **Instances**.
   - Klik **Launch Instances**.
   - Isi **Name and Tags** sesuai keinginan.
   - Pilih **Ubuntu** dan biarkan tipe instance sebagai `t2.micro`.
   - Pilih **Key Pair** yang sesuai (misalnya, `vockey`).
   - Pada pengaturan jaringan, ganti firewall (security group) dengan memilih **Select Existing Security Group** dan pilih **SGServerWeb**.

10. **Isi Advanced Details**
    - Klik **Advanced Details** dan isi bagian **User  Data (Optional)** dengan perintah berikut:
      ```bash
      #!/bin/bash
      echo '#!/bin/bash
      sudo apt update -y
      sudo apt install -y apache2 php php-mysql libapache2-mod-php mysql-client
      sudo rm -rf /var/www/html/{,.}
      sudo git clone [repository GitHub Anda] /var/www/html
      sudo chmod -R 777 /var/www/html
      echo DB_USER=[username RDS] > /var/www/html/.env
      echo DB_PASS=[password RDS] >> /var/www/html/.env
      echo DB_NAME=[nama database] >> /var/www/html/.env
      echo DB_HOST=[endpoint RDS] >> /var/www/html/.env
      sudo apt install -y openssl
      sudo a2enmod ssl
      sudo a2ensite default-ssl.conf
      sudo systemctl reload apache2' > /home/ubuntu/otomatis.sh

      chmod +x /home/ubuntu/otomatis.sh
      ```
    - Gantilah semua placeholder dalam tanda kurung sesuai dengan informasi Anda.

11. **Luncurkan Instance**
    - Klik **Launch Instance**.
    - Setelah berhasil, klik **Instances** dan pilih **Instance ID**.
    - Klik **Connect** dan jalankan perintah berikut:
      ```bash
      ./otomatis.sh
      ```

12. **Akses IP Publik**
    - Salin IP publik dan buka di tab baru.
    - Isi bagian login dengan username dan password Anda.

13. **Isi Data Siswa**
    - Setelah halaman penilaian sumatif akhir tahun muncul, isi bagian input data siswa sesuai dengan data diri masing-masing dan simpan.

Dengan mengikuti langkah-langkah di atas semoga teman teman bisa berhasil manjalankan dan mengatur proyek kalian yaa!!
