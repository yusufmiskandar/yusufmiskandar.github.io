---

layout: post

title: "Membangun Homelab dengan Ubuntu Server, Mikrotik, dan Docker"

date: 2025-08-05 09:00:00 -0500

categories: homelab

tags: homelab ubuntu-server mikrotik docker traefik nextcloud rtrw-net hotspot-voucher

---

# 

# **Membangun Homelab dengan Ubuntu Server, Mikrotik, dan Docker**

**RT/RW Net (Hotspot Voucher \& PPPoE), Self-Hosted PDF, ERP, dan Cloud Pribadi**

Selamat datang di panduan lengkap membangun *homelab* serbaguna. Dalam artikel ini, kita akan mengubah perangkat sederhana di rumah menjadi infrastruktur IT yang kuat. Kita akan mengkonfigurasi jaringan kompleks menggunakan Mikrotik, menyiapkan server dengan Ubuntu, dan menjalankan berbagai aplikasi seperti Nextcloud, ERPNext, dan lainnya menggunakan Docker.

Tujuan akhirnya adalah menciptakan sebuah sistem yang tidak hanya mendukung kebutuhan internet keluarga dan usaha RT/RW Net, tetapi juga menyediakan layanan *cloud* pribadi yang aman dan dapat diandalkan, bahkan tanpa alamat IP publik.

## **Daftar Isi**

1. **Rancangan Jaringan**
2. **Langkah 1: Konfigurasi Dasar Mikrotik RB450GX4**

   * Reset Konfigurasi
   * Konfigurasi WAN (ether1)
   * Membuat Bridge dan Alamat IP untuk Setiap Jaringan
   * Konfigurasi DHCP Server
   * Konfigurasi DNS \& NAT

3. **Langkah 2: Konfigurasi RT/RW Net (Hotspot \& PPPoE)**

   * Membuat VLAN
   * Konfigurasi Server Hotspot Voucher
   * Konfigurasi Server PPPoE

4. **Langkah 3: Instalasi dan Persiapan Ubuntu Server**

   * Instalasi Ubuntu Server 22.04 LTS
   * Konfigurasi IP Statis

5. **Langkah 4: Instalasi Docker dan Persiapan Layanan**

   * Instalasi Docker \& Docker Compose
   * Struktur Folder Proyek

6. **Langkah 5: Deploy Layanan dengan Docker Compose \& Traefik**

   * Membuat File docker-compose.yml
   * Penjelasan Konfigurasi Setiap Layanan

7. **Langkah 6: Mengakses Layanan Secara Lokal dan Online**

   * Akses Lokal dengan DNS Statis Mikrotik
   * Akses Online Gratis dengan Cloudflare Tunnel

### **Rancangan Jaringan**

Sebelum memulai, mari kita visualisasikan kembali topologi jaringan yang akan kita bangun:

* **ISP**: Terhubung ke ether1 Mikrotik.
* **Mikrotik RB450GX4**: Pusat dari semua jaringan.

  * ether1 (WAN): DHCP Client dari ISP (192.168.0.1/24).
  * ether2 (Homelab): 192.168.11.1/24 -> Switch -> Ubuntu Server \& PC Admin.
  * ether3 (CCTV): 192.168.22.1/24 -> AP untuk perangkat IoT.
  * ether4 (Home): 192.168.33.1/24 -> AP untuk pengguna rumah.
  * ether5 (RT/RW Net): Trunk -> Switch Manageable -> AP Hotspot (VLAN 50) \& Client PPPoE (VLAN 80).

### **Langkah 1: Konfigurasi Dasar Mikrotik RB450GX4**

Asumsi kita memulai dari perangkat Mikrotik yang baru atau sudah di-reset. Akses Mikrotik menggunakan WinBox.

#### **1. Reset Konfigurasi**

Buka **System > Reset Configuration**, centang **No Default Configuration**, dan klik Reset. Router akan reboot.

#### **2. Konfigurasi WAN (ether1)**

Buat DHCP Client agar Mikrotik mendapatkan internet dari ISP.

* Buka **IP > DHCP Client**.
* Klik tombol **Add (+)**.
* Pilih **Interface: ether1**.
* Pastikan **Use Peer DNS** dan **Use Peer NTP** tercentang.
* Klik **OK**. Mikrotik Anda sekarang seharusnya sudah online.

