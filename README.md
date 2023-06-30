# rental_mobilgadungan

# ERD

# DDL 

### 1. MEMBUAT DATABASE
```
CREATE DATABASE rentalmobil;
```
### 2. MASUK KEDALAM DATABASE
```
USE rentalmobil;
```
### 3. MEMBUAT TABEL
```
CREATE TABLE customer (
    ->     id_customer VARCHAR (10) PRIMARY KEY,
    ->     nama_cs VARCHAR (45),
    ->     no_hp INT (15),
    ->     alamat VARCHAR (45),
    ->     email VARCHAR (45));
```
```
CREATE TABLE sopir (
    ->     id_sopir VARCHAR (10) PRIMARY KEY,
    ->     id_kendaraan VARCHAR (10),
    ->     nama_sp VARCHAR (45),
    ->     status_sp ENUM ('TERSEDIA', 'TIDAK TERSEDIA') NOT NULL);
```
```
CREATE TABLE kendaraan (
    ->     id_kendaraan VARCHAR (10) PRIMARY KEY,
    ->     merk VARCHAR (45),
    ->     warna VARCHAR (45),
    ->     status_kdr ENUM ('TERSEDIA', 'TIDAK TERSEDIA') NOT NULL,
    ->     harga_sewa INT);
```
```
 CREATE TABLE transaksi (
    ->     id_transaksi VARCHAR (10) PRIMARY KEY,
    ->     id_customer VARCHAR (10),
    ->     id_sopir VARCHAR (10),
    ->     id_kendaraan VARCHAR (10),
    ->     tgl_pembayaran DATE,
    ->     tgl_sewa DATE,
    ->     tgl_kembali DATE,
    ->     status_transaksi VARCHAR (45),
    ->     total_harga INT,
    ->     metode_pembayaran VARCHAR (45));
```
### 4. MENAMPILKAN STRUKTUR TABEL
```
desc customer;
desc sopir;
desc kendaraan;
desc transaksi;
```
![image](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/3c384364-bd03-472e-9109-814744b5854f)

### 5. MENAMBAHKAN INDEX KEY
```
```

# SQL CRUD

### CREATE
```
INSERT INTO customer (id_customer, nama_cs, no_hp, alamat, email)
    ->     VALUES
    ->     ('CS001', 'ARUL', '089754637285', 'JL.ANGGREK', 'arul@gmail.com'),
    ->     ('CS002', 'INAY', '089654236789', 'JL.MAWAR', 'inay@gmail.com'),
    ->     ('CS003', 'RANI', '089172634563', 'JL.MELATI', 'rani@gmail.com'),
    ->     ('CS004', 'FIA', '089876543245', 'JL.KEMUNING', 'fia@gmail.com'),
    ->     ('CS005', 'FEBRI', '089764536276', 'JL.CURUG', 'febri@gmail.com'),
    ->     ('CS006', 'MELATI', '089754636532', 'JL.KENANGA', 'melati@gmail.com');
```
```
 INSERT INTO sopir (id_sopir, id_kendaraan, nama_sp, status_sp)
    ->     VALUES
    ->     ('SP001', 'KDR001', 'Janu', 'TERSEDIA'),
    ->     ('SP002', 'KDR002', 'Rudi', 'TERSEDIA'),
    ->     ('SP003', 'KDR003', 'Siti', 'TERSEDIA'),
    ->     ('SP004', 'KDR004', 'Ahmad', 'TIDAK TERSEDIA'),
    ->     ('SP005', 'KDR005', 'Lina', 'TIDAK TERSEDIA');
```
```
INSERT INTO kendaraan (id_kendaraan, merk, warna, status_kdr, harga_sewa)
    ->     VALUES
    ->     ('KDR001', 'TOYOTA', 'HITAM', 'TERSEDIA', '100000'),
    ->     ('KDR002', 'HYUNDAI', 'SILVER', 'TIDAK TERSEDIA', '500000'),
    ->     ('KDR003', 'HONDA', 'MERAH', 'TERSEDIA', '300000'),
    ->     ('KDR004', 'SUZUKI', 'HITAM', 'TIDAK TERSEDIA', '600000'),
    ->     ('KDR005', 'PORSCHE', 'UNGUN', 'TERSEDIA', '3000000');
```
```
 INSERT INTO transaksi (id_transaksi, id_customer, id_sopir, id_kendaraan, tgl_pembayaran, tgl_sewa, tgl_kembali, status_transaksi, total_harga, metode_pembayaran)
    ->     VALUES
    ->     ('01', 'CS002', 'SP001', 'KDR004', '2023-01-02', '2023-01-02', '2023-01-03', 'SELESAI', '600000', 'CASH'),
    ->     ('02', 'CS004', 'SP003', 'KDR005', '2023-02-05', '2023-02-05', '2023-02-06', 'SELESAI', '3000000', 'KREDIT'),
    ->     ('03', 'CS005', 'SP004', 'KDR003', '2023-03-20', '2023-03-21', '2023-03-22', 'SELESAI', '600000', 'CASH'),
    ->     ('04', 'CS003', 'SP001', 'KDR005', '2023-11-15', '2023-12-15', '2023-12-16', 'SELESAI', '6000000', 'CASH'),
    ->     ('05', 'CS001', 'SP002', 'KDR001', '2023-05-05', '2023-05-06', '2023-05-07', 'SELESAI', '200000', 'DEBIT'),
    ->     ('06', 'CS002', 'SP001', 'KDR005', '2023-06-17', '2023-06-17', '2023-06-18', 'SELESAI', '6000000', 'CASH');
```

