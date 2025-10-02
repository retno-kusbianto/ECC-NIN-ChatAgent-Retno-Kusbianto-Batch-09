# ECC-NIN-ChatAgent-Retno-Kusbianto-Batch-09
# Open Weather
### Workflow n8n ini dibuat untuk mengetahui pengenalan Kondisi Cuaca pada suatu daerah :
Mengambil API dari Open Weather, dengan menampilkan data :
- Curah Hujan
- Kecepatan Angin
- Temperatur Udara
- Kelembapan Udara
- Kelembapan Tanah

# 🔄 Alur Kerja Workflow
![Opend Weather Worflow](https://github.com/retno-kusbianto/ECC-NIN-ChatAgent-Retno-Kusbianto-Batch-09/blob/main/Folder/Workflow.JPG)

1. HTML / Telegram Trigger
  - Workflow akan aktif setiap kali ada user yang mengirim pesan lewat chat agent (HTML) ataupun Bot Telegram.
  - Pesan user (misalnya: “Bandung”) akan diteruskan ke workflow.
  
2. AI Agent (Google Gemini + Tools)
  - Pesan dari user masuk ke AI Agent.
  - AI Agent diberi instruksi khusus:
    - Membuat URL API OpenWeather sesuai nama kota yang diketik user.
    - Memanggil GetData (HTTP Request Tool) untuk mengambil data cuaca dari API.
    - Setelah dapat data cuaca, AI Agent menganalisis dan menyusun laporan cuaca dalam bahasa Indonesia dengan format mudah dipahami + emoji.

3. GetData (HTTP Request Tool)
  - Node ini dipanggil oleh AI Agent untuk benar-benar mengakses API OpenWeather.
  - Data mentah cuaca (suhu, kelembaban, kondisi, angin, dsb.) dikirim kembali ke AI Agent.

4. AI Agent – Analisis Cuaca
  - Dari data API tadi, AI Agent membuat ringkasan:
    - Nama Kota
    - Suhu, Kelembaban, Tekanan Udara
    - Kondisi cuaca (cerah, hujan, berawan, dll)
    - Kecepatan & arah angin
    - Analisis singkat (nyaman, perlu waspada, dll)
    - Tambah emoji ☀️☔💨❄️ biar lebih jelas.
   
5. Respond to Webhook / Send Telegram Message
  - Hasil analisis cuaca dikirim balik ke user melalui Chat Agent (HTML) ataupun Bot Telegram.
  - Jadi user langsung dapat jawaban berupa laporan cuaca yang rapi.

### 📌 KESIMPULAN
Workflow ini bekerja seperti asisten cuaca otomatis:
- User: ketik nama kota ke Chat Agent (HTML) ataupun bot Telegram.
- Workflow: ambil data cuaca → analisis → balas ke user dengan laporan singkat

⚡ Jadi inti workflow:
- HTML Webhook (Chat Agent) → AI Agent + API cuaca → Respond Webhook (Outout)
- Telegram input → AI Agent + API cuaca → Telegram output.

Contoh Output dari Chat Agent / HTML

![Output Keadaan Cuaca_Lewat_Chat_Agent_HTML](https://github.com/retno-kusbianto/ECC-NIN-ChatAgent-Retno-Kusbianto-Batch-09/blob/main/Folder/Output%20Chat%20Agent.JPG)

Contoh Output dari Telegram

![Output Keadaan Cuaca_Lewat_Telegram](https://github.com/retno-kusbianto/ECC-NIN-ChatAgent-Retno-Kusbianto-Batch-09/blob/main/Folder/Output_Telegram.JPG)
