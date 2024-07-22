***Mini E-Commerce MicroService***:
Proyek Mini E-Commerce Microservice ini dirancang untuk mendemonstrasikan platform e-commerce yang terukur dan modular menggunakan arsitektur layanan mikro. Ini mencakup fungsi inti seperti manajemen pengguna, katalog produk, pemrosesan pesanan, integrasi pembayaran, dan layanan notifikasi. Setiap layanan dapat diterapkan secara independen dan berkomunikasi dengan layanan lain melalui API yang terdefinisi dengan baik. Proyek ini menggunakan ***choreography*** untuk interaksi antar layanan, di mana setiap layanan beroperasi secara mandiri dan berkomunikasi melalui event yang dipublikasikan dan diterima, mengurangi ketergantungan langsung antara layanan.

## Service
1. User Service
    - Manages user registration, login, profile, and verification.
    - Technology: Go, PostgreSQL.

2. Product Service
    - Description: Manages the product catalog, including adding, updating, and deleting products.
    - Technology: Go, MongoDB.

3. Order Service:
    - Description: Handles order creation, updating, and tracking.
    - Technology: Go, PostgreSQL.

4. Payment Service:
    - Description: Integrates with payment gateways like Stripe, PayPal, Xendit, or Midtrans to process transactions.
    - Technology: Go, Redis, PostgreSQL.

5. Shipment Service:
    - Description: Manages shipment tracking, including creating, updating, and tracking shipments.
    - Technology: Go, Redis, PostgreSQL.

6. Notification Service:
    - Description: Sends notifications via email, SMS, or push notifications.
    - Technology: Go, RabbitMQ.

7. Auth Service:
    - Description: Manages authentication and authorization, including JWT token management.
    - Technology: Go, Redis.

8. API Gateway:
    - Description: Acts as a single entry point to all microservices, managing routing and load balancing.
    - Technology: Go, Go-Kit or Kong.

## Monitoring and Logging
1. Monitoring: 
    - Prometheus: 
        - ***Time-Series Database***: Prometheus dirancang untuk mengumpulkan dan menyimpan metrik sebagai data rangkaian waktu. Setiap bagian data disimpan dengan stempel waktu dan sekumpulan label.
        - ***Powerful Query Language (PromQL)***: PromQL memungkinkan kueri yang fleksibel dan akurat terhadap data rangkaian waktu yang dikumpulkan.
    - Grafana:
        - ***Visualization***: Grafana adalah alat yang ampuh untuk memvisualisasikan metrik dari Prometheus (dan sumber data lainnya). Ini menyediakan dasbor interaktif dan dapat disesuaikan.
        - ***Alerts***: Grafana dapat membuat peringatan berdasarkan data metrik dan mengirimkan pemberitahuan ke berbagai saluran (seperti Slack, Email, dll.).

    Mengapa Prometheus dan Grafana?:
    - Skalabilitas: Mereka dapat menangani data dalam jumlah besar secara efisien.
    - Fleksibilitas: Cocok untuk berbagai kasus penggunaan, mulai dari pemantauan sederhana hingga visualisasi dan peringatan data yang kompleks.
    - Komunitas dan Dukungan: Keduanya diadopsi secara luas dan memiliki dukungan komunitas yang kuat, dengan dokumentasi yang luas dan banyak integrasi.

2. Logging: ELK Stack And Opentelemetry:
    - Elasticsearch: 
        - ***Search and Analysis***: Elasticsearch adalah mesin pencari terdistribusi yang memungkinkan pencarian teks lengkap yang canggih, serta analisis data terstruktur dan tidak terstruktur.
        - ***Scalability***: Designed to scale horizontally, Elasticsearch can handle large volumes of log data.
        - ***Real-Time Data***: It supports real-time data ingestion and search, making it ideal for monitoring and logging purposes.
    - Logstash:
        - ***Data Processing Pipeline***: Logstash adalah jalur pemrosesan data sisi server yang menyerap data dari berbagai sumber secara bersamaan, mengubahnya, dan mengirimkannya ke “simpanan” seperti Elasticsearch.
        - ***Flexible Configuration***: It supports a wide range of input, filter, and output plugins to transform and transport log data.
    - Kibana:
        - ***Data Visualization***: Kibana menyediakan kemampuan visualisasi selain data yang disimpan di Elasticsearch. Itu dapat membuat dan berbagi dasbor dinamis dengan cepat.
        - ***Real-Time Insights***: Hal ini memungkinkan pengguna untuk menjelajahi dan memvisualisasikan data log secara real-time, membantu dalam diagnosis dan wawasan cepat.
    - Opentelemetry:
        - ***Unified Observability***: OpenTelemetry memungkinkan mengumpulkan dan menghubungkan metrik, log, dan traces, memberikan gambaran komprehensif tentang kinerja dan perilaku sistem Anda.
        - ***Vendor-Neutral***: OpenTelemetry bersifat vendor-agnostic, artinya dapat diintegrasikan dengan berbagai backend seperti Prometheus, Grafana, ELK Stack, dan lainnya.
        - ***Standardization***: OpenTelemetry menyediakan cara standar untuk mengumpulkan data telemetri di berbagai layanan dan platform.
    
    Mengapa ELK Stack and Opentelemetry?:
    - Solusi Komprehensif: Memberikan solusi lengkap untuk mengumpulkan, memproses, menyimpan, dan memvisualisasikan data log.
    - Pencarian dan Analisis yang Kuat: Kemampuan pencarian Elasticsearch yang kuat dikombinasikan dengan visualisasi Kibana memudahkan untuk memperoleh wawasan dari data log.
    - Fleksibilitas dan Ekstensibilitas: Kemampuan untuk berintegrasi dengan berbagai sumber data dan fleksibilitas untuk mengubah data menggunakan filter Logstash menjadikan ELK Stack alat serbaguna untuk logging.

## Deployment:
1. Containerization: Docker.
2. CI/CD: github action