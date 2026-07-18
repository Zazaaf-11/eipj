<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Transformasi Digital Kampung Emas Bumijo</title>
  <!-- Menggunakan Font-Awesome untuk Ikon 3D Layered Modern -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    /* Reset & Variabel Tema Utama Terisolasi */
    :root {
      --bg-gradient: linear-gradient(135deg, #FFFFFF 60%, #F0F7FF 100%);
      --color-navy: #0F294A;
      --color-navy-light: #1E3A8A;
      --color-gold: #F59E0B;
      --color-gold-dark: #D97706;
      --color-muted: #64748B;
      --neumorphic-outset: 8px 8px 16px #CBD5E1, -8px -8px 16px #FFFFFF;
      --neumorphic-inset: inset 4px 4px 8px #CBD5E1, inset -4px -4px 8px #FFFFFF;
    }

    * {
      margin: 0; padding: 0; box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #06162C;
      display: flex; justify-content: center; align-items: center;
      min-height: 100vh; overflow: hidden;
    }

    /* Kontainer Utama Slide Presentation - Rasio Emas 16:9 */
    .deck-container {
      width: 100vw; height: 100vh;
      max-width: 1280px; max-height: 720px;
      position: relative; 
      box-shadow: 0 35px 60px -15px rgba(0,0,0,0.7);
      background: #0F294A;
      overflow: hidden;
    }

    /* STRUKTUR SLIDE INDIVIDUAL */
    .slide {
      position: absolute; top: 0; left: 0;
      width: 100%; height: 100%;
      padding: 40px 60px; 
      display: flex; flex-direction: column; justify-content: space-between;
      background: var(--bg-gradient);
      z-index: 1;
      
      /* Animasi Euforia: Smooth Transition & Scale */
      opacity: 0;
      visibility: hidden;
      transform: scale(0.97) translateY(10px);
      transition: opacity 0.5s cubic-bezier(0.25, 1, 0.5, 1), 
                  transform 0.5s cubic-bezier(0.25, 1, 0.5, 1), 
                  visibility 0.5s;
    }

    /* Slide Aktif */
    .slide.active {
      opacity: 1;
      visibility: visible;
      transform: scale(1) translateY(0);
      z-index: 10;
    }

    /* Pola Corak Garis Abstrak Mewah di Setiap Slide */
    .slide::before {
      content: ""; position: absolute; top: -10%; right: -10%;
      width: 350px; height: 350px;
      border: 5px dashed rgba(245, 158, 11, 0.12); border-radius: 50%;
      pointer-events: none; z-index: 0;
    }

    /* Header Judul Utama */
    .slide-header {
      font-size: 28px; font-weight: 800;
      color: var(--color-navy);
      border-left: 8px solid var(--color-gold);
      padding-left: 15px; margin-bottom: 15px;
      text-transform: uppercase; letter-spacing: 0.5px;
      z-index: 2;
    }

    /* Area Konten Utama */
    .slide-content {
      flex: 1; display: grid; gap: 20px;
      align-items: center; z-index: 2;
      overflow: hidden;
    }

    /* Grid Layout Variasi */
    .grid-2 { grid-template-columns: 1fr 1fr; }
    .grid-3 { grid-template-columns: 1fr 1fr 1fr; }
    .grid-full { grid-template-columns: 1fr; }

    /* Kartu Timbul Elegan (Neumorphic Card) */
    .premium-card {
      background: #FFFFFF; border-radius: 16px;
      padding: 24px; box-shadow: var(--neumorphic-outset);
      border: 1px solid rgba(255,255,255,0.7);
      max-height: 420px; overflow-y: auto;
    }

    /* Teks Isi Utama - Ukuran Font Dikecilkan Aman (19px) */
    .text-body {
      font-size: 19px; line-height: 1.6;
      color: var(--color-navy-light); list-style-position: inside;
    }

    .text-body li {
      margin-bottom: 10px;
    }

    .highlight-gold {
      color: var(--color-gold-dark); font-weight: 700;
    }

    /* Desain Blok Kotak Prompt Bahasa Indonesia */
    .prompt-box {
      background: #F8FAFC; border-radius: 12px;
      padding: 20px; box-shadow: var(--neumorphic-inset);
      border-left: 6px solid var(--color-navy);
      font-style: italic; font-size: 18px;
      color: #334155; margin-top: 5px;
      line-height: 1.6;
    }

    /* Elemen Visual Ikon Ganti Gambar 3D */
    .visual-3d-placeholder {
      display: flex; flex-direction: column;
      justify-content: center; align-items: center;
      background: #FFFFFF; border-radius: 20px;
      box-shadow: var(--neumorphic-outset);
      height: 100%; min-height: 280px; padding: 20px;
      text-align: center; border: 2px solid rgba(245, 158, 11, 0.15);
    }

    .visual-3d-placeholder i {
      font-size: 70px; color: var(--color-navy);
      margin-bottom: 15px;
      text-shadow: 3px 3px 0px var(--color-gold);
      animation: pulseIcon 3s infinite ease-in-out;
    }

    @keyframes pulseIcon {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.05); text-shadow: 4px 4px 0px var(--color-gold-dark); }
    }

    .visual-3d-title {
      font-size: 16px; font-weight: 700; color: var(--color-navy);
    }

    /* Footer Informasi Halaman */
    .slide-footer {
      display: flex; justify-content: space-between; align-items: center;
      border-top: 2px solid rgba(15, 41, 74, 0.08); padding-top: 12px;
      margin-top: 10px; z-index: 2;
    }

    .slide-footer-text {
      font-size: 14px; color: var(--color-muted); font-weight: 500;
    }

    .slide-footer-page {
      font-size: 15px; font-weight: 800;
      color: var(--color-navy); background: #FFFFFF;
      padding: 3px 10px; border-radius: 6px;
      box-shadow: 2px 2px 6px rgba(0,0,0,0.05);
    }

    /* Tombol Navigasi Pengendali Presentasi */
    .nav-controls {
      position: absolute; bottom: 42px; right: 140px;
      display: flex; gap: 12px; z-index: 100;
    }

    .nav-btn {
      background: #FFFFFF; border: none;
      width: 42px; height: 42px; border-radius: 50%;
      color: var(--color-navy); font-size: 16px; cursor: pointer;
      display: flex; justify-content: center; align-items: center;
      box-shadow: 3px 3px 8px #CBD5E1, -3px -3px 8px #FFFFFF;
      transition: all 0.2s ease;
    }

    .nav-btn:hover {
      transform: scale(1.1); background: var(--color-gold); color: white;
    }

    /* Gaya Spesifik Halaman Depan / Cover */
    .cover-slide {
      justify-content: center; align-items: center;
      text-align: center; background: linear-gradient(135deg, #0F294A 0%, #06162C 100%);
    }

    .cover-slide::before { display: none; }

    .cover-badge {
      background: var(--color-gold); color: #FFFFFF;
      padding: 8px 20px; border-radius: 25px;
      font-weight: 700; font-size: 16px; margin-bottom: 20px;
      letter-spacing: 1px; box-shadow: 0 8px 16px rgba(245,158,11,0.25);
    }

    .cover-title {
      font-size: 34px; font-weight: 900; color: #FFFFFF;
      line-height: 1.3; max-width: 1100px; margin-bottom: 25px;
      text-shadow: 0 4px 10px rgba(0,0,0,0.3);
    }
    
    .cover-subtitle {
      font-size: 22px; font-weight: 600; color: #cbd5e1;
      max-width: 1000px; margin-bottom: 35px; line-height: 1.4;
    }

    .cover-meta-box {
      display: flex; gap: 25px; margin-top: 5px;
    }

    .meta-item {
      background: rgba(255, 255, 255, 0.06); padding: 12px 30px;
      border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);
      font-size: 18px; font-weight: 700; color: #FFFFFF;
      backdrop-filter: blur(8px);
    }
    
    .meta-item i { color: var(--color-gold); margin-right: 10px; }
    .text-center { text-align: center; }

    /* GAYA BARU: MOCKUP INTERFACE REALISTIS SPORTRAGA (SLIDE 30) */
    .sportraga-slide {
      background: #f8fafc !important;
      padding: 30px 50px !important;
    }
    
    .browser-window {
      background: #ffffff; border-radius: 14px;
      box-shadow: 0 20px 40px rgba(15, 41, 74, 0.15);
      border: 1px solid #e2e8f0; width: 100%; height: 450px;
      display: flex; flex-direction: column; overflow: hidden;
    }
    
    .browser-header {
      background: #f1f5f9; padding: 10px 20px;
      display: flex; align-items: center; gap: 15px;
      border-bottom: 1px solid #e2e8f0;
    }
    
    .window-dots { display: flex; gap: 6px; }
    .w-dot { width: 12px; height: 12px; border-radius: 50%; }
    .wd-red { background: #ef4444; }
    .wd-amb { background: #f59e0b; }
    .wd-grn { background: #10b981; }
    
    .browser-url-bar {
      background: #ffffff; border: 1px solid #cbd5e1;
      border-radius: 6px; flex: 1; padding: 4px 15px;
      font-size: 13px; color: #64748b; display: flex; align-items: center; gap: 8px;
    }
    
    .ai-badge-top {
      background: #0284c7; color: #fff; font-size: 11px; font-weight: 700;
      padding: 4px 10px; border-radius: 4px; display: flex; align-items: center; gap: 4px;
    }

    .app-layout { display: flex; flex: 1; overflow: hidden; }
    .app-sidebar { width: 220px; background: #0f172a; color: #fff; padding: 20px; display: flex; flex-direction: column; gap: 8px; }
    .side-item { padding: 10px 12px; border-radius: 8px; font-size: 13px; font-weight: 600; color: #94a3b8; display: flex; align-items: center; gap: 10px; cursor: pointer; }
    .side-item.active { background: #0284c7; color: #fff; }
    
    .app-main-content { flex: 1; padding: 20px; display: flex; flex-direction: column; gap: 15px; overflow-y: auto; background: #f8fafc; }
    .app-content-header { display: flex; justify-content: space-between; align-items: center; }
    .app-title { font-size: 18px; font-weight: 800; color: #0f172a; }
    
    .venue-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
    .venue-card { background: #ffffff; border: 1px solid #e2e8f0; border-radius: 12px; overflow: hidden; display: flex; flex-direction: column; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05); }
    .card-img-placeholder { height: 100px; background: linear-gradient(135deg, #059669 0%, #047857 100%); position: relative; padding: 12px; display: flex; align-items: flex-end; }
    .card-img-placeholder.badminton { background: linear-gradient(135deg, #3b82f6 0%, #1d4ed8 100%); }
    .venue-tag { background: rgba(255,255,255,0.2); color: #fff; backdrop-filter: blur(4px); font-size: 11px; font-weight: 700; padding: 3px 8px; border-radius: 4px; }
    
    .card-body { padding: 12px; display: flex; flex-direction: column; gap: 6px; }
    .v-name { font-size: 14px; font-weight: 700; color: #1e293b; }
    .v-loc { font-size: 12px; color: #64748b; display: flex; align-items: center; gap: 4px; }
    .v-meta { display: flex; justify-content: space-between; align-items: center; margin-top: 4px; border-top: 1px dashed #e2e8f0; padding-top: 8px; }
    .v-price { font-size: 13px; font-weight: 800; color: #0f172a; }
    .v-rating { font-size: 12px; color: #f59e0b; font-weight: 600; }
    .v-btn { background: #0f172a; color: #fff; border: none; padding: 6px 12px; border-radius: 6px; font-size: 11px; font-weight: 700; cursor: pointer; }
    
    .ai-sticky-note { background: #f0fdf4; border: 1px solid #bbf7d0; border-left: 4px solid #22c55e; padding: 10px 15px; border-radius: 6px; font-size: 12px; color: #166534; line-height: 1.5; }
  </style>
</head>
<body>

  <div class="deck-container">
    
    <!-- SLIDE 1: HALAMAN DEPAN (COVER) -->
    <div class="slide active cover-slide">
      <div class="cover-badge">PELATIHAN DIGITAL MARKETING BERBASIS AI</div>
      <h1 class="cover-title">Transformasi Strategi Pemasaran dengan<br>Digital Marketing Berbasis AI</h1>
      <p class="cover-subtitle">Akselerasi Usaha Kreatif dan Kemandirian Ekonomi Kampung Emas Bumijo Yogyakarta</p>
      <div class="cover-meta-box">
        <div class="meta-item"><i class="fa-solid fa-calendar-days"></i> Sabtu, 18 Juli 2026</div>
        <div class="meta-item"><i class="fa-solid fa-user-tie"></i> Zaza Afnindar Fakhrurozi</div>
      </div>
      <div class="slide-footer-page" style="position:absolute; bottom:40px; right:60px; background: rgba(255,255,255,0.2); color: white;">1 dari 31</div>
    </div>

    <!-- SLIDE 2: PERBAIKAN PONDASI UTAMA - SINERGI KONSEP 4K -->
    <div class="slide">
      <div class="slide-header">Landasan Strategis: Sinergi Konsep 4K</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li>👑 <span class="highlight-gold">Kraton:</span> Penjaga akar budaya, nilai etika luhur, dan keaslian filosofi produk lokal Yogyakarta.</li>
            <li>🎓 <span class="highlight-gold">Kampus:</span> Motor inovasi teknologi modern, pusat pelatihan AI, dan pendampingan UMKM berkala.</li>
            <li>🏡 <span class="highlight-gold">Kampung:</span> Basis utama produksi usaha warga sekaligus penggerak roda ekonomi lokal.</li>
            <li>🏢 <span class="highlight-gold">Kantor:</span> Jaringan kemitraan dinas pemerintahan resmi serta akses pasar komersial industri.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-circle-nodes"></i>
          <div class="visual-3d-title">Diagram Interaksi Ekosistem 4K untuk Kolaborasi</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Kolaborasi Strategis Unsur Yogyakarta</span>
        <span class="slide-footer-page">2 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 3: STUDI KASUS & DATA RIIL DIY -->
    <div class="slide">
      <div class="slide-header">Studi Kasus Keberhasilan Desa Wisata DIY</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li><span class="highlight-gold">Peningkatan Kunjungan:</span> Data menunjukkan kunjungan wisatawan naik hingga <span class="highlight-gold">45%</span> berkat adaptasi media sosial secara konsisten.</li>
            <li><span class="highlight-gold">Omzet UMKM Naik:</span> Rata-rata pendapatan naik hingga <span class="highlight-gold">2,5 kali lipat</span> via promosi digital terpadu.</li>
            <li>*Belajar dari kisah sukses Desa Nglanggeran & Pentingsari dalam membangun nama merek di internet.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-chart-line"></i>
          <div class="visual-3d-title">Grafik Pertumbuhan Pendapatan Digital</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Analisis Kredibilitas Data Teruji</span>
        <span class="slide-footer-page">3 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 4: PROFIL & POTENSI KAMPUNG EMAS BUMIJO -->
    <div class="slide">
      <div class="slide-header">Profil & Potensi Kampung Emas Bumijo</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li><span class="highlight-gold">Aset Budaya & Tradisi:</span> Memiliki nilai luhur warisan lokal yang kental dan asri untuk menarik wisatawan.</li>
            <li><span class="highlight-gold">Sektor UMKM Kuliner:</span> Ragam olahan pangan kuliner tradisional otentik dengan potensi pasar yang besar.</li>
            <li><span class="highlight-gold">Sentra Kerajinan Tangan:</span> Karya seni kerajinan lokal unik yang bernilai ekonomi tinggi jika dikemas dengan modern.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-store"></i>
          <div class="visual-3d-title">Visualisasi Tiga Sektor Potensi Desa</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Kampung Emas Bumijo - Identifikasi Aset Usaha Warga</span>
        <span class="slide-footer-page">4 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 5: TANTANGAN PEMASARAN UMKM -->
    <div class="slide">
      <div class="slide-header">Tantangan Pemasaran UMKM Bumijo</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li><span class="highlight-gold">Jangkauan Terbatas:</span> Penjualan produk mayoritas masih mengandalkan area pasar lokal sekitar kampung.</li>
            <li><span class="highlight-gold">Masalah Konsistensi:</span> Kesulitan membuat ide konten jualan setiap hari karena waktu yang terbatas.</li>
            <li><span class="highlight-gold">Kendala Modal Pajang:</span> Terbatasnya biaya modal untuk membayar agen iklan profesional yang mahal.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-triangle-exclamation"></i>
          <div class="visual-3d-title">Analisis Titik Hambat Usaha Warga</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Identifikasi Hambatan Lapangan</span>
        <span class="slide-footer-page">5 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 6: SOLUSI MASA DEPAN: AI & DIGITAL MARKETING -->
    <div class="slide">
      <div class="slide-header">Solusi Masa Depan: Mengapa AI & Digital?</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li><span class="highlight-gold">Akses Pasar Tanpa Batas:</span> Membuka pintu gerbang promosi global agar produk Bumijo dikenal ke luar kota secara instan.</li>
            <li><span class="highlight-gold">Efisiensi Tanpa Modal:</span> Menggunakan teknologi kecerdasan buatan gratis sebagai asisten kreatif jualan pribadi warga tanpa tambahan biaya operasional.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-rocket"></i>
          <div class="visual-3d-title">Jembatan Lompatan Menuju Pasar Modern</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Strategi Efisiensi Optimal</span>
        <span class="slide-footer-page">6 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 7: APA ITU AI DALAM KONTEKS BISNIS -->
    <div class="slide">
      <div class="slide-header">Apa Itu AI dalam Konteks Bisnis?</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <p class="text-body">
            <span class="highlight-gold">Artificial Intelligence (AI)</span> bukanlah pengganti pekerjaan manusia, melainkan sebuah <span class="highlight-gold">Asisten Super Gratis</span> di HP Anda yang membantu para pelaku UMKM bekerja dengan jauh lebih cepat, cerdas, kreatif, dan efisien untuk memajukan kampung.
          </p>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-lightbulb"></i>
          <div class="visual-3d-title">AI Sebagai Sumber Inspirasi Instan</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Pemahaman Dasar Teknologi Ramah Pemula</span>
        <span class="slide-footer-page">7 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 8: TRADISIONAL VS AI DIGITAL -->
    <div class="slide">
      <div class="slide-header">Transformasi Promosi Tradisional VS AI Digital</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li><span class="highlight-gold">Promosi Gaya Lama:</span> Cetak brosur kertas secara manual, disebar terbatas, membutuhkan waktu lama dan biaya cetak mahal.</li>
            <li><span class="highlight-gold">Promosi Era AI Digital:</span> Mengetik instruksi di HP, materi teks promosi langsung jadi dalam hitungan 5 detik dan siap sebar luas ke ribuan calon pembeli.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-arrows-left-right-to-line"></i>
          <div class="visual-3d-title">Perbandingan Efisiensi Kerja Nyata</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Komparasi Metode Kerja Kerja Pintar</span>
        <span class="slide-footer-page">8 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 9: 3 PILAR UTAMA PEMASARAN CERDAS -->
    <div class="slide">
      <div class="slide-header">3 Pilar Utama Pemasaran Cerdas Berbasis AI</div>
      <div class="slide-content grid-3">
        <div class="premium-card text-center">
          <h3 class="highlight-gold" style="font-size:22px;margin-bottom:10px;"><i class="fa-solid fa-pen-nib"></i> Copywriting</h3>
          <p class="text-body" style="font-size:16px;">Menyusun teks jualan caption media sosial yang menarik dan meyakinkan.</p>
        </div>
        <div class="premium-card text-center">
          <h3 class="highlight-gold" style="font-size:22px;margin-bottom:10px;"><i class="fa-solid fa-palette"></i> Tata Visual</h3>
          <p class="text-body" style="font-size:16px;">Merancang konsep logo kemasan dan panduan tata foto produk estetik.</p>
        </div>
        <div class="premium-card text-center">
          <h3 class="highlight-gold" style="font-size:22px;margin-bottom:10px;"><i class="fa-solid fa-comments"></i> Pelayanan</h3>
          <p class="text-body" style="font-size:16px;">Menyiapkan template pesan balasan otomatis pelanggan di WhatsApp.</p>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Tiga Komponen Pondasi UMKM Naik Kelas</span>
        <span class="slide-footer-page">9 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 10: PSIKOLOGI KONSUMEN & STORYTELLING -->
    <div class="slide">
      <div class="slide-header">Psikologi Konsumen & Cerita Lokal</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <p class="text-body">
            Pembeli modern tidak hanya sekadar membeli barang jualan, melainkan membeli <span class="highlight-gold">cerita budaya di balik produk tersebut</span>. AI membantu menggali nilai sejarah Kampung Emas Bumijo menjadi untaian kalimat penulisan cerita iklan (*storytelling*) yang menyentuh hati pembeli.
          </p>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-heart"></i>
          <div class="visual-3d-title">Membangun Ikatan Emosi dengan Pembeli</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Strategi Sentuhan Rasa Seni Jualan</span>
        <span class="slide-footer-page">10 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 11: MENENTUKAN "BUYER PERSONA" -->
    <div class="slide">
      <div class="slide-header">Menentukan Target Pembeli Potensial</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li>👪 <span class="highlight-gold">Wisatawan Keluarga:</span> Kelompok yang memburu wisata ketenangan edukasi budaya asli.</li>
            <li>🎓 <span class="highlight-gold">Generasi Muda Kreatif:</span> Anak muda kampus yang gemar mencari spot tempat kumpul estetik.</li>
            <li>🍲 <span class="highlight-gold">Pecinta Kuliner Sehat:</span> Pengunjung penikmat citarasa sajian hidangan tradisional otentik.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-bullseye"></i>
          <div class="visual-3d-title">Peta Bidik Target Konsumen Bumijo</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Segmentasi Pasar Tepat Sasaran</span>
        <span class="slide-footer-page">11 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 12: CHATGPT VS GEMINI AI -->
    <div class="slide">
      <div class="slide-header">Mengenal Alat Bantu: ChatGPT VS Gemini AI</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li><span class="highlight-gold">ChatGPT (OpenAI):</span> Sangat hebat dalam menstrukturkan rencana strategi bisnis baru dan mengolah tata kalimat copywriting yang rapi teratur.</li>
            <li><span class="highlight-gold">Gemini AI (Google):</span> Sangat cerdas dalam membaca situasi tren pasar terbaru karena terkoneksi langsung secara langsung dengan mesin pencarian Google Indonesia.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-robot"></i>
          <div class="visual-3d-title">Dua Mesin Asisten Pintar Gratis di HP Anda</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Pilihan Piranti Lunak Pendukung</span>
        <span class="slide-footer-page">12 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 13: MODEL EKOSISTEM PLATFORM TERPADU -->
    <div class="slide">
      <div class="slide-header">Model Ekosistem Platform Digital Terpadu</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li><span class="highlight-gold">Katalog Terintegrated:</span> Menyatukan seluruh etalase kuliner dan kerajinan tangan warga ke dalam satu sistem interface rapi yang mudah dibuka kapan saja.</li>
            <li><span class="highlight-gold">Akses Kontak Terdekat:</span> Memudahkan calon pembeli luar daerah terhubung langsung dengan pengelola via WhatsApp tanpa hambatan pihak ketiga.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-cubes"></i>
          <div class="visual-3d-title">Simulasi Integrasi Portal Produk UMKM Desa</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Infrastruktur Digitalisasi Komunitas</span>
        <span class="slide-footer-page">13 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 14: BEDAH INSPIRASI PLATFORM SPORTRAGA BUATAN AI -->
    <div class="slide">
      <div class="slide-header">Inspirasi Output: Platform Sportraga Buatan AI</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li>🌐 <span class="highlight-gold">Bukti Nyata Kekuatan AI:</span> Platform <span class="highlight-gold">sportraga.lovable.app</span> adalah bukti konkrit prototype yang **dibuat penuh menggunakan bantuan AI** (Kecerdasan Buatan) tanpa coding manual yang rumit.</li>
            <li>📱 <span class="highlight-gold">Sistem Informasi Instan:</span> Dengan instruksi prompt AI yang tepat, web aplikasi ini bisa menyatukan jadwal, sarana olahraga, dan komunitas dalam sekejap.</li>
            <li>💡 Model digital berbasis AI inilah yang diadopsi untuk menyatukan & mempromosikan potensi besar Kampung Emas Bumijo.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-wand-magic-sparkles" style="color: #0284c7;"></i>
          <div class="visual-3d-title">Sistem Aplikasi Komunitas Hasil Karya Kecerdasan AI</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Adaptasi Studi Kasus Hasil Output Berbasis AI</span>
        <span class="slide-footer-page">14 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 15: DATA ANALITIK UNTUK EVALUASI -->
    <div class="slide">
      <div class="slide-header">Data Analitik: Membaca Keinginan Pasar</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li>📊 Melihat jenis kiriman promosi apa yang terbukti mengundang banyak klik suka dari netizen.</li>
            <li>⏰ Memantau jam aktif harian para calon pembeli saat membuka ponsel cerdas.</li>
            <li>📍 Mendeteksi asal wilayah kota para pengunjung akun bisnis Kampung Emas Bumijo.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-pie-chart"></i>
          <div class="visual-3d-title">Tampilan Data Evaluasi Konten Berkala</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Mengambil Keputusan Berbasis Fakta Data</span>
        <span class="slide-footer-page">15 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 16: PERSIAPAN PRAKTIK MANDIRI -->
    <div class="slide">
      <div class="slide-header">🛑 Sesi Praktik: Siapkan HP Anda Masing-Masing!</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ol class="text-body">
            <li>Keluarkan Smartphone/HP kesayangan Banyak Ibu saat ini.</li>
            <li>Pastikan koneksi internet Anda aktif berjalan lancar.</li>
            <li>Buka browser internet Google Chrome, lalu buka situs: <span class="highlight-gold">gemini.google.com</span> ATAU <span class="highlight-gold">chatgpt.com</span>.</li>
          </ol>
        </div>
        <div class="visual-3d-placeholder" style="border-color: var(--color-gold);">
          <i class="fa-solid fa-mobile-screen-button" style="color:var(--color-gold-dark);"></i>
          <div class="visual-3d-title" style="font-size:20px;">KITA MEMULAI PRAKTIK LANGSUNG SEKARANG!</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Panduan Praktik Interaktif Mandiri Warga</span>
        <span class="slide-footer-page">16 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 17: PRAKTIK TEKS 1 -->
    <div class="slide">
      <div class="slide-header">🛠️ Praktik Teks 1: Merancang Ide Konten Sebulan</div>
      <div class="slide-content grid-full">
        <div class="premium-card">
          <p class="text-body"><span class="highlight-gold">Langkah:</span> Salin kalimat perintah di bawah ini secara utuh, isi bagian dalam tanda kurung kotak sesuai jenis usaha asli Anda, lalu kirimkan ke Gemini AI atau ChatGPT.</p>
          <div class="prompt-box">
            "Saya adalah pengelola usaha kuliner tradisional [Sebutkan Nama Produk Anda] di Kampung Emas Bumijo Yogyakarta. Tolong buatkan jadwal rancangan ide konten promosi kreatif selama 4 minggu ke depan untuk Instagram. Gunakan bahasa Indonesia yang ramah, sopan, bersahabat, serta selipkan unsur kearifan lokal kebudayaan Yogyakarta agar menarik minat wisatawan."
          </div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Sesi Praktik Teks - Pembuatan Kalender Konten</span>
        <span class="slide-footer-page">17 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 18: PRAKTIK TEKS 2 -->
    <div class="slide">
      <div class="slide-header">🛠️ Praktik Teks 2: Menulis Caption Jualan</div>
      <div class="slide-content grid-full">
        <div class="premium-card">
          <p class="text-body"><span class="highlight-gold">Langkah:</span> Lanjutkan perintah obrolan sebelumnya untuk menghasilkan naskah tulisan iklan caption media sosial yang siap pakai.</p>
          <div class="prompt-box">
            "Dari draf rencana minggu pertama tadi, tolong buatkan satu kalimat teks caption promosi jualan yang memikat untuk produk saya tersebut. Gunakan gaya penulisan santai yang persuasif, berikan kalimat ajakan memesan yang jelas di akhir paragraf, serta lengkapi dengan 5 hashtag terpopuler bahasa Indonesia yang relevan."
          </div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Sesi Praktik Teks - Copywriting Iklan WhatsApp & Media Sosial</span>
        <span class="slide-footer-page">18 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 19: PRAKTIK DESAIN 1 -->
    <div class="slide">
      <div class="slide-header">🛠️ Praktik Desain 1: Merancang Konsep Logo Merek</div>
      <div class="slide-content grid-full">
        <div class="premium-card">
          <p class="text-body"><span class="highlight-gold">Langkah:</span> Gunakan perintah khusus bahasa Indonesia berikut untuk memunculkan ide rancangan gambar logo usaha berstandar mahal.</p>
          <div class="prompt-box">
            "Saya ingin membuat sebuah logo identitas merek baru untuk produk kerajinan/makanan khas Kampung Emas Bumijo bernama Merek [Tulis Nama Toko Anda]. Tolong berikan ide panduan konsep filosofi visual logo yang menggabungkan simbol kemewahan warna emas, warisan kebudayaan Kraton, namun dikemas dengan model garis minimalis yang disukai oleh anak muda modern."
          </div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Sesi Praktik Desain - Panduan Pembuatan Filosofi Logo</span>
        <span class="slide-footer-page">19 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 20: PRAKTIK DESAIN 2 -->
    <div class="slide">
      <div class="slide-header">🛠️ Praktik Desain 2: Aturan Foto Produk Bergaya 3D HD</div>
      <div class="slide-content grid-full">
        <div class="premium-card">
          <p class="text-body"><span class="highlight-gold">Langkah:</span> Minta instruksi teknis kepada AI untuk mengubah hasil jepretan kamera ponsel biasa menjadi terlihat seperti jepretan studio profesional.</p>
          <div class="prompt-box">
            "Tolong berikan saya panduan lengkap tips praktis menata posisi latar belakang foto kemasan produk [Nama Produk Anda] agar terlihat sangat jernih, estetik, and berkualitas tajam layaknya hasil render 3D HD. Perlengkapan hiasan murah apa saja yang perlu ditaruh di atas meja kayu, dan bagaimana cara mengatur arah masuk cahaya matahari agar bayangan produk terlihat sangat rapi?"
          </div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Sesi Praktik Desain - Arahan Estetika Fotografi Produk</span>
        <span class="slide-footer-page">20 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 21: PRAKTIK PROMOSI 1 -->
    <div class="slide">
      <div class="slide-header">🛠️ Praktik Promosi 1: Naskah Video Pendek Tiktok/Reels</div>
      <div class="slide-content grid-full">
        <div class="premium-card">
          <p class="text-body"><span class="highlight-gold">Langkah:</span> Buat naskah rangkaian video berdurasi pendek yang menghibur untuk memicu ketertarikan penonton generasi muda internet.</p>
          <div class="prompt-box">
            "Buatkan saya naskah skrip tulisan video pendek promosi untuk media sosial Tiktok berdurasi total 30 detik. Tema videonya adalah memperlihatkan keseruan berbelanja kuliner khas sore hari di Kampung Emas Bumijo. Rincikan instruksi gerakan visual kamera apa saja yang wajib direkam dari detik 1 sampai 30, beserta teks teks suara narasi pembicaraan yang harus diucapkan."
          </div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Sesi Praktik Promosi - Skrip Konten Video Kreatif</span>
        <span class="slide-footer-page">21 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 22: PRAKTIK PROMOSI 2 -->
    <div class="slide">
      <div class="slide-header">🛠️ Praktik Promosi 2: Menyusun Isi Kalimat Flyer</div>
      <div class="slide-content grid-full">
        <div class="premium-card">
          <p class="text-body"><span class="highlight-gold">Langkah:</span> Rumuskan rangkaian informasi teks selebaran digital padat ringkas untuk dibagikan masif ke grup obrolan WhatsApp.</p>
          <div class="prompt-box">
            "Tolong buatkan susunan draf kalimat informasi singkat untuk materi brosur selebaran digital acara pasar kuliner malam minggu di Kampung Emas Bumijo. Berikan ide judul acara yang heboh menarik perhatian, susun daftar poin keuntungan mengapa pengunjung wajib datang, serta tuliskan ruang kosong penempatan informasi tanggal, waktu, dan peta lokasi acara secara ringkas."
          </div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Sesi Praktik Promosi - Layout Pesan Pamflet Digital</span>
        <span class="slide-footer-page">22 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 23: PRAKTIK PELAYANAN 1 -->
    <div class="slide">
      <div class="slide-header">🛠️ Praktik Pelayanan 1: Balasan Otomatis WhatsApp</div>
      <div class="slide-content grid-full">
        <div class="premium-card">
          <p class="text-body"><span class="highlight-gold">Langkah:</span> Siapkan teks salam sapaan otomatis agar setiap chat calon pembeli masuk bisa langsung ditangani tanpa penundaan waktu.</p>
          <div class="prompt-box">
            "Buatkan saya draf template teks balasan sambutan chat otomatis WhatsApp Business yang ramah, sopan, dan hangat untuk menyambut calon pelanggan baru yang ingin bertanya mengenai harga paket oleh-oleh Kampung Emas Bumijo. Sertakan penggunaan emoji yang manis serta berikan format pengisian alamat pengiriman yang rapi."
          </div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Sesi Praktik Pelayanan - Otomatisasi Operasional Chat Bisnis</span>
        <span class="slide-footer-page">23 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 24: PRAKTIK PELAYANAN 2 -->
    <div class="slide">
      <div class="slide-header">🛠️ Praktik Pelayanan 2: Menangani Komplain Pembeli</div>
      <div class="slide-content grid-full">
        <div class="premium-card">
          <p class="text-body"><span class="highlight-gold">Langkah:</span> Redam situasi kemarahan keluhan pembeli secara elegan menggunakan susunan tata bahasa diplomatis bantuan kecerdasan buatan.</p>
          <div class="prompt-box">
            "Ada seorang pembeli produk kuliner saya yang melayangkan komplain marah karena kiriman paketnya datang terlambat dan kotak pembungkusnya sedikit robek. Tolong buatkan pesan balasan permohonan maaf resmi dalam bahasa Indonesia yang tulus, terdengar bertanggung jawab atas nama manajemen UMKM Bumijo, serta tawarkan opsi kompensasi gratis demi menjaga kesetiaan pembeli tersebut."
          </div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Sesi Praktik Pelayanan - Manajemen Krisis Nama Baik Toko</span>
        <span class="slide-footer-page">24 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 25: PRAKTIK EVALUASI: ANALISIS KOMPETITOR -->
    <div class="slide">
      <div class="slide-header">🛠️ Praktik Evaluasi: Mengamati Taktik Kompetitor</div>
      <div class="slide-content grid-full">
        <div class="premium-card">
          <p class="text-body"><span class="highlight-gold">Langkah:</span> Gunakan cara pandang cerdas untuk meniru poin kesuksesan dari akun pariwisata wilayah daerah lain secara legal dan bijak.</p>
          <div class="prompt-box">
            "Bagaimana cara mudah bagi masyarakat awam untuk menganalisis taktik promosi digital dari akun kompetitor desa wisata lain di luar daerah yang sudah memiliki ribuan pengikut sukses? Berikan saya langkah langkah praktis indikator apa saja yang harus kami amati, pelajari, dan modifikasi untuk diaplikasikan ke ekosistem Kampung Emas Bumijo."
          </div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Sesi Praktik Evaluasi - Taktik Pemetaan Strategi Kompetitif</span>
        <span class="slide-footer-page">25 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 26: PAMERAN KARYA KILAT (SHOWCASE) -->
    <div class="slide">
      <div class="slide-header">👥 Sesi Showcase: Pamerkan Hasil Tulisan Anda!</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li>Tunjukkan hasil balasan teks dari layar HP Anda kepada rekan peserta di sebelah Anda sekarang.</li>
            <li>Saling bacakan susunan kalimat caption iklan produk hasil kreasi bantuan ChatGPT/Gemini tadi.</li>
            <li>Diskusikan bersama: Apakah metode bantuan teknologi AI ini terasa jauh lebih praktis dan cepat dibandingkan memikirkan kata-kata sendiri secara manual?</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-people-group"></i>
          <div class="visual-3d-title">Saling Berbagi Ide Positif Antar Warga Kampoeng</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Apresiasi Hasil Karya Kelompok Kerja UMKM</span>
        <span class="slide-footer-page">26 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 27: HAMBATAN PENERAPAN (PARADOKS KETERAMPILAN) -->
    <div class="slide">
      <div class="slide-header">Hambatan Penerapan AI: Paradoks Keterampilan</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li><span class="highlight-gold">Ketakutan Awal Mental:</span> Adanya perasaan ragu takut salah memencet tombol menu aplikasi digital karena mengira teknologi itu rumit.</li>
            <li><span class="highlight-gold">Ekspektasi Keliru:</span> Anggapan keliru bahwa menggunakan kecerdasan buatan langsung menaikkan penjualan seketika tanpa dibarengi konsistensi unggah berkala.</li>
            <li>*Kunci utama menembus batas hambatan adalah berani mencoba mempraktikkannya langsung setiap hari tanpa takut salah.*</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-brain"></i>
          <div class="visual-3d-title">Mengubah Pola Pikir Untuk Maju Bersama</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Analisis Tantangan Internal Komunitas</span>
        <span class="slide-footer-page">27 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 28: METODOLOGI BELAJAR MANDIRI: DPFR -->
    <div class="slide">
      <div class="slide-header">Metodologi Belajar Mandiri: Alur Sistem DPFR</div>
      <div class="slide-content grid-2">
        <div class="premium-card">
          <ul class="text-body">
            <li>🔄 <span class="highlight-gold">D - Demonstrasi:</span> Mengingat kembali contoh cara pengisian prompt perintah yang dipelajari hari ini.</li>
            <li>✍️ <span class="highlight-gold">P - Praktik Mandiri:</span> Meluangkan waktu mencoba membuat variasi prompt baru sendirian di rumah.</li>
            <li>💬 <span class="highlight-gold">F - Feedback (Umpan Balik):</span> Memantau respon ketertarikan minat beli dari warga netizen internet.</li>
            <li>🛠️ <span class="highlight-gold">R - Revisi Konten:</span> Terus menyempurnakan struktur susunan bahasa jualan agar semakin menjual.</li>
          </ul>
        </div>
        <div class="visual-3d-placeholder">
          <i class="fa-solid fa-arrows-spin"></i>
          <div class="visual-3d-title">Siklus Keberlanjutan Penguasaan Keahlian Digital</div>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Model Pembelajaran Efektif Berkelanjutan</span>
        <span class="slide-footer-page">28 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 29: ROADMAP IMPLEMENTASI BUMIJO 2026 -->
    <div class="slide">
      <div class="slide-header">Jadwal Rencana Kerja Gerakan Aksi Bumijo 2026</div>
      <div class="slide-content grid-3">
        <div class="premium-card">
          <h3 class="highlight-gold" style="font-size:20px;margin-bottom:8px;">Bulan ke-1</h3>
          <p class="text-body" style="font-size:15px;">Seluruh elemen warga pelaku UMKM Kampung Emas lancar membuka aplikasi AI pendukung di HP masing-masing tanpa kebingungan lagi.</p>
        </div>
        <div class="premium-card">
          <h3 class="highlight-gold" style="font-size:20px;margin-bottom:8px;">Bulan ke-2</h3>
          <p class="text-body" style="font-size:15px;">Mulai kompak menjalankan aksi konsisten mengunggah minimal 3 buah materi promosi hasil bantuan kecerdasan buatan ke internet setiap minggunya.</p>
        </div>
        <div class="premium-card">
          <h3 class="highlight-gold" style="font-size:20px;margin-bottom:8px;">Bulan ke-3</h3>
          <p class="text-body" style="font-size:15px;">Mengadakan evaluasi bersama untuk meninjau lonjakan angka transaksi penjualan produk dan jumlah kedatangan wisatawan ke desa.</p>
        </div>
      </div>
      <div class="slide-footer">
        <span class="slide-footer-text">Tahapan Target Nyata Keberhasilan Komunitas</span>
        <span class="slide-footer-page">29 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 30: MOCKUP FORM REALISTIS SPORTRAGA BUATAN AI -->
    <div class="slide sportraga-slide">
      <div class="slide-header" style="margin-bottom: 10px;">Output Kegiatan: Mockup Riil Platform Sportraga</div>
      
      <!-- Browser Mockup Wrapper Shell -->
      <div class="browser-window">
        <!-- Top Bar Header Browser -->
        <div class="browser-header">
          <div class="window-dots">
            <div class="w-dot wd-red"></div>
            <div class="w-dot wd-amb"></div>
            <div class="w-dot wd-grn"></div>
          </div>
          <div class="browser-url-bar">
            <i class="fa-solid fa-lock" style="color:#10b981; font-size:11px;"></i> sportraga.lovable.app/explore-venues
          </div>
          <div class="ai-badge-top">
            <i class="fa-solid fa-brain"></i> 100% GENERATED BY AI
          </div>
        </div>
        
        <!-- Application Interior Layout -->
        <div class="app-layout">
          <!-- Sidebar Navigasi App -->
          <div class="app-sidebar">
            <div style="font-weight:800; font-size:15px; color:#38bdf8; margin-bottom:15px; display:flex; align-items:center; gap:8px;">
              <i class="fa-solid fa-running"></i> Sportraga
            </div>
            <div class="side-item active"><i class="fa-solid fa-map-marked-alt"></i> Cari Lapangan</div>
            <div class="side-item"><i class="fa-solid fa-calendar-check"></i> Jadwal Saya</div>
            <div class="side-item"><i class="fa-solid fa-users"></i> Komunitas</div>
            <div class="side-item"><i class="fa-solid fa-gears"></i> Pengaturan</div>
          </div>
          
          <!-- Main Content Dashboard Area -->
          <div class="app-main-content">
            <!-- Sticky AI Info Banner -->
            <div class="ai-sticky-note">
              <i class="fa-solid fa-circle-info" style="color:#22c55e; margin-right:6px;"></i>
              <strong>Sistem Informasi Riil:</strong> Gambar komponen antarmuka, basis data filter wilayah Sleman, dan kartu pemesanan di bawah ini dibuat otomatis oleh AI via perintah prompt sekali klik.
            </div>
            
            <div class="app-content-header">
              <div class="app-title">Direktori Lapangan Olahraga Aktif</div>
              <div style="font-size:12px; color:#64748b; font-weight:600;"><i class="fa-solid fa-sliders"></i> Filter: Semua Kecamatan</div>
            </div>
            
            <!-- Real Grid Usaha/Venue List -->
            <div class="venue-grid">
              <!-- Card Item 1 -->
              <div class="venue-card">
                <div class="card-img-placeholder">
                  <div class="venue-tag">Futsal</div>
                </div>
                <div class="card-body">
                  <div class="v-name">Sleman Futsal Arena Center</div>
                  <div class="v-loc"><i class="fa-solid fa-location-dot"></i> Jl. Magelang KM 10, Sleman</div>
                  <div class="v-meta">
                    <div class="v-price">Rp 120.000<span style="font-size:10px; font-weight:normal; color:#64748b;">/jam</span></div>
                    <div class="v-rating"><i class="fa-solid fa-star"></i> 4.8</div>
                    <button class="v-btn">Pesan</button>
                  </div>
                </div>
              </div>
              
              <!-- Card Item 2 -->
              <div class="venue-card">
                <div class="card-img-placeholder badminton">
                  <div class="venue-tag">Badminton</div>
                </div>
                <div class="card-body">
                  <div class="v-name">Gedung Bulutangkis Shanti Graha</div>
                  <div class="v-loc"><i class="fa-solid fa-location-dot"></i> Kec. Mlati, Kabupaten Sleman</div>
                  <div class="v-meta">
                    <div class="v-price">Rp 50.000<span style="font-size:10px; font-weight:normal; color:#64748b;">/jam</span></div>
                    <div class="v-rating"><i class="fa-solid fa-star"></i> 4.7</div>
                    <button class="v-btn">Pesan</button>
                  </div>
                </div>
              </div>
            </div>
            
          </div>
        </div>
      </div>

      <!-- Footer Info Halaman -->
      <div class="slide-footer" style="width: 100%;">
        <span class="slide-footer-text">Sistem Prototype Aplikasi Fungsional Nyata Berbasis AI</span>
        <span class="slide-footer-page">30 dari 31</span>
      </div>
    </div>

    <!-- SLIDE 31: SESI TANYA JAWAB (Q&A) -->
    <div class="slide" style="justify-content: center; align-items: center; text-align: center; background: linear-gradient(135deg, #0F294A 0%, #06162C 100%);">
      <div style="max-width: 850px; padding: 20px; z-index:2;">
        <h2 style="font-size: 42px; font-weight: 900; color: var(--color-gold); margin-bottom: 20px; letter-spacing: 1px; text-transform: uppercase;">
          <i class="fa-solid fa-comments" style="margin-right: 12px;"></i> Pertanyaan & Diskusi
        </h2>
        <p style="font-size: 22px; line-height: 1.6; color: #FFFFFF; font-weight: 500; margin-bottom: 35px;">
          Mari saling berkolaborasi, bertukar pikiran, dan memperkuat kemandirian ekonomi Kampung Emas Bumijo bersama-sama!
        </p>
        <div style="display: inline-block; background: rgba(255, 255, 255, 0.08); border: 2px dashed var(--color-gold); padding: 12px 30px; border-radius: 12px; font-size: 20px; font-weight: 700; color: #FFFFFF; letter-spacing: 0.5px;">
          Silakan Ajukan Pertanyaan Anda
        </div>
      </div>
      <div class="slide-footer-page" style="position:absolute; bottom:40px; right:60px; background: rgba(255,255,255,0.2); color: white;">31 dari 31</div>
    </div>

    <!-- Tombol Kendali Navigasi Slide Bawah -->
    <div class="nav-controls">
      <button class="nav-btn" id="prevBtn" title="Slide Sebelumnya"><i class="fa-solid fa-arrow-left"></i></button>
      <button class="nav-btn" id="nextBtn" title="Slide Selanjutnya"><i class="fa-solid fa-arrow-right"></i></button>
    </div>

  </div>

  <!-- Script Logika Pengendali Transisi -->
  <script>
    const slides = document.querySelectorAll('.slide');
    let currentSlideIndex = 0;

    const showSlide = (index) => {
      slides[currentSlideIndex].classList.remove('active');
      currentSlideIndex = (index + slides.length) % slides.length;
      slides[currentSlideIndex].classList.add('active');
    };

    document.getElementById('nextBtn').addEventListener('click', () => showSlide(currentSlideIndex + 1));
    document.getElementById('prevBtn').addEventListener('click', () => showSlide(currentSlideIndex - 1));

    document.addEventListener('keydown', (e) => {
      if (e.key === 'ArrowRight' || e.key === ' ') {
        e.preventDefault();
        showSlide(currentSlideIndex + 1);
      }
      if (e.key === 'ArrowLeft') {
        e.preventDefault();
        showSlide(currentSlideIndex - 1);
      }
    });
  </script>
</body>
</html>