#### **3. Membuat Bridge dan Alamat IP**

Kita akan membuat bridge untuk setiap segmen jaringan agar lebih fleksibel di kemudian hari.

* Buka **Bridge**, klik **Add (+)** untuk membuat bridge baru:

  * bridge-homelab
  * bridge-cctv
  * bridge-home

* Pindahkan port ethernet ke bridge yang sesuai di menu **Bridge > Ports**:

  * Interface ether2 ke bridge bridge-homelab.
  * Interface ether3 ke bridge bridge-cctv.
  * Interface ether4 ke bridge bridge-home.

* Sekarang, atur alamat IP untuk setiap bridge di **IP > Addresses**:

  * 192.168.11.1/24 pada interface bridge-homelab.
  * 192.168.22.1/24 pada interface bridge-cctv.
  * 192.168.33.1/24 pada interface bridge-home.

#### **4. Konfigurasi DHCP Server**

Agar perangkat yang terhubung otomatis mendapatkan IP.

* Buka **IP > DHCP Server**.
* Klik **DHCP Setup** untuk setiap bridge: bridge-homelab, bridge-cctv, dan bridge-home. Ikuti wizard hingga selesai.

#### **5. Konfigurasi DNS \& NAT**

* **DNS**: Buka **IP > DNS**. Masukkan DNS server publik (misal: 8.8.8.8 dan 1.1.1.1) dan centang **Allow Remote Requests**.
* **NAT**: Agar semua jaringan lokal bisa mengakses internet. Buka **IP > Firewall > NAT**.

  * Klik **Add (+)**.
  * **Chain**: srcnat.
  * **Out. Interface**: ether1.
  * Buka tab **Action**, pilih **Action: masquerade**.
  * Klik **OK**.

### **Langkah 2: Konfigurasi RT/RW Net (Hotspot \& PPPoE)**

Jaringan ini akan berjalan di atas ether5 menggunakan VLAN.

#### **1. Membuat VLAN**

Buka **Interfaces > VLAN**.

* **VLAN Hotspot**:

  * **Name**: vlan50-hotspot
  * **VLAN ID**: 50
  * **Interface**: ether5

* **VLAN PPPoE**:

  * **Name**: vlan80-pppoe
  * **VLAN ID**: 80
  * **Interface**: ether5

Sekarang, berikan alamat IP untuk VLAN tersebut di **IP > Addresses**:

* 192.168.44.1/24 pada interface vlan50-hotspot.
* 192.168.55.1/24 pada interface vlan80-pppoe.

#### **2. Konfigurasi Server Hotspot Voucher**

* Buka **IP > Hotspot**.
* Klik **Hotspot Setup**.

  * **Hotspot Interface**: vlan50-hotspot.
  * Ikuti wizard, untuk DNS Name bisa diisi misal net.yusufmiskandar.my.id.

* **Membuat Profile Bandwidth**:

  * Di tab **User Profiles**, klik **Add (+)**.
  * **Name**: 2M-Profile.
  * **Rate Limit (rx/tx)**: 2M/2M.
  * Klik **OK**.

* **Membuat Voucher dengan Mikhmon**: Kita akan install Mikhmon di Docker, namun untuk pengujian, Anda bisa membuat user manual di tab **Users**.

#### **3. Konfigurasi Server PPPoE**

* Buka **PPP**.
* Di tab **PPPoE Servers**, klik **Add (+)**.

  * **Service Name**: pppoe-yusuf
  * **Interface**: vlan80-pppoe
  * **Default Profile**: default-encryption
  * Klik **OK**.

* **Membuat Profile Bandwidth**:

  * Di tab **Profiles**, klik **Add (+)** untuk membuat 3 profile:

    1. **Name**: 5M-Profile, **Local Address**: 192.168.55.1, **Remote Address**: pppoe-pool, **Rate Limit**: 5M/5M.
    2. **Name**: 10M-Profile, **Local Address**: 192.168.55.1, **Remote Address**: pppoe-pool, **Rate Limit**: 10M/10M.
    3. **Name**: 20M-Profile, **Local Address**: 192.168.55.1, **Remote Address**: pppoe-pool, **Rate Limit**: 20M/20M.

  * Jangan lupa membuat IP Pool untuk pppoe-pool di **IP > Pool** (misal: 192.168.55.2-192.168.55.254).

