# Dashboard KSAS Negeri Selangor

Dashboard interaktif untuk rekod permohonan Kawasan Sensitif Alam Sekitar (KSAS) Negeri Selangor, berasaskan data Excel yang dibekalkan. Paparan tersedia dalam Bahasa Melayu.

## Ciri utama
- Indikator jumlah permohonan dan status keputusan
- Trend tahunan permohonan (2010–2026)
- Pecahan keputusan dan bilangan mengikut PBT
- Penapis tahun, PBT, keputusan dan carian teks
- Jadual permohonan dan eksport CSV mengikut penapis
- Responsive untuk desktop dan telefon; tanpa pelayan/backend atau kebergantungan CDN

## Terbitkan di GitHub Pages
1. Cipta repositori baharu di GitHub (contohnya `dashboard-ksas-selangor`).
2. Muat naik fail `index.html` dan `README.md` di root repositori.
3. Buka **Settings → Pages**.
4. Pada **Build and deployment**, pilih **Deploy from a branch**.
5. Pilih branch `main`, folder `/ (root)`, dan **Save**.
6. Halaman akan tersedia di `https://NAMA-PENGGUNA.github.io/dashboard-ksas-selangor/` setelah GitHub menyelesaikan penerbitan.

## Kemas kini data
1. Simpan fail Excel terkini dengan nama `REKOD PERMOHONAN KSAS 1.xlsx` dalam folder yang sama dengan `build_ksas.py`.
2. Jalankan `python build_ksas.py` (Python 3; tiada pakej tambahan diperlukan).
3. Fail `index.html` dikemaskini dengan data dari Excel. Commit dan push `index.html` ke GitHub.

**Perhatian:** `index.html` mengandungi data rekod termasuk nama pemohon dan tajuk permohonan secara terbuka dalam kod sumber. **Semak dan dapatkan kelulusan pelepasan data sebelum menerbitkan repositori sebagai public/GitHub Pages.** Jangan muat naik fail Excel asal jika ia mengandungi butiran terhad/sulit.

**Catatan kualiti data:** Data dibaca daripada helaian pertama dan rekod yang mempunyai tahun 2000–2099. PBT dikekalkan seperti sumber, tanpa penyatuan singkatan lama. Keputusan kosong dipaparkan sebagai 'BELUM DIREKODKAN'. Dashboard bukan rekod keputusan rasmi terkini melainkan sumber dikemas kini.


## Tema dashboard
Versi ini menggunakan gaya putih/jingga-merah, navigasi sisi kiri dan susun atur panel yang diilhamkan oleh imej rujukan. Rekod sebenar dipaparkan tanpa mereka-reka koordinat lokasi. Untuk membina semula, letakkan `REKOD PERMOHONAN KSAS 1.xlsx` dalam folder dan jalankan `python build_ksas.py`.

## Peta interaktif KSAS
Peta menggunakan Leaflet 1.9.4 dan peta asas OpenStreetMap (memerlukan internet). Paparan pin mewakili **jumlah rekod bagi kod PBT**, pada **koordinat anggaran pusat pentadbiran/kawasan bandar PBT** dan **bukan lokasi sebenar permohonan**. Penapis dashboard mengubah bilangan pin. Rekod tanpa padanan kod PBT tidak dipetakan dan dilaporkan pada keterangan di atas peta. Nama/singkatan lama PBT boleh berkongsi koordinat yang sama, menyebabkan penanda bertindih. Untuk peta tapak yang tepat, perlukan data koordinat latitud/longitud sebenar bagi setiap permohonan.


### Peta sempadan PBT sebenar
Peta Leaflet menggunakan sempadan 12 PBT daripada fail GeoJSON dibekalkan pengguna. Warna poligon menunjukkan jumlah rekod KSAS bagi PBT yang dipadankan; ia tidak menunjukkan lokasi tepat tapak permohonan. Klik kawasan PBT untuk menapis dashboard. `index.html` telah memasukkan data geometri supaya peta boleh berjalan tanpa permintaan rangkaian tambahan selain library Leaflet dan OpenStreetMap. Untuk menjana semula, simpan fail GeoJSON dan Excel dalam folder yang sama dengan `build_ksas.py`.

### Logo PBT pada peta
Peta memaparkan 12 kedudukan logo berdasarkan titik dalaman poligon. 7 logo dirujuk dari Wikimedia Commons; PBT selebihnya memaparkan singkatan sehingga fail PNG rasmi disediakan. Untuk mengisi kesemua logo, tambah `logos/MBSA.png`, `logos/MBPJ.png`, `logos/MBSJ.png`, `logos/MBDK.png`, `logos/MPS.png`, `logos/MPKj.png`, `logos/MPAJ.png`, `logos/MPSp.png`, `logos/MPKL.png`, `logos/MPKS.png`, `logos/MPHS.png`, `logos/MDSB.png`. Pautan Commons memerlukan akses internet.


## Peta topografi Esri dan logo rasmi PBT (kemas kini Oktober 2026)

- Peta asas: Esri **World Topographic Map** (`World_Topo_Map`) melalui ArcGIS REST tiles. Internet diperlukan. Kredit Esri tertera pada peta.
- Sempadan PBT: GeoJSON yang dibekalkan pengguna.
- Penanda menggunakan fail `logos/<KOD_PBT>.png` di GitHub dahulu.
- **MBDK**: pautan PNG dari portal rasmi MBDK ditetapkan sebagai alternatif sekiranya fail tempatan tiada.
- **11 PBT lain**: kekal penanda singkatan **sehingga PNG rasmi resolusi tinggi disahkan/dimuat naik**. Logo Wikimedia/format JPG/GIF/SVG tidak lagi dipaparkan sebagai ganti.
- Rujukan laman logo rasmi yang ditemui: [MBDK](https://www.mbdk.gov.my/ms/muat-turun), [MPAJ](https://www.mpaj.gov.my/ms/mpaj/profil/logo), [MPSp](https://www.mpsepang.gov.my/logo-mpsepang/), [MPKL](https://mpkl.gov.my/mpkl/profil/logo), [MBSJ](https://portal.mbsj.gov.my/en/node/131), [MPKS](https://mpks.gov.my/ms/logo-bendera).

Letakkan PNG rasmi resolusi tinggi dengan nama tepat `MDSB.png`, `MPKS.png`, `MBSJ.png`, `MBPJ.png`, `MPKL.png`, `MPHS.png`, `MPSp.png`, `MPKj.png`, `MPAJ.png`, `MPS.png`, `MBSA.png`, `MBDK.png`. Fail tempatan itu mengatasi semua URL. Untuk ketepatan identiti korporat, gunakan logo yang disahkan oleh setiap majlis.
