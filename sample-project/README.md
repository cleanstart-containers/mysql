# MySQL Sample Project

This sample uses the **CleanStart MySQL** image (`cleanstart/mysql:latest-dev`) to run a container and demonstrates adding, updating, and retrieving data.

## 1. Pull and run the container

```bash
docker pull cleanstart/mysql:latest-dev
```

```bash
docker run -d \
  --name mysql-demo \
  -p 3306:3306 \
  -e MYSQL_ROOT_PASSWORD=root123 \
  cleanstart/mysql:latest-dev
```

Wait a few seconds for MySQL to start.

## 2. Connect to MySQL

```bash
docker exec -it mysql-demo mysql -u root -p
```

Enter password: `root123`

## 3. Add data

In the MySQL shell:

```sql
CREATE DATABASE demodb;
USE demodb;

CREATE TABLE products (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  price DECIMAL(10,2),
  quantity INT
);

INSERT INTO products (name, price, quantity) VALUES
  ('Widget', 9.99, 100),
  ('Gadget', 19.99, 50),
  ('Gizmo', 4.99, 200);
```

## 4. Update data

```sql
UPDATE products SET price = 12.99, quantity = 90 WHERE name = 'Widget';

UPDATE products SET quantity = quantity - 10 WHERE id = 2;
```

## 5. Retrieve data

```sql
SELECT * FROM products;

SELECT id, name, price FROM products WHERE price < 15;

SELECT * FROM products WHERE id = 1;
```

Type `exit` to leave the MySQL shell.

## One-off command (from host)

```bash
docker exec mysql-demo mysql -u root -proot123 -e "SELECT * FROM demodb.products;"
```

## Clean up

```bash
docker stop mysql-demo
docker rm mysql-demo
```

## Resources

- [CleanStart](https://cleanstart.com/)
- [MySQL Documentation](https://dev.mysql.com/doc/)
