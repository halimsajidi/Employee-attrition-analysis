# Proyek Akhir: Menyelesaikan Permasalahan Perusahaan Edutech

## Business Understanding

Perusahaan menghadapi tantangan dalam mempertahankan karyawan yang berkualitas dan meningkatkan produktivitas tim. Dengan tingginya tingkat pergantian karyawan, perusahaan berisiko kehilangan pengetahuan berharga dan investasi yang telah dilakukan dalam pelatihan karyawan. Oleh karena itu, penting untuk memahami faktor-faktor yang mempengaruhi keputusan karyawan untuk bertahan atau keluar dari perusahaan.

### Permasalahan Bisnis

1. Tingkat Pergantian Karyawan yang Tinggi: Meningkatnya jumlah karyawan yang memilih untuk keluar dari perusahaan, yang dapat menyebabkan kerugian finansial dan penurunan produktivitas.
2. Identifikasi Faktor Penyebab: Ketidakpastian mengenai faktor-faktor yang berkontribusi terhadap keputusan karyawan untuk bertahan atau meninggalkan perusahaan.

### Cakupan Proyek

1. Analisis Data Karyawan: Menganalisis dataset yang berisi informasi demografis dan metrik kerja untuk menemukan pola yang berhubungan dengan pergantian karyawan.
2. Model Prediksi: Membangun model prediktif untuk memprediksi kemungkinan seorang karyawan akan melakukan atrisi berdasarkan fitur-fitur dalam dataset.
3. Visualisasi Data: Membuat dashboard bisnis yang menunjukkan temuan dari analisis data, termasuk faktor-faktor yang paling memengaruhi kepuasan dan retensi karyawan.
4. Rekomendasi Strategis: Menyusun rekomendasi berdasarkan analisis untuk meningkatkan retensi dan kepuasan karyawan.
   
### Persiapan

Sumber data: https://www.ibm.com/communities/analytics/watson-analytics-blog/watson-analytics-use-case-for-hr-retaining-valuable-employees/

Setup environment:

```bash
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.preprocessing import LabelEncoder
from sklearn.model_selection import train_test_split

#model machine learning
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from sklearn.svm import SVC
from xgboost import XGBClassifier

# evaluasi model
from sklearn.metrics import confusion_matrix, recall_score, f1_score, accuracy_score, precision_score

# deploy
from joblib import dump, load
```
### Exploratory Data Analysis

