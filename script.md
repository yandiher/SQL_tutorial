1. "tolong berikan saya 10 kota di USA dengan jumlah pelanggan terbanyak."

~~~ sql
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
~~~
---

2. "Saya ingin tahu pelanggan yang memiliki limit kredit nol, beserta nama kontak dan negara mereka."

~~~sql
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
~~~
---

3. "Saya ingin tahu rata-rata credit limit dari keseluruhan pelanggan serta rata-rata credit limit jika tidak menghitung yang bernilai nol."

~~~sql
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
~~~
---

4. "Siapa saja 10 karyawan dengan jumlah pelanggan terbanyak? Berikan nama lengkap karyawan dan jumlah pelanggan yang mereka tangani."

~~~sql
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
~~~
---

5. "Tolong berikan daftar kantor beserta jumlah karyawan di masing-masing kota, diurutkan dari jumlah terbanyak."

~~~sql
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
~~~
---

