# DB-Live-test-Md_Nazmul_huda-01882076221

### User table
CREATE TABLE User (
    user_id INT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL,
);

### Menu table
CREATE TABLE Menu (
    menu_id INT PRIMARY KEY,
    menu_name VARCHAR(255) NOT NULL,
);

### Item table
CREATE TABLE Item (
    item_id INT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    description VARCHAR(255),
    photo VARCHAR(255), 
);

### Order table
CREATE TABLE Order (
    order_id INT PRIMARY KEY,
    user_id INT,
    status VARCHAR(20) NOT NULL,
    order_date DATE NOT NULL,
    FOREIGN KEY (user_id) REFERENCES User(user_id)
);

### OrderItem table 
CREATE TABLE OrderItem (
    order_id INT,
    item_id INT,
    quantity INT NOT NULL,
    PRIMARY KEY (order_id, item_id),
    FOREIGN KEY (order_id) REFERENCES Order(order_id),
    FOREIGN KEY (item_id) REFERENCES Item(item_id)
);

# Query 
### Display a list of 20 latest available menu items

SELECT *
FROM Item
ORDER BY item_id DESC
LIMIT 20;


### Incomplete Order list from newest order

SELECT *
FROM Order
WHERE status IN ('new', 'in-progress')
AND order_date = CURRENT_DATE
ORDER BY order_date ASC;


### Delete all complete orders that have been placed before 15 days

DELETE FROM Order
WHERE status = 'completed'
AND order_date < (CURRENT_DATE - INTERVAL 15 DAY);


