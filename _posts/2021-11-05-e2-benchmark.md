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

<div class="wp-block-image">
  <figure class="alignleft size-large"><img loading="lazy" width="1024" height="662" src="https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-bencmark1-1024x662.png" alt="" class="wp-image-74" srcset="https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-bencmark1-1024x662.png 1024w, https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-bencmark1-300x194.png 300w, https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-bencmark1-768x496.png 768w, https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-bencmark1.png 1037w" sizes="(max-width: 1024px) 100vw, 1024px" /><figcaption>terlihat tipe cpu yang digunakan, kecepatan enkripsi, kecepatan i/o dan dd serta speedtest</figcaption></figure>
</div>

Berikut ini hasil speedtest ke server lokal di Jakarta, kenceng bet ternyata. 😀<figure class="wp-block-image size-large">

<img loading="lazy" width="764" height="353" src="https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-speedtest.png" alt="" class="wp-image-75" srcset="https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-speedtest.png 764w, https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-speedtest-300x139.png 300w" sizes="(max-width: 764px) 100vw, 764px" /> <figcaption>speedtest ke biznet</figcaption></figure> <figure class="wp-block-image size-large"><img loading="lazy" width="756" height="402" src="https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-speedtest2.png" alt="" class="wp-image-76" srcset="https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-speedtest2.png 756w, https://debsys.web.id/wp-content/uploads/2021/03/gcp-vps-speedtest2-300x160.png 300w" sizes="(max-width: 756px) 100vw, 756px" /><figcaption>speedtest ke cbn</figcaption></figure> 

Hmmm, . . . .

Kesimpulannya, secara hardware VPS ini sudah mumpuni untuk load kerja rendah hingga sedang. Untuk jaringan tidak perlu diragukan, apalagi server berlokasi di Jakarta maka sangat cocok untuk target visitor dari Indonesia.

Okedah, cukup sekian. Nanti kalau ada tambahan benchmark akan saya update tulisannya.

Salam,
