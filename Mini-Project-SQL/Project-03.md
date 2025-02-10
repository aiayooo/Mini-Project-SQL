# Fundamental SQL Using INNER JOIN and UNION

### About The Project

#### A. PROJECT INNER JOIN

Dalam database, terdapat tabel ms_pelanggan yang berisi data - data pelanggan yang membeli produk dan tabel tr_penjualan yang berisi data transaksi pembelian di suatu store.
Suatu hari, departemen marketing & promotion meminta bantuan untuk meng-query data-data pelanggan yang membeli produk Kotak Pensil DQLab, Flashdisk DQLab 32 GB, dan Sticky Notes DQLab 500 sheets.

Buatlah query menggunakan tabel ms_pelanggan dan tr_penjualan untuk mendapatkan data - data yang diminta oleh marketing yaitu kode_pelanggan, nama_customer, alamat.

**Tabel ms_pelanggan**:
![image](https://github.com/user-attachments/assets/d9daba9d-60bb-40fb-a3f4-f775f2dff105)


**Tabel tr_penjualan**:
![image](https://github.com/user-attachments/assets/883e5a28-64d5-470c-b26c-26911dea25b9)

#### Sample Query
Berikut adalah contoh query yang dapat digunakan:
```
select distinct ms_pelanggan.kode_pelanggan, ms_pelanggan.nama_customer, ms_pelanggan.alamat
from ms_pelanggan
inner join tr_penjualan
on ms_pelanggan.kode_pelanggan = tr_penjualan.kode_pelanggan
where tr_penjualan.nama_produk = 'Kotak Pensil DQLab' OR tr_penjualan.nama_produk = 'Flashdisk DQLab 32 GB' OR tr_penjualan.nama_produk = 'Sticky Notes DQLab 500 sheets';
```

#### Expected Output
Hasil dari query akan berupa tabel berikut:
![image](https://github.com/user-attachments/assets/d447e771-4b99-4725-9c14-0f98319c993a)

Pada tabel ini ditampilkan data pelanggan yang membeli produk Kotak Pensil DQLab, Flashdisk DQLab 32 GB, dan Sticky Notes DQLab 500 sheets
yang mencakup kode pelanggan, nama customer, dan alamat pelanggan.




#### B. PROJECT UNION
Persiapkanlah data katalog mengenai mengenai nama - nama produk yang akan dijual di suatu store. Data tersebut akan digunakan dalam meeting untuk mereview produk mana saja yang akan dilanjutkan penjualannya dan mana yang tidak akan dilanjutkan.

Siapkan hanya data produk dengan harga di bawah 100K untuk kode produk prod-1 sampai prod-5; dan dibawah 50K untuk kode produk prod-6 sampai prod-10, tanpa mencantumkan kolom no_urut.

Saat mengecek data produk di database, terdapat 2 tabel yang sama - sama berisi data katalog, yaitu:
**Tabel ms_produk_1**
![image](https://github.com/user-attachments/assets/60a625a6-6beb-43d3-b10a-e365f0979b09)

**Tabel ms_produk_2**
![image](https://github.com/user-attachments/assets/0ed7fec5-12a0-432e-b46e-5d86259016a2)

#### Sample Query
Berikut adalah contoh query yang dapat digunakan:
```
select kode_produk, nama_produk, harga from ms_produk_1 where harga < 100000 
union
select kode_produk, nama_produk, harga from ms_produk_2 where harga < 50000;
```

#### Expected Output
Hasil dari query akan berupa tabel berikut:
![image](https://github.com/user-attachments/assets/8623cb32-7b45-441a-805b-21edfaf40376)

Pada tabel ini ditampilkan data produk dengan harga di bawah 100K untuk kode produk prod-1 hingga prod-5, serta dibawah 50K untuk kode produk prod-6 sampai prod-10.

#### Disclaimer
Proyek ini merupakan bagian dari modul pembelajaran [DQLab](https://academy.dqlab.id/main)