### READ
```
SELECT * FROM customer;
```
![2](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/27632572-f360-4177-af21-6ead89953dee)
```
SELECT * FROM sopir;
```

![3](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/e517d0bf-6f01-4063-aac4-ca2f4d4012d5)

```
SELECT * FROM kendaraan;
```
![4](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/7004e647-48f0-4dff-a3b2-66cdcd1e71ca)
```
SELECT * FROM transaksi;
```
![5](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/b9a3c03d-652c-4932-9b0f-19dc9a647704)

### UPDATE
```
 UPDATE customer SET email = 'sahrul@gmail.com' WHERE id_customer = 'CS001';
```
![6](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/ddc6f435-9053-4309-97ec-93292acd8eb0)

```
UPDATE sopir SET status_sp = 'TERSEDIA' WHERE id_sopir = 'SP004';
```
![7](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/b789f4d6-4432-49ec-9005-9903b46c3a4f)
```
UPDATE kendaraan SET warna = 'BIRU' WHERE id_kendaraan = 'KDR005';
```
![8](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/6da833a2-76c4-40ae-b95c-bc375dd5a370)
```
UPDATE transaksi SET metode_pembayaran = 'CASH' WHERE id_transaksi = '02';
```
![9](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/1024a7c1-8d06-4fc5-8b3b-e1a72546f86a)

### DELETE
```
DELETE FROM customer WHERE id_customer='CS006';
```
![10](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/1561ecb3-2e4d-47fc-be85-2796b9cc42a0)

```
DELETE FROM sopir WHERE id_sopir='SP005';
```
![11](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/d07ec695-aa2c-4ebc-88ef-c3f0cf1b8c52)
```
DELETE FROM kendaraan WHERE id_kendaraan='KDR002';
```
![12](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/4b1995c7-ebf9-4254-8af4-2eced6e236e4)
```
DELETE FROM transaksi WHERE id_transaksi='01';
```
![13](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/96e5ed74-45e6-4fe6-b821-3977590fe33a)


# SQL JOIN
```
SELECT Transaksi.id_transaksi, Kendaraan.merk, Sopir.nama_sp, Customer.nama_cs
    -> FROM Transaksi
    -> INNER JOIN Kendaraan ON Transaksi.id_kendaraan = Kendaraan.id_kendaraan
    -> INNER JOIN Sopir ON Transaksi.id_sopir = Sopir.id_sopir
    -> INNER JOIN Customer ON Transaksi.id_customer = Customer.id_customer;
```
![14](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/05403129-60b4-4c32-b394-07e70ea3b582)

```
 SELECT Transaksi.id_transaksi, Kendaraan.merk, Transaksi.total_harga, Customer.nama_cs, Transaksi.status_transaksi
    -> FROM Transaksi
    -> LEFT JOIN Kendaraan ON Transaksi.id_kendaraan = Kendaraan.id_kendaraan
    -> LEFT JOIN Customer ON Transaksi.id_customer = Customer.id_customer;
```
![15 (2)](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/bbf4b03e-138d-4a5d-8900-70c4a2dcbef1)
```
SELECT Transaksi.id_transaksi, Transaksi.total_harga, Sopir.nama_sp, Customer.nama_cs
    -> FROM Transaksi
    -> RIGHT JOIN Sopir ON Transaksi.id_sopir = Sopir.id_sopir
    -> RIGHT JOIN Customer ON Transaksi.id_customer = Customer.id_customer;
```
![15](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/8b547397-08bd-48a5-816b-6c5f0244eeb6)
```
SELECT * FROM Transaksi
    -> LEFT OUTER JOIN Customer ON Transaksi.id_customer = Customer.id_customer
    -> UNION
    -> SELECT * FROM Transaksi
    -> LEFT OUTER JOIN Customer ON Transaksi.id_customer = Customer.id_customer;
```
![17](https://github.com/Aliyahasmarani/rental_mobilgadungan/assets/115197672/98b87e9f-88f3-4f3a-8abe-01a37b041103)

