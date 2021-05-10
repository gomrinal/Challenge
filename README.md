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
