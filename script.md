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

select 'TOTAL', (select sum(harga_beli) from makanan)

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

# 009

## code solution

```sql
select 
case extract (month from tanggal_transaksi)
when 1 then 'January'
when 2 then 'February'
when 3 then 'March'
when 4 then 'April'
when 5 then 'May'
when 6 then 'June'
when 7 then 'July'
when 8 then 'August'
when 9 then 'September'
when 10 then 'October'
when 11 then 'November'
when 12 then 'December'
end "bulan",
count(*) as jumlah

from transaksi

group by  bulan
order by jumlah desc;
```

# 010

## code solution

```sql
select
extract(DOW from tanggal_transaksi) as hari,
count(tanggal_transaksi)/52 avg_transaksi_perhari

from transaksi

group by hari
order by avg_transaksi_perhari desc;
```

# 011

## code solution

```sql
select
nama_lengkap,
tanggal_transaksi,
count(*) jumlah

from transaksi t
join pelanggan p
on t.id_pelanggan=p.id_pelanggan

where extract(month from tanggal_transaksi) = 3
group by tanggal_transaksi, nama_lengkap
having count(*) > 2
order by tanggal_transaksi desc;
```