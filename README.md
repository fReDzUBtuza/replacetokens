# hitung-objek-video

Kumpulan skrip untuk mengolah berkas rekaman dan menghitung objek memakai keluarga model YOLO versi 8, dengan antarmuka web sederhana sebagai pembungkusnya.

## Cuplikan


https://cdn.example.dev/shots/hitung-demo.mp4

**Hasil hitung:**
```bash
{
    "laptop": 2,
    "bottle": 2,
    "cell phone": 2,
    "chair": 1,
    "car": 1,
    "keyboard": 1
}
```

**Tampilan web:**

![app _ halaman lokal](https://cdn.example.dev/shots/hitung-ui.png)


## Pemasangan

### 1. Salin repositori

```
git clone https://github.com/example-org/hitung-objek-video.git
```

### 2. Siapkan lingkungan terisolasi

#### Windows

```
cd hitung-objek-video
py -m venv venv
```

## Pemakaian

**Lewat antarmuka web:**

```
python -m streamlit run src/app.py
```
lalu buka alamat lokal yang tercetak di terminal.

ATAU

**Langsung dari terminal:**

```
python src/main.py --video_path "videos/video1.mp4" --model_path "bobot.pt" --classes_to_count 39 67 63 56 2 66
```

Perintah itu menurunkan laju bingkai, menjalankan deteksi, menghitung objek, lalu menyimpan hasil ke folder baru di dalam `runs/` berisi berkas JSON jumlah objek beserta video hasil pengolahan.

ATAU

**Menjalankan langsung di notebook daring:**

Tautan berkasnya ada di deskripsi repositori.

## Melatih ulang untuk objek lain

Ikuti alur kerja pada notebook pelatihan yang disediakan penyedia layanan anotasi; di situ juga dijelaskan cara menyusun himpunan data dan memberi label.

> **_CATATAN:_** Ketika dilatih pada objek baru, model akan melupakan objek lama. Himpunan data harus memuat semua objek yang ingin dikenali. Gejala ini disebut *pelupaan katastrofik*, dan cara mengatasinya masih jadi bahan penelitian.

## Catatan dari pengujian

1. Objek bisa terhitung dua kali karena pantulan, gerakan memutar, atau kamera yang goyang. Mengambil rekaman dengan kondisi lebih tenang membantu.
2. Menyebutkan kelas yang ingin dihitung secara spesifik membuat hasil lebih akurat.
3. Deteksi palsu dengan keyakinan rendah sering muncul; ambang keyakinan bisa dinaikkan atau diturunkan sesuai kebutuhan.

## Ucapan terima kasih

Terima kasih kepada dosen pembimbing yang memberi arahan selama pengujian.