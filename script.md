1. "tolong berikan saya 10 kota di USA dengan jumlah pelanggan terbanyak."

``` sql
select 
    city,
    count(city) as jumlah_pelanggan
from
    customers
where
    country = 'USA'
group by
    city
order by
    COUNT(city) desc
limit 10;
```
---

2. "Saya ingin tahu pelanggan yang memiliki limit kredit nol, beserta nama kontak dan negara mereka."

```sql
select
	customerName, 
	concat(contactFirstName,
	' ',
	contactLastName) as contactName,
	country
from
	customers
where
	creditLimit = 0;
```
---

3. "Saya ingin tahu rata-rata credit limit dari keseluruhan pelanggan serta rata-rata credit limit jika tidak menghitung yang bernilai nol."

```sql
select
	(select
		avg(creditLimit)
	from
		customers) as "average",

	(select
		avg(creditLimit)
	from
		customers
	where
		creditLimit > 0) 
	as
		"average when zero is not included"
```
---

4. "Siapa saja 10 karyawan dengan jumlah pelanggan terbanyak? Berikan nama lengkap karyawan dan jumlah pelanggan yang mereka tangani."

```sql
select
	concat(employees.firstName,
	' ',
	employees.lastName)
	as employeeName,
	count(*) as amount

from
	customers
join
	employees
on
	customers.salesRepEmployeeNumber 
=
	employees.employeeNumber
group by
	employeeName
order by
	amount desc
limit 10;
```
---

5. "Tolong berikan daftar kantor beserta jumlah karyawan di masing-masing kota, diurutkan dari jumlah terbanyak."

```sql
select 
    offices.city, 
    count(employees.employeeNumber)
    as amount
from
    employees
join
    offices
on
    offices.officeCode
=
    employees.officeCode
group by
    offices.city
order by
    amount desc;
```
---

6. "Tolong bantu saya mendapatkan daftar pelanggan di USA dan kredit limit mereka, diurutkan menurut nama pelanggan."

```sql
select
    customername,
    creditlimit
from 
    customers
where 
    country = 'USA'
order by
    customername
```
---

7. "Tolong carikan kota-kota di luar USA dengan total kredit limit di bawah 50,000 dan urutkan berdasarkan jumlah kredit dari yang tertinggi."

```sql
select
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
    amount desc
```
---

8. "Tolong beri saya daftar nama lengkap dari karyawan yang bekerja sebagai Sales Rep di kantor Paris."

```sql
select
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
    city = 'Paris'
```
---

9. "Tolong beri saya daftar email dari karyawan yang bekerja di wilayah EMEA."

```sql
select
    email
from
    employees as e
join
    offices as o
on
    e.officecode=o.officecode
where
    territory = 'EMEA'
```
---

10. "Tolong buatkan daftar nama lengkap dari Sales Rep yang belum memiliki pelanggan."

```sql
select
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
    customernumber is null
```
---