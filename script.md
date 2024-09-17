# 001 

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

## code solution

```sql
select
upper(nama_lengkap) as nama_lengkap,
email 

from pelanggan

where nama_lengkap like '%Permana%'
order by nama_lengkap
limit 10;
```

# 003

## code solution

```sql
select
nama_makanan,
kategori,
round(avg(harga_beli) over(partition by kategori)) as average

from makanan

order by average desc;
```

# 004

## code solution

```sql
select
kategori,
sum(harga_beli) as jumlah

from makanan

group by kategori

union

select "TOTAL", (select sum(harga_beli) from makanan)

order by jumlah;
```

# 005

## code solution

```sql
select
nama_makanan,
(harga_jual_satuan) as harga_jual,
(harga_beli/isi_per_pcs) as modal,
(harga_jual_satuan-(harga_beli/isi_per_pcs))
as keuntungan

from makanan

order by keuntungan desc;
```

# 006

## code solution

```sql
select
nama_makanan,
isi_per_pcs,
harga_beli

from makanan

where harga_jual_satuan >= 3000
order by harga_beli desc;
```

# 007

## code solution

```sql
select
nama_lengkap,
count(*) as jumlah_pembelian

from pelanggan p
join transaksi t
on p.id_pelanggan=t.id_pelanggan

group by nama_lengkap
order by jumlah_pembelian desc
limit 5;
```

# 008

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