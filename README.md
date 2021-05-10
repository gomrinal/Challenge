# Challenge

## SQL Questions:

### Q-1 How many orders were shipped by speedy express in total?

```sql
select count(*) as NumberofOrders
from orders o 
left join shippers s on o.shipperid=s.shipperid
where s.shippername='Speedy Express'
group by s.shippername;
```

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
