# Challenge

## SQL Questions:
- Note:
- You can copy & paste my queries in the editor directly for seeing the results.
- Link: https://www.w3schools.com/SQL/TRYSQL.ASP?FILENAME=TRYSQL_SELECT_ALL

### Q-1 How many orders were shipped by speedy express in total?

```sql
select count(*) as NumberofOrders
from orders o 
left join shippers s on o.shipperid=s.shipperid
where s.shippername='Speedy Express'
group by s.shippername;
```
### Output:

| NumberofOrders |
|----------|
|  54 |


### Q-2 What is the lastname of the employee with the most orders?
```sql
select lastname from
(
  select e.lastname, count(*) as cnt
  from employees e
  join orders o on e.employeeid=o.employeeid
  group by e.lastname 
  order by cnt desc
  limit 1
) temp
```
### Output:

| LastName |
|----------|
| Peacock  |

### Q-3 What product was ordered the most by customers in germany?
```sql
select productname
from
(
  select p.productname, count(*) as cnt
  from orders o
  join customers c on o.customerid = c.customerid
  join orderdetails od on o.orderid = od.orderid
  join products p on od.productid = p.productid
  where c.country = 'Germany'
  group by p.productname
  order by cnt desc
  limit 1
) temp
```
### Output:

| ProductName |
|----------|
| Gorgonzola Telino  |
