# Fundamental SQL Using FUNCTION and GROUP BY

### About the project

Pada sebuah store, terdapat data transaksi penjualan selama beberapa bulan yang mencakup berbagai informasi penting mengenai produknya. Store tersebut ingin melakukan analisis data penjualan yang ada di store. 

Adapun laporan yang diminta sebagai berikut:
1. Total jumlah seluruh penjualan (total/revenue).
2. Total quantity seluruh produk yang terjual.
3. Total quantity dan total revenue untuk setiap kode produk.
4. Rata - Rata total belanja per kode pelanggan.
5. Selain itu,  jangan lupa untuk menambahkan kolom baru dengan nama ‘kategori’ yang mengkategorikan total/revenue ke dalam 3 kategori: High: > 300K; Medium: 100K - 300K; Low: <100K.

Berikut adalah **tabel tr_penjualan**:
![image](https://github.com/user-attachments/assets/cc3c7652-f7ad-4e70-9dc0-ee4f9cc9d1ff)

### Analisis Penjualan Part 1
Berikut adalah laporan bagian pertama yang diminta:
1.	Total jumlah seluruh penjualan (total/revenue).
2.	Total quantity seluruh produk yang terjual.
3.	Total quantity dan total revenue untuk setiap kode produk.

#### Sample Query
Berikut adalah contoh query yang dapat digunakan untuk memenuhi kebutuhan laporan ini:
```
## 1. Total jumlah seluruh penjualan (total/revenue).
SELECT SUM(total) as total 
FROM tr_penjualan;

## 2. Total quantity seluruh produk yang terjual.
SELECT SUM(qty) as qty 
FROM tr_penjualan;

## 3. Total quantity dan total revenue untuk setiap kode produk.
SELECT kode_produk, SUM(qty) as qty,SUM(total) as total 
FROM tr_penjualan
GROUP BY kode_produk;

```

#### Expected Output
Hasil dari query akan berupa tabel dengan format berikut:

1. Total jumlah seluruh penjualan (total/revenue).

![Screenshot 2025-01-25 1552243](https://github.com/user-attachments/assets/8ce29775-42a8-4e6a-a58f-2eef83d19404)

2. Total quantity seluruh produk yang terjual.

![Screenshot 2025-01-25 155224](https://github.com/user-attachments/assets/7da1c8ba-17fb-483a-8ccb-cdc6d953b0c2)

3. Total quantity dan total revenue untuk setiap kode produk.

![Screenshot 2025-01-25 155237](https://github.com/user-attachments/assets/5183dcb2-98a7-41ca-b838-bbb9442a7263)


### Analisis Penjualan Part 2
Berikut adalah laporan bagian kedua yang diminta:

4. Rata - Rata total belanja per kode pelanggan.
5. Selain itu,  jangan lupa untuk menambahkan kolom baru dengan nama ‘kategori’ yang mengkategorikan total/revenue ke dalam 3 kategori: High: > 300K; Medium: 100K - 300K; Low: <100K.

#### Sample Query
Berikut adalah contoh query yang dapat digunakan untuk memenuhi kebutuhan laporan ini:
```
## 4. Rata - Rata total belanja per kode pelanggan.
SELECT kode_pelanggan, AVG(total) as avg_total 
FROM tr_penjualan
GROUP BY kode_pelanggan;

## 5. Selain itu,  jangan lupa untuk menambahkan kolom baru dengan nama ‘kategori’ yang mengkategorikan total/revenue ke dalam 3 kategori: High: > 300K; Medium: 100K - 300K; Low: <100K.
SELECT kode_transaksi,kode_pelanggan,no_urut,kode_produk, nama_produk, qty, total,
CASE  
    WHEN total > 300000 THEN 'High'
    WHEN total < 100000 THEN 'Low'  
    ELSE 'Medium'  
END as kategori 
FROM tr_penjualan;
```

#### Expected Output
Hasil dari query akan berupa tabel dengan format berikut:

4. Rata - Rata total belanja per kode pelanggan.

![image](https://github.com/user-attachments/assets/54f56362-46cc-4737-bd01-6de8c5017a6b)

5. Selain itu,  jangan lupa untuk menambahkan kolom baru dengan nama ‘kategori’ yang mengkategorikan total/revenue ke dalam 3 kategori: High: > 300K; Medium: 100K - 300K; Low: <100K.
![image](https://github.com/user-attachments/assets/0cb9c243-cc68-4eb7-8c42-603296178bc7)

Pada tabel ini ditampilkan data transaksi penjualan yang telah dilengkapi dengan kolom baru bernama 'kategori.' 
Kolom ini mengelompokkan total revenue dari setiap transaksi ke dalam tiga tingkatan berdasarkan pendapatan yang dihasilkan oleh store tersebut.
- High (di atas 300K)
- Medium (antara 100K hingga 300K)
- Low (di bawah 100K)


#### Disclaimer
Proyek ini merupakan bagian dari modul pembelajaran [DQLab](https://academy.dqlab.id/main)







