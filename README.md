# Ringkasan Sistem Operasi

## 1. Installasi Ubuntu Server

📺 [Tonton Video di YouTube](https://youtu.be/q4Gn8AQwc98)

---

## 2. Layanan Sistem Operasi

### Eksekusi Program
- Memuat program ke memori dan menjalankannya.
- **Contoh:** Sistem operasi mengalokasikan CPU untuk menjalankan aplikasi seperti browser atau pengolah kata.

### Operasi I/O
- Menyediakan mekanisme terkendali untuk mengakses perangkat I/O.
- **Contoh:** Membaca data dari hard disk atau mengirim data ke printer.

### Manipulasi File-System
- Membuat, menghapus, membaca, dan menulis file.
- **Contoh:** Membuka dokumen atau menyimpan file ke direktori.

### Komunikasi
- Memfasilitasi pertukaran data antar proses, baik dalam satu komputer atau jaringan.
- **Contoh:** Sinkronisasi data antara aplikasi client dan server.

### Deteksi Error
- Mendeteksi kesalahan hardware (misal: disk rusak) atau operasional (misal: pembagian oleh nol).

### Proteksi
- Mengontrol akses pengguna ke sumber daya sistem.
- **Contoh:** Membatasi akses ke file sensitif.

### Akunting
- Mencatat penggunaan sumber daya untuk audit atau penagihan.
- **Contoh:** Memonitor penggunaan CPU oleh tiap pengguna.

### Diagram Status Proses

Diagram status proses menggambarkan perubahan keadaan sebuah proses selama eksekusi:

```mermaid
stateDiagram-v2
    [*] --> New
    New --> Ready
    Ready --> Running
    Running --> Waiting
    Waiting --> Ready
    Running --> Ready
    Running --> Terminated

#### Penjelasan Status:

- **New:** Proses baru dibuat. Sistem operasi mengalokasikan memori dan tabel proses.
- **Ready:** Proses siap dieksekusi, menunggu alokasi CPU.
- **Running:** Proses sedang dijalankan oleh CPU. Hanya satu proses per inti CPU.
- **Waiting:** Proses menunggu sumber daya eksternal.
- **Terminated:** Proses selesai atau dihentikan.

#### Transisi Status:

- `New → Ready:` Proses masuk antrian scheduler.
- `Ready → Running:` CPU menjalankan proses sesuai penjadwalan.
- `Running → Ready:` Proses dipreempt karena interupsi.
- `Running → Waiting:` Proses meminta sumber daya yang belum tersedia.
- `Waiting → Ready:` Sumber daya tersedia, proses kembali ke scheduler.
- `Running → Terminated:` Proses selesai atau dihentikan.

---

## 3. Usulan Sistem Operasi Server untuk Data Center

### Rekomendasi OS:

#### Linux (RHEL, CentOS, Ubuntu Server)
- **Kelebihan:**
  - Open-source, stabil, hemat sumber daya.
  - Mendukung Docker, KVM.
  - Kompatibel dengan aplikasi web dan database.
- **Contoh Aplikasi:** Apache, PostgreSQL.

#### Windows Server
- **Kelebihan:**
  - GUI intuitif.
  - Integrasi dengan produk Microsoft (Active Directory, SQL Server).
  - Cocok untuk lingkungan enterprise.

### Aplikasi Penunjang:

- **Virtualisasi/Container:**
  - VMware vSphere, Kubernetes.
- **Load Balancer:**
  - Nginx, HAProxy.
- **Monitoring:**
  - Prometheus + Grafana, Zabbix.
- **Database:**
  - MySQL, MongoDB.
- **Backup:**
  - Bacula.
- **Keamanan:**
  - SELinux/AppArmor, iptables/ufw.

**Pendapat:**  
Prioritaskan Linux untuk efisiensi biaya. Gunakan Kubernetes dan monitoring otomatis untuk keandalan.

---

## 4. Proses vs Thread

| Aspek        | Proses                                       | Thread                                  |
|--------------|----------------------------------------------|------------------------------------------|
| Definisi     | Instansi independen program.                 | Unit eksekusi dalam proses.             |
| Sumber Daya  | Memiliki memori dan resource terpisah.       | Berbagi memori dan resource induk.      |
| Overhead     | Tinggi (isolasi penuh).                      | Rendah (resource sharing).              |
| Komunikasi   | IPC (pipes, sockets) kompleks.               | Langsung via shared memory.             |
| Kegagalan    | Tidak memengaruhi proses lain.               | Dapat memengaruhi seluruh proses.       |

### Kelebihan Proses:
- Isolasi, keamanan, stabilitas.

### Kekurangan Proses:
- Konsumsi memori tinggi, komunikasi lambat.

### Kelebihan Thread:
- Efisiensi, responsif.

### Kekurangan Thread:
- Deadlock, risiko keamanan.

---

## 5. Tiga Komponen Utama Sistem Operasi dan Jenis Kernel

### Tiga Komponen Utama:

- **Kernel:** Inti OS, mengelola CPU, memori, perangkat.
- **Shell/User Interface:** CLI atau GUI untuk interaksi pengguna.
  - Contoh: Bash (Linux), Command Prompt (Windows).
- **System Utilities:** Tools bantu manajemen file, jaringan, keamanan.
  - Contoh: `ls`, `ping`.

### Jenis Kernel:

| Jenis Kernel | Ciri Khas | Kelebihan | Kekurangan |
|--------------|-----------|-----------|------------|
| **Monolitik** (Linux) | Semua layanan di kernel space. | Performa tinggi. | Risiko crash tinggi. |
| **Mikrokernel** (QNX) | Fungsi dasar saja di kernel space. | Stabil, modular. | Overhead komunikasi tinggi. |
| **Hybrid** (Windows NT, macOS) | Kombinasi keduanya. | Seimbang antara performa & stabilitas. | Kompleksitas lebih tinggi. |

---
