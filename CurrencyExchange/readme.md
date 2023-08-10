

- http://localhost:8000/currency-exchange/from/USD/to/INR

```json
{
  "id": 10001,
  "from": "USD",
  "to": "INR",
  "conversionMultiple": 65.00,
  "environmentInfo": "NA"
}
```

## H2 Console

- http://localhost:8000/h2-console
- Use `jdbc:h2:mem:testdb` as JDBC URL


## Notes

## Tables Created
```
create table exchange_value 
(
	id bigint not null, 
	conversion_multiple decimal(19,2), 
	currency_from varchar(255), 
	currency_to varchar(255), 
	primary key (id)
)
```



### Creating Container

- mvn package

### Running Container

#### Basic
```
docker container run --publish 8000:8000 img
```
----