* **Membuat User PPPoE**:

  * Di tab **Secrets**, klik **Add (+)**.
  * **Name**: (username pelanggan), **Password**: (password), **Service**: pppoe, **Profile**: (pilih profile bandwidth yang sesuai).

### **Langkah 3: Instalasi dan Persiapan Ubuntu Server**

Gunakan laptop Dell E5410 untuk server ini.

#### **1. Instalasi Ubuntu Server 22.04 LTS**

* Unduh ISO Ubuntu Server dari situs resminya.
* Buat bootable USB drive menggunakan Rufus atau BalenaEtcher.
* Boot laptop dari USB dan ikuti proses instalasi.

  * Saat instalasi, pastikan untuk memilih **Install OpenSSH server** agar bisa di-remote.
  * Biarkan konfigurasi jaringan sebagai DHCP untuk sementara.

#### **2. Konfigurasi IP Statis**

Setelah instalasi selesai dan server berjalan, remote server dari PC Admin menggunakan SSH.  
ssh username@ip-ubuntu-server  
Cari tahu nama interface jaringan Anda dengan ip a. Biasanya eth0 atau enpXsY.  
Edit file konfigurasi Netplan:  
sudo nano /etc/netplan/00-installer-config.yaml  
Ubah konfigurasinya menjadi seperti ini (sesuaikan nama interface):

network:  
ethernets:  
enp0s3: # <-- Ganti dengan nama interface Anda  
dhcp4: no  
addresses:  
- 192.168.11.2/24  
routes:  
- to: default  
via: 192.168.11.1  
nameservers:  
addresses: \[8.8.8.8, 1.1.1.1]  
version: 2

Simpan file, lalu terapkan konfigurasi: sudo netplan apply.

### **Langkah 4: Instalasi Docker dan Persiapan Layanan**

#### **1. Instalasi Docker \& Docker Compose**

Jalankan perintah berikut di terminal Ubuntu Server Anda:

\# Update package list  
sudo apt update \&\& sudo apt upgrade -y

\# Install prerequisite packages  
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

\# Add Docker's official GPG key  
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

\# Add Docker repository  
echo "deb \[arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb\_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

\# Install Docker Engine  
sudo apt update  
sudo apt install -y docker-ce docker-ce-cli containerd.io

\# Add your user to the docker group to run docker without sudo  
sudo usermod -aG docker ${USER}

\# Install Docker Compose  
sudo curl -L "https://github.com/docker/compose/releases/download/v2.20.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose  
sudo chmod +x /usr/local/bin/docker-compose

\# Logout dan login kembali agar perubahan grup user berlaku

#### **2. Struktur Folder Proyek**

Buat struktur direktori di home folder Anda untuk menyimpan data persisten dari setiap container.

cd ~  
mkdir homelab  
cd homelab  
mkdir -p data/{traefik,portainer,mikhmon,nextcloud,erpnext,stirling-pdf}  
touch docker-compose.yml  
touch data/traefik/acme.json  
chmod 600 data/traefik/acme.json

### **Langkah 5: Deploy Layanan dengan Docker Compose \& Traefik**

Edit file docker-compose.yml yang baru saja Anda buat.

nano docker-compose.yml

Salin dan tempel konfigurasi di bawah ini. Konfigurasi ini menggunakan Traefik sebagai *reverse proxy* untuk mengarahkan trafik ke layanan yang benar berdasarkan nama domain.

version: '3.8'

services:  
traefik:  
image: "traefik:v2.9"  
container\_name: "traefik"  
command:  
- "--api.insecure=true"  
- "--providers.docker=true"  
- "--providers.docker.exposedbydefault=false"  
- "--entrypoints.web.address=:80"  
- "--entrypoints.websecure.address=:443"  
- "--certificatesresolvers.myresolver.acme.httpchallenge=true"  
- "--certificatesresolvers.myresolver.acme.httpchallenge.entrypoint=web"  
- "--certificatesresolvers.myresolver.acme.email=email@anda.com" # Ganti dengan email Anda  
- "--certificatesresolvers.myresolver.acme.storage=/letsencrypt/acme.json"  
ports:  
- "80:80"  
- "443:443"  
- "8080:8080" # Untuk Traefik Dashboard  
volumes:  
- "./data/traefik/acme.json:/letsencrypt/acme.json"  
- "/var/run/docker.sock:/var/run/docker.sock:ro"  
networks:  
- proxy  
restart: unless-stopped

