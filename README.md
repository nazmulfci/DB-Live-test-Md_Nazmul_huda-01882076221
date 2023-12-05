# DB-Live-test-Md_Nazmul_huda-01882076221

## User table
CREATE TABLE User (
    user_id INT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL,
);

## Menu table
CREATE TABLE Menu (
    menu_id INT PRIMARY KEY,
    menu_name VARCHAR(255) NOT NULL,
);

## Item table
CREATE TABLE Item (
    item_id INT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    description VARCHAR(255),
    photo VARCHAR(255), 
);

## Order table
CREATE TABLE Order (
    order_id INT PRIMARY KEY,
    user_id INT,
    status VARCHAR(20) NOT NULL,
    order_date DATE NOT NULL,
    FOREIGN KEY (user_id) REFERENCES User(user_id)
);

## OrderItem table 
CREATE TABLE OrderItem (
    order_id INT,
    item_id INT,
    quantity INT NOT NULL,
    PRIMARY KEY (order_id, item_id),
    FOREIGN KEY (order_id) REFERENCES Order(order_id),
    FOREIGN KEY (item_id) REFERENCES Item(item_id)
);
