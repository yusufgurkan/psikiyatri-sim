# Ruh Sağlığı Acil Servisi — Triyaj ve Kapasite Planlama DSS

Bu proje, yüksek yoğunluklu psikiyatri acil servislerinde hasta akışını, triyaj süreçlerini ve kaynak yönetimini optimize etmek amacıyla geliştirilmiş bir **Karar Destek Sistemi (DSS)** ve **Kesikli Olay Simülasyonu** uygulamasıdır.

![Psikiyatri Acil Servisi Karar Destek Sistemi paneli](report_images/image3.png)

## 📌 Projenin Amacı

Ruh sağlığı acil servisleri, kriz düzeylerine göre hızlı ve hassas müdahale gerektiren dinamik ortamlardır. Bu simülasyon aracı, hastane yöneticilerine şu gibi kritik senaryoları test etme imkanı sunar:

- "1 yerine 2 psikiyatrist olsaydı bekleme süreleri ne kadar kısalırdı?"
- "Hasta geliş hızı %20 artarsa kaç kişi hizmet alamadan ayrılır (Reneging)?"

## Temel Özellikler

- **Hiyerarşik Triyaj:** Hastalar P1 (Akut), P2 (Orta) ve P3 (Hafif) olarak sınıflandırılır. Akut vakalar kuyrukta otomatik olarak en öne alınır.
- **Akıllı Kaynak Atama:** Kriz seviyesine göre müsait olan uzman doktor veya psikolog ataması gerçek zamanlı yapılır.
- **Vazgeçme (Reneging) Analizi:** Bekleme toleransını aşan hastaların sistemi terk etme oranları matematiksel olarak izlenir.
- **Gerçek Zamanlı Dashboard:** Simülasyon çıktıları (bekleme süreleri, kuyruk uzunluğu, doktor doluluk oranları) anlık grafiklerle görselleştirilir.

## Örnek Senaryolar

Sol paneldeki parametreler değiştikçe sonuçlar değişir. Rapor için alınan üç örnek çalıştırma:

| Senaryo | Ort. hasta geliş (dk) | Triyaj hemşiresi | Psikiyatrist | Psikolog | Gelen hasta | Ayrılan | Ort. bekleme |
|---|---|---|---|---|---|---|---|
| Rahat kapasite | 16,5 | 3 | 2 | 4 | 83 | 0 | 10,74 dk |
| Sınırlı kapasite | 11,5 | 2 | 1 | 2 | 111 | 0 | 160,28 dk |
| Aşırı yoğun | 4 | 2 | 1 | 2 | 385 | 16 | 475,59 dk |

Aşırı yoğun senaryoda bekleme toleransını aşan 16 hasta sistemi terk ediyor:

![Aşırı yoğun senaryo](report_images/image5.png)

## Kullanılan Teknolojiler

**Backend (Simülasyon ve API Katmanı):**

- **Python:** Temel mantık ve veri katmanı
- **SimPy:** Kesikli olay simülasyon motoru
- **FastAPI:** Yüksek performanslı REST API altyapısı
- **NumPy:** İstatistiksel ve matematiksel hesaplamalar

**Frontend (Kullanıcı Arayüzü):**

- **Next.js & React:** Bileşen tabanlı, hızlı kullanıcı arayüzü
- **Tailwind CSS:** Modern ve duyarlı (responsive) tasarım
- **Recharts:** Simülasyon verilerinin anlık grafik görselleştirmesi
- **Axios:** Backend ile API iletişimi

---

## Kurulum ve Çalıştırma Rehberi

Projeyi kendi bilgisayarınızda çalıştırmak için aşağıdaki adımları izleyebilirsiniz.

### 1. Repoyu Klonlayın

```bash
git clone https://github.com/yusufgurkan/psikiyatri-sim.git
cd psikiyatri-sim
```

### 2. Backend Sunucusunu Başlatın

Yeni bir terminal açın ve sırasıyla şu komutları girin:

```bash
cd backend
python -m venv venv
# Sanal ortamı aktif edin (Windows için):
venv\Scripts\activate
# (Mac/Linux için): source venv/bin/activate

pip install -r requirements.txt
uvicorn main:app --reload
```

### 3. Frontend Arayüzünü Başlatın

Yeni bir terminal daha açın ve şu komutları girin:

```bash
cd frontend
npm install
npm run dev
```

## Geliştirici Ekibi

Bu proje takım çalışmasıyla aşağıdaki görev dağılımına göre geliştirilmektedir:

- **Yusuf Gürkan:** Proje Lideri & Sistem Entegrasyonu
- **Ömer Faruk Yalçınkaya:** Backend Geliştirme & SimPy Mantığı
- **Kaan Gerçek:** Frontend Geliştirme & Veri Görselleştirme