portainer:  
image: portainer/portainer-ce:latest  
container\_name: portainer  
command: -H unix:///var/run/docker.sock  
volumes:  
- /var/run/docker.sock:/var/run/docker.sock  
- ./data/portainer:/data  
networks:  
- proxy  
labels:  
- "traefik.enable=true"  
- "traefik.http.routers.portainer.rule=Host(`portainer.home.local`)" # Ganti domain sesuai keinginan  
- "traefik.http.routers.portainer.entrypoints=web"  
- "traefik.http.services.portainer.loadbalancer.server.port=9000"  
restart: unless-stopped

mikhmon:  
image: animegasan/mikhmonv3  
container\_name: mikhmon  
networks:  
- proxy  
labels:  
- "traefik.enable=true"  
- "traefik.http.routers.mikhmon.rule=Host(`mikhmon.home.local`)"  
- "traefik.http.routers.mikhmon.entrypoints=web"  
- "traefik.http.services.mikhmon.loadbalancer.server.port=80"  
volumes:  
- ./data/mikhmon:/var/www/html/mikhmon/data  
restart: unless-stopped

nextcloud:  
image: nextcloud:latest  
container\_name: nextcloud  
networks:  
- proxy  
volumes:  
- ./data/nextcloud:/var/www/html  
labels:  
- "traefik.enable=true"  
- "traefik.http.routers.nextcloud.rule=Host(`cloud.home.local`)"  
- "traefik.http.routers.nextcloud.entrypoints=web"  
- "traefik.http.services.nextcloud.loadbalancer.server.port=80"  
depends\_on:  
- traefik  
restart: unless-stopped

stirling-pdf:  
image: frooodle/s-pdf:latest  
container\_name: stirling-pdf  
networks:  
- proxy  
volumes:  
- ./data/stirling-pdf/training-data:/usr/share/tessdata  
- ./data/stirling-pdf/extra-config:/configs  
labels:  
- "traefik.enable=true"  
- "traefik.http.routers.stirling-pdf.rule=Host(`pdf.home.local`)"  
- "traefik.http.routers.stirling-pdf.entrypoints=web"  
- "traefik.http.services.stirling-pdf.loadbalancer.server.port=8080"  
restart: unless-stopped

\# ERPNext membutuhkan beberapa container (backend, frontend, redis, dll)  
# Ini adalah contoh sederhana, mungkin perlu penyesuaian lebih lanjut  
erpnext-db:  
image: mariadb:10.6  
container\_name: erpnext-db  
environment:  
- MYSQL\_ROOT\_PASSWORD=gantidenganpasswordaman  
volumes:  
- ./data/erpnext/db:/var/lib/mysql  
networks:  
- proxy  
restart: unless-stopped

erpnext-redis-queue:  
image: redis:6.2-alpine  
container\_name: erpnext-redis-queue  
networks:  
- proxy  
restart: unless-stopped

erpnext-redis-cache:  
image: redis:6.2-alpine  
container\_name: erpnext-redis-cache  
networks:  
- proxy  
restart: unless-stopped

erpnext-backend:  
image: frappe/erpnext:v14  
container\_name: erpnext-backend  
environment:  
- DB\_HOST=erpnext-db  
- DB\_PASSWORD=gantidenganpasswordaman  
- REDIS\_QUEUE=redis://erpnext-redis-queue:6379  
- REDIS\_CACHE=redis://erpnext-redis-cache:6379  
- LETSENCRYPT\_EMAIL=email@anda.com # Ganti  
volumes:  
- ./data/erpnext/sites:/home/frappe/frappe-bench/sites  
networks:  
- proxy  
labels:  
- "traefik.enable=true"  
- "traefik.http.routers.erpnext.rule=Host(`erp.home.local`)"  
- "traefik.http.routers.erpnext.entrypoints=web"  
- "traefik.http.services.erpnext.loadbalancer.server.port=8000"  
restart: unless-stopped

networks:  
proxy:  
external: true

**Sebelum Menjalankan:**

