# ⚡ ROUTING STATIS ⚡
## Pengertian
Routing Statis adalah metode konfigurasi rute jaringan dengan cara menentukan jalur paket data secara manual oleh administrator jaringan, bukan otomatis oleh router seperti pada routing dinamis. Metode ini cocok untuk jaringan kecil yang stabil karena administrator dapat memiliki kontrol penuh atas aliran data, namun memerlukan pemeliharaan manual saat ada perubahan topologi jaringan. 
***
## Topologi Jaringan
Berikut adalah topologi jaringan yang digunakan pada simulasi routing statis menggunakan Cisco Packet Tracer :
## 1. Hubungkan kabel

PC → Router: Copper Straight-Through (pilih FastEthernet0 di PC, GigabitEthernet0/0 di Router).

Router ↔ Router: Copper Cross-Over (kamu sudah pilih ini) antara G0/1 ↔ G0/1.

Jangan lupa pasang kabel ke port yang sesuai saat diminta Packet Tracer.

## 2. Set IP di PC

Di PC → Desktop → IP Configuration

💻 PC 01

- IP Address: 192.168.1.2

- Subnet Mask: 255.255.255.0

- Default Gateway: 192.168.1.1

![PC 01](images/Screenshot(88).png)

---

💻 PC 02

- IP Address: 192.168.3.2

- Subnet Mask: 255.255.255.0

- Default Gateway: 192.168.3.1

![PC 01](images/Screenshot(89).png)

## 3. Konfigurasi Router via Config Tab (GUI Mode)

Klik router → pilih tab Config.

Di bagian kiri pilih interface yang mau dipakai, contoh GigabitEthernet0/0 dan GigabitEthernet0/1

✅ Centang On untuk mengaktifkan port.

Isi:
ROUTER 1
- IP Address : 192.168.1.1

- Subnet Mask : 255.255.255.0

![ROUTER 01](images/Screenshot(90).png)

ROUTER 2
- IP Address : 192.168.3.2

- Subnet Mask : 255.255.255.0

![ROUTER 01](images/Screenshot(91).png)


Lakukan hal yang sama di Router2 (misalnya pakai 192.168.2.1/24).

⚠️ Jangan lupa di PC juga kasih IP address manual, misalnya:

- PC1 → 192.168.1.2 / 255.255.255.0 dengan gateway 192.168.1.1

- PC2 → 192.168.3.2 / 255.255.255.0 dengan gateway 192.168.2.1

