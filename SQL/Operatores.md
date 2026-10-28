 # SQL Operators

## Comparison Operators

| Operator | Meaning | Example |
|---|---|---|
| `=` | Equal to | `age = 18` |
| `<>` or `!=` | Not equal to | `status <> 'Closed'` |
| `<` | Less than | `price < 100` |
| `>` | Greater than | `price > 100` |
| `<=` | Less than or equal to | `age <= 18` |
| `>=` | Greater than or equal to | `age >= 18` |

## Logical Operators

- `AND`: All conditions must be true.
	```sql
	WHERE age >= 18 AND city = 'London'
	```
- `OR`: At least one condition must be true.
	```sql
	WHERE city = 'London' OR city = 'Paris'
	```
- `NOT`: Reverses a condition.
	```sql
	WHERE NOT status = 'Closed'
	```

## Other Useful Operators

- `BETWEEN`: Checks an inclusive range.
	```sql
	WHERE price BETWEEN 10 AND 50
	```
- `IN`: Matches any value in a list.
	```sql
	WHERE department IN ('IT', 'Sales')
	```
- `NOT IN`: Excludes values in a list.
	```sql
	WHERE department NOT IN ('HR', 'Legal')
	```
- `LIKE`: Searches for a pattern. `%` means any number of characters; `_` means one character.
	```sql
	WHERE name LIKE 'A%'
	```
- `NOT LIKE`: Does not match a pattern.
	```sql
	WHERE name NOT LIKE '%test%'
	```
- `IS NULL`: Checks for a missing value.
	```sql
	WHERE email IS NULL
	```
- `IS NOT NULL`: Checks that a value exists.
	```sql
	WHERE email IS NOT NULL
	```

## Arithmetic Operators

`+` addition, `-` subtraction, `*` multiplication, `/` division, `%` remainder.

```sql
SELECT price * quantity AS total
FROM Orders;
```

## Operator Order

Parentheses are evaluated first, followed by `NOT`, `AND`, then `OR`.
Use parentheses to make conditions clear:

```sql
WHERE (city = 'London' OR city = 'Paris') AND age >= 18
```

## Common Use Cases

- **Filter active adult customers:** Combine `AND` with comparison and `IS NOT NULL` operators.
	```sql
	SELECT name, email
	FROM Customers
	WHERE age >= 18 AND status = 'Active' AND email IS NOT NULL;
	```
- **Find products in a budget range:** Use `BETWEEN` with arithmetic to calculate the total value.
	```sql
	SELECT product_name, price * quantity AS total
	FROM OrderItems
	WHERE price * quantity BETWEEN 10 AND 50;
	```
