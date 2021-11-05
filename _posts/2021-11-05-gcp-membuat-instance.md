---
title: 'GCP Cara Membuat Instance atau Compute Engine'
layout: single
toc: true
---
# Dashboard GCP
Ini adalah kelanjutan dari tulisan sebelumnya, masih mengenai GCP. Setelah berhasil daftar maka kita akan diarahkan ke dashbord GCP. Awal buka dashboard rasanya agak sedikit bingung karena saking banyaknya menu yang ada.

![Dashboard GCP](/images/dashboard-gcp.png)

Untuk membuat instance/VPS, pada menu sebelah kiri arahkan pada opsi Compute Engine > VM Instances.

Selanjutnya klik create.

# Membuat Instance
Pada menu create instance, kita dapat melakukan kustomisasi untuk instance yang akan kita buat. Semakin tinggi spesifikasi yang kita pilih maka semakin mahal juga biaya yang harus kita bayar. Karena kita mendapat free kredit $300 untuk 3 bulan maka usahakan untuk tidak melebihi batasan tersebut.

Sebagai contoh, disini saya membuat instance dengan spesifikasi 2vCPU, 2GB memory dan 10GB SSD persistent disk dikenakan biaya $18.66/bulan. Yang mana apabila ditotal selama 3 bulan : $18.66 x 3 = $55.98  
Masih sangat jauh untuk batasan kredit $300 untuk 3 bulan.

Untuk instance ini saya memilih OS Debian 10 dan menggunakan SSD sebesar 10GB, karena nantinya akan saya jadikan webserver maka pada bagian firewall beri centang pada allow traffic http dan https.

Cek sekali lagi, dari mulai pemilihan cpu, memory, OS, dan disk serta estimasi harga total perbulan. Apabila sudah oke maka klik create.

# Akses Instance
Tunggu beberapa saat maka instance akan dibuat, dan kita akan di bawa ke dashboard VM Instance.
Coba akses instance via SSH, klik konek via ssh untuk login ke instance yang sudah dibuat.

Cukup mudah sebenarnya membuat instance di GCP, tinggal disesuiakan dengan budget saja. Hha . . .
Kalau dirasa instance yang kita buat spesifikasinya masih kurang, tenang saja. Nanti bisa dilakukan scale lagi sesuai kebutuhan.

Udah dulu ya, kapan2 dilanjut lagi coba install LEMP, WordPress, sama SSL Let's Encrypt di instance yang barusan kita buat.

Salam,
