# 001 

## skin ⭐

|kategori|jenis_makanan|
|---|---|
frozen|9
kerupuk|5
mie|1
jamur|1

## code solution

```sql
select 
kategori,
count(*) as jenis_makanan 

from makanan

group by kategori
order by jenis_makanan desc;
```

# 002 

## skin ⭐

|nama_lengkap|email|
|---|---|
ANDI AGUNG PERMANA|andiagungpermana@email.com
ANDI AJI PERMANA|andiajipermana@email.com
ANDI ARYA PERMANA|andiaryapermana@email.com
ANDI KUSUMA PERMANA|andikusumapermana@email.com
ANDI PERMATA PERMANA|andipermatapermana@email.com
ANDI PUTRI PERMANA|andiputripermana@email.com
ANDI RAMADHAN PERMANA|andiramadhanpermana@email.com
ANDI RAMADHANY PERMANA|andiramadhanypermana@email.com
ANDI RANI PERMANA|andiranipermana@email.com
ANDI SETIAWAN PERMANA|andisetiawanpermana@email.com

## code solution

```sql
select
<<<<<<< HEAD
upper(nama_lengkap) as nama_lengkap,
email 
=======
    customername,
    creditlimit
from 
    customers
where 
    country = 'USA'
order by
    customername;
```
---
>>>>>>> cf6b3fb216a9d1b4d84d66f874772642e72317b7

from pelanggan

where nama_lengkap like '%Permana%'
order by nama_lengkap
limit 10;
```

# 003

## skin ⭐

|nama_makanan|kategori|average|
|---|---|---|
fishroll|frozen|51322
chikuwa|frozen|51322
dumpling_keju|frozen|51322
dumpling_ayam|frozen|51322
crab_stick|frozen|51322
flower_twister|frozen|51322
bakso_ikan|frozen|51322
bakso_tahu|frozen|51322
sosis|frozen|51322
kerupuk_mawar|kerupuk|22600
kerupuk_bawang|kerupuk|22600
kerupuk_bubur|kerupuk|22600
batagor_kering|kerupuk|22600
lidah|kerupuk|22600
mie|mie|18000
enoki|jamur|4000

## code solution

```sql
select
<<<<<<< HEAD
nama_makanan,
kategori,
round(avg(harga_beli) over(partition by kategori)) as average
=======
    city,
    sum(creditlimit) as amount
from
    customers
where
    country != 'USA'
group by
    city
having
    sum(creditlimit) < 50000
order by 
    amount desc;
```
---
>>>>>>> cf6b3fb216a9d1b4d84d66f874772642e72317b7

from makanan

order by average desc;
```

# 004

## skin ⭐

|kategori|jumlah|
|---|---:|
|frozen|461900|
|kerupuk|113000|
|mie|18000|
|jamur|4000|
|TOTAL|596900|

## code solution

```sql
(select
kategori,
sum(harga_beli) as jumlah

from makanan

group by kategori
order by jumlah desc)

union all

select 'TOTAL', (select sum(harga_beli) from makanan);
```

# 005

## flesh ⭐⭐

|nama_makanan|harga_jual|modal|keuntungan|
|---|---:|---:|---:|
dumpling_ayam|3000|1060|1940
bakso_ikan|3000|1080|1920
kerupuk_mawar|3000|1100|1900
lidah|3000|1100|1900
kerupuk_bawang|3000|1100|1900
bakso_tahu|3000|1125|1875
batagor_kering|3000|1150|1850
fishroll|3000|1197|1803
kerupuk_bubur|3000|1200|1800
dumpling_keju|3000|1240|1760
enoki|3000|1333|1667
crab_stick|2500|966|1534
flower_twister|2500|966|1534
sosis|2000|550|1450
chikuwa|2000|638|1362
mie|3000|1800|1200

## code solution

```sql
select
<<<<<<< HEAD
nama_makanan,
(harga_jual_satuan) as harga_jual,
(harga_beli/isi_per_pcs) as modal,
(harga_jual_satuan-(harga_beli/isi_per_pcs))
as keuntungan
=======
    concat(
    firstname,
    ' ',
    lastname)
from
    employees as e
join
    offices as o
on
    e.officecode=o.officecode
where
    jobtitle = 'Sales Rep'
and
    city = 'Paris';
```
---
>>>>>>> cf6b3fb216a9d1b4d84d66f874772642e72317b7

from makanan

order by keuntungan desc;
```

# 006

## skin ⭐

|nama_makanan|isi_per_pcs|harga_beli|
|---|---|---|
dumpling_keju|50|62000
bakso_ikan|50|54000
bakso_tahu|48|54000
dumpling_ayam|50|53000
fishroll|40|47900
kerupuk_bubur|20|24000
batagor_kering|20|23000
kerupuk_bawang|20|22000
kerupuk_mawar|20|22000
lidah|20|22000
mie|10|18000
enoki|3|4000

## code solution

```sql
select
<<<<<<< HEAD
nama_makanan,
isi_per_pcs,
harga_beli
=======
    email
from
    employees as e
join
    offices as o
on
    e.officecode=o.officecode
where
    territory = 'EMEA';
```
---
>>>>>>> cf6b3fb216a9d1b4d84d66f874772642e72317b7

from makanan

where harga_jual_satuan >= 3000
order by harga_beli desc;
```

# 007

## flesh ⭐⭐

|nama_lengkap|jumlah_pembelian|
|---|---|
Dwi Dewi Putri|30
Hani Ramadhan Putri|29
Budi Saputra Wulandari|27
Eka Setiawati Supriyanto|26
Dwi Ramadhany Putri|26


## code solution

```sql
select
<<<<<<< HEAD
nama_lengkap,
count(*) as jumlah_pembelian

from pelanggan p
join transaksi t
on p.id_pelanggan=t.id_pelanggan

group by nama_lengkap
order by jumlah_pembelian desc
limit 5;
=======
    concat(
    firstname,
    ' ',
    lastname) as fullname
from
    customers as c
right join
    employees as e
on
    c.salesrepemployeenumber=e.employeenumber
where
    jobtitle = 'Sales Rep'
and
    customernumber is null;
>>>>>>> cf6b3fb216a9d1b4d84d66f874772642e72317b7
```

# 008

## flesh

|tanggal_transaksi|jumlah_transaksi|
|---|---|
2024-08-20|79
2024-02-07|77
2024-09-01|75


## code solution

```sql
select 
tanggal_transaksi,
count(*) as jumlah_transaksi

from pelanggan p
join transaksi t
on p.id_pelanggan=t.id_pelanggan

group by tanggal_transaksi
order by jumlah_transaksi desc
limit 3;
```