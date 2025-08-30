# ROUTING STATIS
## Pengertian
Routing Statis adalah metode konfigurasi rute jaringan dengan cara menentukan jalur paket data secara manual oleh administrator jaringan, bukan otomatis oleh router seperti pada routing dinamis. Metode ini cocok untuk jaringan kecil yang stabil karena administrator dapat memiliki kontrol penuh atas aliran data, namun memerlukan pemeliharaan manual saat ada perubahan topologi jaringan. 
## Topologi Jaringan
Berikut adalah topologi jaringan yang digunakan pada simulasi routing statis menggunakan Cisco Packet Tracer :
## 1. Hubungkan kabel

PC → Router: Copper Straight-Through (pilih FastEthernet0 di PC, GigabitEthernet0/0 di Router).

Router ↔ Router: Copper Cross-Over (kamu sudah pilih ini) antara G0/1 ↔ G0/1.

Jangan lupa pasang kabel ke port yang sesuai saat diminta Packet Tracer.

## 2. Set IP di PC

Di PC → Desktop → IP Configuration

💻 PC1

- IP Address: 192.168.1.2

- Subnet Mask: 255.255.255.0

- Default Gateway: 192.168.1.1

💻 PC2

- IP Address: 192.168.3.2

- Subnet Mask: 255.255.255.0

- Default Gateway: 192.168.3.1
