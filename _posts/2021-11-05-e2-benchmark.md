---
title: 'GCP VPS e2-small Benchmark'
layout: single
toc: true
---
# Alat Benchmark
Jadi tulisan ini adalah hasil benchmark sederhana yang saya lakukan pada VPS e2-small di GCP, untuk spesifikasi detail mengenai VPSnya bisa dibaca pada tulisan sebelumnya.

Untuk melakukan benchmark, saya menggunakan <a rel="noreferrer noopener" href="https://github.com/n-st/nench" target="_blank">nench.sh</a> 

# Parameter Benchmark
Benchmark ini melakukan pengujian dengan hash, kompresi dan enkripsi untuk melihat kemampuan CPU yang digunakan pada VPS tersebut. Kemudian ada test I/O menggunakan ioping dan dd, serta ada pengujian kecepatan jaringan ke beberapa server yang ada.

Nanti akan saya tambahkan juga speedtest ke server lokal, karena VPS ini pada pemilihan lokasi kemarin saya pilih berlokasi di Jakarta.

# Hasil Benchmark
Hasil benchmark menggunakan nench.sh :  
![e2 benchmark](/images/e2-benchmark.png)  
Terlihat tipe cpu yang digunakan, kecepatan enkripsi, kecepatan i/o dan dd serta speedtest.  

Berikut ini hasil speedtest ke server lokal di Jakarta, kenceng bet ternyata.  
![vps speedtest](/images/vps-speedtest.png)  
![vps speedtest 2](/images/vps-speedtest2.png)

# Kesimpulan
Kesimpulannya, secara hardware VPS ini sudah mumpuni untuk load kerja rendah hingga sedang. Untuk jaringan tidak perlu diragukan, apalagi server berlokasi di Jakarta maka sangat cocok untuk target visitor dari Indonesia.

Okedah, cukup sekian. Nanti kalau ada tambahan benchmark akan saya update tulisannya.

Salam,