1. Buat network eksternal untuk Traefik: docker network create proxy
2. Ganti semua \*.home.local dengan domain lokal yang Anda inginkan.
3. Ganti email@anda.com dan password database ERPNext.

Jalankan semua layanan:  
docker-compose up -d  
Anda bisa melihat log dengan docker-compose logs -f nama\_layanan.

### **Langkah 6: Mengakses Layanan Secara Lokal dan Online**

#### **1. Akses Lokal dengan DNS Statis Mikrotik**

Ini adalah cara paling efisien untuk akses lokal. Semua perangkat di jaringan Anda akan bisa mengakses cloud.home.local tanpa konfigurasi tambahan.

* Buka **IP > DNS > Static**.
* Klik **Add (+)** untuk setiap layanan:

  * **Name**: portainer.home.local, **Address**: 192.168.11.2
  * **Name**: mikhmon.home.local, **Address**: 192.168.11.2
  * **Name**: cloud.home.local, **Address**: 192.168.11.2
  * **Name**: pdf.home.local, **Address**: 192.168.11.2
  * **Name**: erp.home.local, **Address**: 192.168.11.2

* Sekarang, coba buka http://portainer.home.local atau http://cloud.home.local dari browser di PC Admin Anda.

#### **2. Akses Online Gratis dengan Cloudflare Tunnel**

Karena tidak ada IP Publik, kita akan menggunakan Cloudflare Tunnel yang aman dan gratis.

* **Daftar Cloudflare**: Buat akun gratis di Cloudflare dan tambahkan domain Anda (bisa beli domain murah atau pakai domain gratis dari Freenom/EU.org).
* **Instal cloudflared di Ubuntu Server**:  
  curl -L --output cloudflared.deb https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb  
  sudo dpkg -i cloudflared.deb
* Login ke Cloudflare:  
  cloudflared tunnel login  
  Buka URL yang ditampilkan di browser, login, dan otorisasi domain Anda.
* Buat Tunnel:  
  cloudflared tunnel create namatunnel (misal: homelab-yusuf)
* Konfigurasi Tunnel:  
  File konfigurasi akan dibuat di ~/.cloudflared/. Cari ID tunnel Anda dan catat.  
  Buat file config.yml di dalam folder ~/.cloudflared/:  
  nano ~/.cloudflared/config.yml  
  Isi dengan konfigurasi berikut (ganti YOUR\_TUNNEL\_ID dan domain Anda):  
  tunnel: YOUR\_TUNNEL\_ID  
  credentials-file: /home/username/.cloudflared/YOUR\_TUNNEL\_ID.json # Sesuaikan path

  ingress:  
  - hostname: cloud.yusufmiskandar.my.id  
  service: http://192.168.11.2:80  
  - hostname: erp.yusufmiskandar.my.id  
  service: http://192.168.11.2:80  
  # Tambahkan layanan lain yang ingin di-expose  
  - service: http\_status:404 # Default rule

  *Penting*: Konfigurasi di atas akan mengarahkan semua permintaan dari subdomain Cloudflare ke Traefik (di port 80). Traefik kemudian akan mengarahkannya ke container yang benar berdasarkan hostname.

* Buat DNS Record di Cloudflare:  
  cloudflared tunnel route dns namatunnel cloud.yusufmiskandar.my.id  
  Ulangi untuk setiap subdomain (erp, pdf, dll).
* Jalankan Tunnel sebagai Service:  
  sudo cloudflared service install  
  sudo systemctl start cloudflared

  Sekarang, Anda seharusnya bisa mengakses https://cloud.yusufmiskandar.my.id dari mana saja di dunia! Cloudflare akan otomatis menyediakan sertifikat SSL.

  ### **Kesimpulan**

  Selamat! Anda telah berhasil membangun sebuah *homelab* yang sangat fungsional. Anda memiliki jaringan yang tersegmentasi dengan baik, sistem RT/RW Net yang siap dijalankan, dan berbagai layanan *self-hosted* yang kuat untuk produktivitas dan penyimpanan data pribadi.

  Proyek ini adalah fondasi yang luar biasa. Dari sini, Anda bisa mengeksplorasi lebih banyak layanan Docker, memperdalam keamanan jaringan, atau bahkan melakukan otomatisasi dengan Ansible. Semoga berhasil!