![image](https://github.com/user-attachments/assets/bafbd5fa-349a-4abd-b23c-6d7eaf60d231)

Berdasarkan grafik di atas menunjukkan bahwa proporsi karyawan yang meninggalkan perusahaan jauh lebih sedikit dibandingkan yang tetap tinggal.


![image](https://github.com/user-attachments/assets/cacba7b7-42b0-45b4-8e90-0d21d8abc5ed)

Dapat dilihat karyawan yang berumur lebih 30 sampai 40 tahun-an cenderung tetap tinggal di tempat kerja, dibandingkan dengan karyawan yang berumur dibawah 40 tahun sampai 20 tahun-an.


![image](https://github.com/user-attachments/assets/de441d83-3b46-4b32-bfea-8d1866894a25)

Pengaruh penghasilan bulanan dapat dilihat pada grafik di atas, karyawan yang memiliki penghasilan bulanan lebih besar cenderung lebih memilih tinggal dibandingkan dengan karyawan yang memliki penghasilan bulanan lebih rendah.


![image](https://github.com/user-attachments/assets/c4f283d1-d45f-4c66-a771-01a00adc6280)

Grafik di atas menunjukkan bahwa karyawan yang sering bekerja lembur lebih cenderung resign dibandingkan yang tidak.


![image](https://github.com/user-attachments/assets/3274c82d-c288-4e92-b57f-7ba4734a76b2)

Berdasarkan grafik dia atas, Work-Life Balance tidak menjadi alasan karyaman melakukan resign


![image](https://github.com/user-attachments/assets/01e44ae1-ec01-4844-a12b-7d9475d2eaee)

Karyawan yang lebih lama bekerja di perusahaan cenderung lebih memlih untuk tetap tinggal dibandingkan dengan karyawan yang belum lama bekerja, walapun dapat dilihat pada grafik terdapat karyawan yang memutuskan resign walaupun sudah lama bekerja.


![image](https://github.com/user-attachments/assets/0dbfa6a2-1aff-4082-a58d-c4c18fe5c7b0)

Berdasarkan grafik di atas, menikah menjadi salah satu alasan mengapa karyawan tidak melakukan resign dan tetap tinggal di perusahaannya.


## Business Dashboard

Dashboard bisnis telah dibuat untuk memberikan gambaran visual mengenai faktor-faktor yang mempengaruhi  tingkat atrisi. Dashboard ini mencakup visualisasi data seperti grafik distribusi kepuasan karyawan, dan pengaruh tingkat atrisi.
https://lookerstudio.google.com/reporting/6407fa8e-c1d0-4830-b988-5107ced82a7f

## Conclusion
Berdasarkan hasil analisis, ada beberapa faktor yang berpengaruh signifikan terhadap keputusan karyawan untuk tetap tinggal atau keluar dari perusahaan:
1. Usia Karyawan: Karyawan yang berusia di atas 30 hingga 40 tahun cenderung lebih setia dan memilih untuk tetap tinggal di perusahaan dibandingkan dengan yang lebih muda. Hal ini mungkin disebabkan oleh stabilitas dalam karir dan tanggung jawab keluarga yang semakin meningkat.
2. Penghasilan Bulanan: Karyawan dengan penghasilan bulanan yang lebih tinggi memiliki kecenderungan untuk tetap tinggal. Karyawan yang memiliki kompensasi yang lebih baik merasa lebih dihargai dan termotivasi untuk melanjutkan karir di perusahaan.
3. Lembur (Overtime): Karyawan yang sering bekerja lembur menunjukkan kecenderungan lebih tinggi untuk resign. Hal ini mungkin berkaitan dengan kelelahan, stress, atau ketidakseimbangan antara pekerjaan dan kehidupan pribadi.
4. Work-Life Balance: Meskipun lembur menjadi salah satu faktor resign, grafik menunjukkan bahwa keseimbangan antara pekerjaan dan kehidupan pribadi (work-life balance) secara umum tidak menjadi alasan utama karyawan melakukan resign.
5. Lama Bekerja di Perusahaan: Karyawan yang sudah lama bekerja di perusahaan memiliki kecenderungan untuk tetap tinggal. Loyalitas mereka terhadap perusahaan lebih tinggi dibandingkan dengan karyawan yang baru saja bergabung.
6. Status Pernikahan: Karyawan yang sudah menikah memiliki kecenderungan yang lebih rendah untuk melakukan resign. Kemungkinan mereka mencari stabilitas yang lebih tinggi dalam pekerjaan, yang mempengaruhi keputusan untuk tetap tinggal.

Dengan model prediksi terbaik menggunakan **Random Forest**, perusahaan dapat mengidentifikasi karyawan yang berisiko resign dengan akurasi sebesar **84.9%**, sehingga bisa mengambil langkah preventif.

### Rekomendasi Action Items (Optional)
Berdasarkan kesimpulan di atas, berikut adalah beberapa rekomendasi yang dapat dilakukan oleh perusahaan untuk mengurangi tingkat pergantian karyawan:
1. Peningkatan Gaji dan Tunjangan: Mengidentifikasi karyawan dengan performa tinggi dan memberikan kenaikan gaji atau insentif yang lebih kompetitif agar mereka merasa lebih dihargai dan terdorong untuk tetap tinggal.
2. Program Keseimbangan Kerja dan Kehidupan Pribadi: Mengurangi frekuensi lembur dengan merancang program work-life balance yang lebih baik. Perusahaan dapat menyediakan jam kerja yang lebih fleksibel atau mendorong kebijakan cuti yang lebih longgar untuk mengurangi stress.
3. Program Retensi untuk Karyawan Baru: Mengembangkan program onboarding yang lebih efektif dan menyusun strategi retensi khusus untuk karyawan yang baru bergabung agar mereka lebih cepat beradaptasi dan merasa nyaman di perusahaan.
4. Peningkatan Keterlibatan Karyawan Senior: Memberikan peran mentor atau tanggung jawab tambahan bagi karyawan yang sudah lama bekerja untuk meningkatkan keterlibatan mereka dan memanfaatkan pengalaman mereka untuk mendorong loyalitas.
5. Dukungan untuk Karyawan yang Menikah: Menyediakan program kesejahteraan yang mendukung karyawan yang sudah menikah, seperti asuransi keluarga, tunjangan anak, atau kebijakan cuti yang lebih baik untuk mendukung keseimbangan kehidupan pribadi dan pekerjaan.

Implementasi dari action items ini diharapkan dapat membantu perusahaan dalam mengurangi tingkat pergantian karyawan dan meningkatkan kepuasan serta loyalitas karyawan dalam jangka panjang.
