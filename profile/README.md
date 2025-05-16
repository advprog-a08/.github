## Advanced Programming 2025 &mdash; A08

1. 2306152411	Muhammad Vito Secona ([@secona](https://github.com/secona))
2. 2306222746	Pascal Hafidz Fajri ([@Scallss](https://github.com/Scallss))
3. 2306228756	Krisna Putra Purnomo ([@KrisnaPutraP](https://github.com/KrisnaPutraP))
4. 2306152494	Andrew Devito Aryo ([@Andrew4Coding](https://github.com/Andrew4Coding))
5. 2306207480	Muhammad Rafli Esa Pradana ([@rafliesa](https://github.com/rafliesa))

# Group Software Architecture Assignment
## Current Architecture of the Application (C4 Diagram) - Deliverables G.1
### Context Diagram
![image](https://github.com/user-attachments/assets/2d647249-7521-4e3d-9eb5-c52396ad708b)

### Container Diagram
![image](https://github.com/user-attachments/assets/e752b0ee-63bc-4bbd-a6f8-faef17a0b643)


### Deployment Diagram
![image](https://github.com/user-attachments/assets/d9870a62-fd1e-4b97-a091-6b6872dddf44)

## Future Architecture - Deliverables G.2
### Kafka Container Diagram
![image](https://github.com/user-attachments/assets/027ee064-14ce-4e5e-99a2-99a53acc1d70)

### Kafka Deployment Diagram
![image](https://github.com/user-attachments/assets/2467e9a0-8c66-4c82-b626-5385b4734bff)

## Risk Mitigation - Deliverables G.3
### Why the risk storming technique is applied?
Kami menerapkan teknik Risk Storming untuk mengidentifikasi, memprioritaskan, dan mengurangi risiko dalam sistem pemesanan makanan berbasis microservice. Dengan arsitektur yang terdistribusi (database terpisah, komunikasi antar layanan, dan eksposur API), Risk Storming membantu tim secara kolaboratif menemukan risiko teknis dan operasional sejak awal. 

### Risk Matrix
![image](https://github.com/user-attachments/assets/9d2f21e7-da32-4e73-82ff-7a3687e9dd99)

### Current Deployment Risk Diagram
![WhatsApp Image 2025-05-16 at 7 55 04 PM](https://github.com/user-attachments/assets/979488da-2a15-4b67-bc9a-394f3086f6d1)

### Consensus
1. Lima partisipan mendapati bahwa inkonsistensi database antar microservice merupakan resiko yang cukup tinggi, karena dapat menyebabkan alur data tidak dapat ditrack. Resiko ini sendiri dapat terjadi secara berkala (6).
2. Lima partisipan mendapati bahwa koneksi yang lambat antar service juga dapat menjadi resiko, namun memiliki dampak yang tidak terlalu serius. Selain itu, resiko hanya akan terjadi ketika user menjadi banyak secara tiba-tiba (4).
3. Lima partisipan mendapati bahwa service yang tidak mendapatkan autentikasi dapat menjadi resiko, yang dimana resiko memiliki dampak yang cukup tinggi, karena dapat menyebabkan perubahan data secara ilegal oleh pihak yang tidak bertanggung jawab. Namun, resiko ini cenderung jarang untuk terjadi dengan adanya service auth yang digunakan pada sistem (3).

### Mitigations
1. **Inconsistent Database**
*Mitigasi:* Mengembangkan arsitektur ke depan dengan menerapkan event-based synchronization menggunakan Kafka untuk menjaga konsistensi antar layanan.

2. **Exposed Service Without Authentication**
*Mitigasi:* Memasang API Gateway dan menerapkan autentikasi berbasis JWT untuk memastikan hanya pengguna terverifikasi yang dapat mengakses layanan.

3. **Lambatnya Koneksi Antar Microservice**
*Mitigasi:* Mengoptimalkan jaringan menggunakan service mesh (seperti Istio atau Linkerd) untuk meningkatkan performa dan observabilitas antar layanan.
