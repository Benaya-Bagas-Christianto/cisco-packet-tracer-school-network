# 🌐 Konfigurasi Jaringan Enterprise — UBSI
### Cisco Packet Tracer · VLAN · Inter-VLAN Routing · STP

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco_Packet_Tracer-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)
![VLAN](https://img.shields.io/badge/VLAN-Configured-success?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)
![Mata Kuliah](https://img.shields.io/badge/Mata_Kuliah-Jaringan_Komputer-orange?style=for-the-badge)

---

## 📋 Tentang Proyek

Proyek ini merupakan **simulasi dan konfigurasi arsitektur jaringan enterprise** yang dikerjakan sebagai tugas mata kuliah **Jaringan Komputer** di Universitas Bina Sarana Informatika (UBSI).

Simulasi dibangun menggunakan **Cisco Packet Tracer** dengan menerapkan konsep VLAN, Inter-VLAN Routing, dan manajemen switching untuk lingkungan jaringan multi-departemen layaknya jaringan sebuah sekolah atau kampus skala kecil.

---

## 🎯 Tujuan Proyek

- ✅ Memahami konsep dan implementasi **VLAN** (Virtual Local Area Network)
- ✅ Mengonfigurasi **Inter-VLAN Routing** menggunakan Router-on-a-Stick
- ✅ Menerapkan **Spanning Tree Protocol (STP)** untuk mencegah *broadcast storm*
- ✅ Merancang topologi jaringan yang **efisien dan terstruktur**
- ✅ Memisahkan jaringan antar departemen demi keamanan dan manajemen yang lebih baik

---

## 🏗️ Topologi Jaringan

```
                        [ INTERNET / ISP ]
                               |
                          [ ROUTER ]
                               |
                    [ MULTILAYER SWITCH ]
                     /         |         \
              [VLAN 10]   [VLAN 20]   [VLAN 30]
              Akademik    Administrasi  Laboratorium
              /    \         |            /    \
           PC1    PC2       PC3         PC4   PC5
```

---

## 📡 Daftar VLAN

| VLAN ID | Nama           | Subnet           | Gateway         | Keterangan              |
|---------|----------------|------------------|-----------------|-------------------------|
| 10      | Akademik       | 192.168.10.0/24  | 192.168.10.1    | Ruang Kelas & Pengajar  |
| 20      | Administrasi   | 192.168.20.0/24  | 192.168.20.1    | Tata Usaha & Staf       |
| 30      | Laboratorium   | 192.168.30.0/24  | 192.168.30.1    | Lab Komputer            |

---

## 🛠️ Teknologi & Perangkat

| Komponen            | Perangkat / Teknologi           |
|---------------------|---------------------------------|
| Simulasi            | Cisco Packet Tracer 8.x         |
| Router              | Cisco Router 2911               |
| Switch (Core)       | Cisco Catalyst 3560 (L3)        |
| Switch (Access)     | Cisco Catalyst 2960             |
| Protokol Routing    | Router-on-a-Stick (Subinterface)|
| Protokol Switching  | IEEE 802.1Q Trunking            |
| Loop Prevention     | Spanning Tree Protocol (STP)    |

---

## ⚙️ Konfigurasi Utama

### 1. Konfigurasi VLAN di Switch

```bash
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name Akademik
Switch(config)# vlan 20
Switch(config-vlan)# name Administrasi
Switch(config)# vlan 30
Switch(config-vlan)# name Laboratorium
```

### 2. Konfigurasi Trunk Port

```bash
Switch(config)# interface GigabitEthernet0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan 10,20,30
```

### 3. Konfigurasi Inter-VLAN Routing (Router-on-a-Stick)

```bash
Router(config)# interface GigabitEthernet0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.10.1 255.255.255.0

Router(config)# interface GigabitEthernet0/0.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.20.1 255.255.255.0

Router(config)# interface GigabitEthernet0/0.30
Router(config-subif)# encapsulation dot1Q 30
Router(config-subif)# ip address 192.168.30.1 255.255.255.0
```

---

## 📂 Struktur File

```
cisco-packet-tracer-school-network/
│
├── Project Jaringan Komputer.pkt    <- File simulasi Cisco Packet Tracer
├── Dokumentasi Jaringan Kel 2.pdf   <- Laporan & dokumentasi lengkap
└── README.md                        <- Halaman ini
```

---

## 🚀 Cara Menggunakan

### Prasyarat
- Install **Cisco Packet Tracer 8.x** terlebih dahulu
  - Download gratis di: [Cisco Networking Academy](https://www.netacad.com/) (butuh akun)

### Langkah-langkah

1. **Clone atau Download** repository ini:
   ```bash
   git clone https://github.com/Benaya-Bagas-Christianto/cisco-packet-tracer-school-network.git
   ```

2. **Buka file `.pkt`** menggunakan Cisco Packet Tracer:
   ```
   File → Open → Project Jaringan Komputer.pkt
   ```

3. **Jalankan simulasi** dengan menekan tombol **Play** di pojok kanan bawah layar.

4. **Uji konektivitas** antar VLAN menggunakan perintah `ping`:
   ```
   PC> ping 192.168.20.1
   PC> ping 192.168.30.1
   ```

5. Baca **Dokumentasi Jaringan Kel 2.pdf** untuk memahami detail topologi, konfigurasi lengkap, dan hasil pengujian.

---

## ✅ Hasil Pengujian Konektivitas

| Sumber     | Tujuan         | Status      |
|------------|----------------|-------------|
| VLAN 10    | VLAN 20        | ✅ Berhasil  |
| VLAN 10    | VLAN 30        | ✅ Berhasil  |
| VLAN 20    | VLAN 30        | ✅ Berhasil  |
| Semua VLAN | Gateway Router | ✅ Berhasil  |

---

## 👨‍💻 Developer

**Benaya Bagas Christianto**  
Mahasiswa Teknologi Informasi — Universitas Bina Sarana Informatika (UBSI)

[![GitHub](https://img.shields.io/badge/GitHub-Benaya--Bagas--Christianto-181717?style=flat-square&logo=github)](https://github.com/Benaya-Bagas-Christianto)

---

## 📄 Lisensi

Proyek ini dibuat untuk keperluan **akademik** sebagai tugas mata kuliah Jaringan Komputer.  
Bebas digunakan sebagai referensi belajar dengan tetap mencantumkan sumber.

---

<div align="center">
  <sub>Dibuat dengan ❤️ oleh <strong>Benaya Bagas Christianto</strong> · UBSI 2024</sub>
</div>
