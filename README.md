
# Tugas Kelompok 1

Simpel E-commerce Restful API dengan Go-lang


## ERD
[Erd Desain](https://dbdiagram.io/d/Copy-of-E-commerce-SI-664de795f84ecd1d22db8741)

![Erd Screenshots](https://i.postimg.cc/tT9750zL/Copy-of-E-commerce-SI.png)

1. ### Tabel user
   Deskripsi: Tabel ini menyimpan informasi tentang pengguna, yang bisa berupa BUYER (pembeli) atau SELLER (penjual).
   Kolom:
    * user_id: Primary key untuk mengidentifikasi setiap pengguna.
    * name: Nama pengguna.
    * password: Kata sandi untuk login.
    * email: Alamat email unik setiap pengguna.
    * role: Peran pengguna (BUYER atau SELLER), ditentukan oleh enum Role.
    * created_at: Waktu pembuatan akun.
    * updated_at: Waktu terakhir pembaruan akun.
2. ### Tabel item
    Deskripsi: Tabel ini menyimpan informasi tentang barang yang dijual oleh penjual (seller).
    Kolom:
    * item_id: Primary key untuk mengidentifikasi setiap barang.
    * seller_id: Foreign key yang merujuk ke user_id di tabel user, menunjukkan siapa penjual barang tersebut.
    * name: Nama barang.
    * quantity: Jumlah barang yang tersedia.
    * price: Harga barang per unit.
    * description: Deskripsi barang.
    * created_at: Waktu pembuatan entri barang.
  * updated_at: Waktu terakhir pembaruan entri barang.
3. ### Tabel order
    Deskripsi: Tabel ini menyimpan informasi tentang pesanan yang dibuat oleh pembeli (buyer).
    Kolom:
    * order_id: Primary key untuk mengidentifikasi setiap pesanan.
    * seller_id: Foreign key yang merujuk ke user_id di tabel user, menunjukkan penjual dari barang yang dipesan.
    * buyer_id: Foreign key yang merujuk ke user_id di tabel user, menunjukkan pembeli yang membuat pesanan.
    * sub_total: Total harga dari semua barang dalam pesanan.
    * order_date: Tanggal pesanan dibuat.
    * created_at: Waktu pembuatan entri pesanan.
    * updated_at: Waktu terakhir pembaruan entri pesanan.
4. ### Tabel order_detail
    Deskripsi: Tabel ini menyimpan detail dari setiap barang yang termasuk dalam suatu pesanan.
    Kolom:
    * detail_id: Primary key untuk mengidentifikasi setiap detail pesanan.
    * order_id: Foreign key yang merujuk ke order_id di tabel order, menunjukkan pesanan mana detail ini termasuk.
    * item_id: Foreign key yang merujuk ke item_id di tabel item, menunjukkan barang yang dipesan.
    * item_name: Nama barang yang dipesan.
    * quantity: Jumlah barang yang dipesan.
    * price: Harga barang per unit saat dipesan.
    * sub_total: Total harga untuk jumlah barang yang dipesan (quantity * price).
    * created_at: Waktu pembuatan entri detail pesanan.
    * updated_at: Waktu terakhir pembaruan entri detail pesanan.


### Relasi Antar Tabel
#### Relasi user dengan item:
  Satu pengguna dengan peran SELLER dapat memiliki banyak barang (items).  
  Relasi ini direpresentasikan dengan seller_id di tabel item yang merujuk ke user_id di tabel user.
#### Relasi user dengan order:
  Satu pengguna dengan peran BUYER dapat membuat banyak pesanan (orders).
  Satu pengguna dengan peran SELLER dapat menerima banyak pesanan (orders).
  Relasi ini direpresentasikan dengan buyer_id dan seller_id di tabel order yang masing-masing merujuk ke user_id di tabel user.
#### Relasi order dengan order_detail:
  Satu pesanan dapat memiliki banyak detail pesanan (order_details). Relasi ini direpresentasikan dengan order_id di tabel order_detail yang merujuk ke order_id di tabel order.
#### Relasi item dengan order_detail:
  Satu barang (item) dapat muncul di banyak detail pesanan (order_details). Relasi ini direpresentasikan dengan item_id di tabel order_detail yang merujuk ke item_id di tabel item.

## FEATURE

1. /register: Form register yang di mana user dapat membuat account yang di mana terdapat dua role (BUYER/SELLER).
2. /login: Yang di mana user dapat mengakses seubah feature login yang sudah terdaftar.
3. /item: Creat item adalah sebuah feature yang di mana setiap seller dapat membuat sebuah produk yang akan di jual/di tampilkan untuk buyer.
4. /items: Items sendiri adalah sebuah path yang di mana user dapat melihat semua barang yang sudah di create seller sebelumnya.
5. /item/{{item_id}}: Update item itu sendiri yang di mana item yang sudah di buat seller dengan id yang sudah di daftar kan dapat di edit sepenuhnya.
6. /Item.{{item_id}}: path tersebut adalah melihat detail barang dengan id tertentu yang di inginkan.
7. /order: Path Order sendiri adalah feature yang dimana user buyer dapat order sebuah barang yang sudah di sediakan oleh seller.
8. /oder/detail: yang dimana feature tersebut dapat menampilkan seluruh transaksi order yang di lakukan oleh role buyer.
9. /oder/detail/{{oder_id}}: path tersebut adalah untuk melihat sebuah sepesifikasi transaksi yang sudah di lakukan.
10. /purchase: Purcahse sendiri adalah path yang dimana seller dapat melihat transaksi barang yang sudah terjual.

## API Spec

[Apidog](https://ve7gpwat88.apidog.io)


## Anggota

- [Haerul](https://www.github.com/haerul-umam)
- [Radya](https://www.github.com/Nrjtiii)
- [Mutiara](https://github.com/Mutiaraflv)
- [Bagus](https://github.com/ajusdwimantara)
- [Yonatan](https://github.com/yonatanpv)
