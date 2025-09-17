# 🚖 Uber Ride Analytics – Descriptive & Predictive Analysis

Bu çalışma, Kaggle’dan alınan **Uber Ride Analytics veri seti** üzerinde hem **betimleyici (descriptive)** hem de **tahminleyici (predictive)** analiz adımlarını kapsamaktadır.  
Amaç; yolculuk verilerini analiz ederek müşteri davranışlarını ve operasyonel süreçleri anlamak, ayrıca **Booking Value (yolculuk ücreti)** için bir tahmin modeli geliştirmektir.  



## 📌 Problem Tanımı
- Yolculuk verilerinin analizi ile müşteri davranışı ve operasyonel verimliliği anlamak  
- Booking Value (yolculuk ücreti) için regresyon tabanlı tahmin modeli geliştirmek  
- **İş faydası:**  
  - Dinamik fiyatlama stratejileri  
  - Promosyon planlaması  
  - Müşteri memnuniyeti ve sadakati artırımı  


##  Veri Seti İçeriği
- **Booking Status:** Completed, Cancelled, Incomplete  
- **Distance & Duration:** `ride_distance_km`, `avg_ctat_min`, `avg_vtat_min`, `duration_min_est`  
- **Ratings:** `driver_rating`, `customer_rating`  
- **Fare:** `booking_value`, `booking_value_adjusted`  
- **Operational:** `vehicle_type`, `payment_method`, `pickup_location`, `drop_location`  



##  Girdi & Çıktı Değişkenleri
- **Features (Girdi):**  
  - `distance_km_clean`  
  - `avg_ctat_min`  
  - `avg_vtat_min`  
  - `duration_min_est`  
  - `driver_rating`  
  - `customer_rating`  
- **Target (Çıktı):**  
  - `booking_value_adjusted`  



## 🔍 Descriptive Analiz
- Veri temizleme & eksik değer doldurma (medyan/ortalama)  
- Özellik çıkarımı: `weekday`, `hour`, `duration_min_est`  
- **KPI’lar:**  
  - Tamamlanma / iptal oranı  
  - Günlük talep & ciro trendi  
  - Araç tiplerine göre gelir  
  - Ödeme yöntemlerine göre kullanım oranı  
- **Görselleştirmeler:**  
  -  Line: Saatlik & günlük talep, günlük ciro  
  -  Bar: Araç tipi geliri, ödeme yöntemi  
  -  Pie/Donut: Booking status dağılımı, araç tipi payı  
  -  Top 10 müşteri / pickup-location analizi  



## 🤖 Predictive Analiz
- Kullanılan Modeller:  
  - Linear Regression  
  - Random Forest Regressor  
  - XGBoost Regressor  
- **Değerlendirme Metrikleri:**  
  - MSE (Mean Squared Error)  
  - RMSE (Root Mean Squared Error)  
  - MAE (Mean Absolute Error)  
  - R² (Açıklanan varyans oranı)  



## 📈 Karşılaştırmalı Performans

| Model              | MSE     | RMSE   | MAE   | R²   |
|--------------------|---------|--------|-------|------|
| Linear Regression  | 3121.96 | 55.87  | 36.70 | 0.900 |
| Random Forest      | 3643.10 | 60.36  | 39.23 | 0.883 |
| XGBoost            | 3192.89 | 56.51  | 36.83 | 0.898 |


##  Yorumlar
- **En iyi model:** Linear Regression (R²=0.900)  
- Random Forest & XGBoost yakın performans gösterdi ancak daha karmaşık modellere gerek kalmadı  
- Özellik önemi:  
  - Mesafe (`distance_km_clean`) ve süre (`avg_ctat_min`) en kritik belirleyiciler  
  - Rating’ler daha zayıf ama müşteri deneyimi açısından anlamlı  


---

## ⚙️ Model Uygulaması
- Tahmin sonuçları veri setine eklendi: **`booking_value_predicted`**  
- Yeni veriler için fonksiyon geliştirildi:  

