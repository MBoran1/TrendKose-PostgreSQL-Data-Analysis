# 🛒 TrendKöşe E-Ticaret Veritabanı Yönetimi & SQL Veri Analizi (PostgreSQL)

Bu proje, **TrendKöşe** isimli sanal e-ticaret mağazasının veritabanı mimarisinin PostgreSQL üzerinde sıfırdan kurulması, ilişkisel veri yapısının yönetilmesi ve iş kararlarına altlık oluşturacak gelişmiş SQL sorgularının yazılmasını kapsar.

## 🛠️ Kullanılan Teknolojiler
* **Veritabanı:** PostgreSQL 18
* **Arayüz:** pgAdmin 4
* **Dil:** SQL (PostgreSQL Sözdizimi)

---

## 📐 Veritabanı Mimarisi & Tablolar

Proje kapsamında ilişkisel bütünlüğü (Referential Integrity) sağlanmış 5 temel tablo oluşturulmuştur:
* **`kategoriler`**: Ürün kategorileri (PK, Identity, Unique)
* **`musteriler`**: Müşteri bilgileri (PK, Unique Email)
* **`urunler`**: Mağaza stok ve ürün bilgileri (PK, FK, Check constraint `fiyat > 0`)
* **`siparisler`**: Sipariş durum ve tarih takibi (PK, FK, Check constraint `durum`)
* **`siparisdetaylari`**: Sipariş kalemi detayları (PK, FK, Check constraint `adet >= 1`)

---

## 📊 Öne Çıkan Analiz Sorguları ve İş Mantıkları

Projede aşağıdaki ileri seviye SQL konseptleri uygulanmıştır:
* **Çoklu Tablo Birleştirmeleri (`INNER JOIN`, `LEFT JOIN`):** Hiç satılmayan ürünlerin (`Masa Lambası`) tespiti ve müşteri sipariş sayıları tespiti.
* **Alt Sorgular (`Subquery`):** Ortalama harcama üzeri harcama yapan VIP müşterilerin tespiti ve kategorilere göre ortalama fiyat karşılaştırmaları.
* **Koşullu İfadeler (`CASE WHEN`):** Müşterilerin harcama tutarlarına göre üyelik segmentlerine ayrılması (*Altın Üye, Gümüş Üye, Bronz Üye, Yeni Üye*) ve sipariş durumuna göre Pivot Tablo üretilmesi.
* **Veri Güncelleme ve Silme Operasyonları:** İlişkisel kısıtlamalar (Foreign Key) dikkate alınarak iptal edilen siparişlerin güvenli şekilde silinmesi ve dinamik fiyat zam güncellemeleri.

---

## 📈 Yönetici Raporu (Executive Summary)

Yazılan birleşik SQL sorgusu sonucunda elde edilen finansal özet:
* **Toplam Ciro (İptaller Hariç):** 18.210 TL
* **En Çok Harcama Yapan Müşteri:** Mehmet Kaya (6.550 TL - Altın Üye)
* **Sipariş Vermeyen Müşteri:** Burak Arslan (0 TL - Yeni Üye)
* **Hiç Satılmayan Ürün:** Masa Lambası

---

## 🚀 Projeyi Çalıştırma
1. PostgreSQL ortamında `trendkose` adında bir veritabanı oluşturun.
2. `schema_and_queries.sql` dosyasındaki SQL komutlarını pgAdmin veya `psql` üzerinden çalıştırın.
