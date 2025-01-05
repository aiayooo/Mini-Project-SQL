# Fundamental SQL Using SELECT Statement


### About the project
Pada sebuah proyek dari Cabang A, terdapat database yang berisi data transaksi penjualan. Dalam proyek ini, diminta untuk menyiapkan data transaksi penjualan dengan total revenue ≥ IDR 100.000. 

Format data yang harus ditampilkan dalam hasil query meliputi:
- kode_pelanggan
- nama_produk
- qty
- harga
- total

Data harus diurutkan mulai dari total revenue terbesar. Data transaksi diambil dari tabel tr_penjualan.

### Objectives
- Menghitung total revenue setiap kode pelanggan dengan melakukan perkalian antara kolom qty dan harga, dan hasilnya dinyatakan ke dalam kolom total.
- Mengurutkan data berdasarkan kolom total dengan menggunakan "ORDER BY total DESC".

Berikut adalah contoh tabel **tr_penjualan**:
![image](https://github.com/user-attachments/assets/74e485d1-5aa3-463e-bbb1-7ad31096d109)

### Sample Query
Berikut adalah contoh query yang dapat digunakan untuk memenuhi kebutuhan proyek ini:

```
select kode_pelanggan, nama_produk, qty, harga, (qty * harga) as total
from tr_penjualan
where (qty * harga) >= 100000
order by total desc;
```

### Expected Output
Hasil dari query akan berupa tabel dengan format berikut:
![image](https://github.com/user-attachments/assets/7b2d2f12-efa5-4f15-8e73-9c710e4618b9)

Pada tabel ini menampilkan semua data yang berisi data transaksi penjualan dengan total revenue ≥ IDR 100.000.

#### Disclaimer
Proyek ini merupakan bagian dari modul pembelajaran [DQLab](https://academy.dqlab.id/main)

