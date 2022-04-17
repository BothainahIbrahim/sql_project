#create database -------------------------------

CREATE DATABASE store;
#create table countries-------------------------
CREATE TABLE countries (
    code int ,
    name varchar (20) UNIQUE,
    contintent varchar(20) not null,
    PRIMARY KEY (code)
    );


#create table use ------------------------------
CREATE TABLE users (
    id int ,
    full_name varchar (20),
    email varchar(20) UNIQUE,
    gender char(1) CHECK (gender = 'f' or gender ='m'),
    date_of_brith varchar(15),
    created_at  datetime,
    country_code int ,
    PRIMARY key (id),
    FOREIGN key (country_code) REFERENCES countries(code)
    );

#craete table orders --------------------------------
 CREATE TABLE orders (
    id int,
    user_id int,
    status varchar(6) CHECK (status="start" or status="finish"),
    created_at datetime,
    PRIMARY KEY(id),
    FOREIGN KEY(user_id) REFERENCES users(id)
);

#create table orders_products---------------------------------

CREATE TABLE orders_products (
    order_id int,
    product_id int,
    quantitay int DEFAULT 0,
    PRIMARY KEY(order_id),
    FOREIGN KEY(order_id) REFERENCES orders(id)
);



#create table product ------------------------------------------

CREATE TABLE products(
    id int,
    name varchar(10) NOT NULL,
    price int DEFAULT 0,
    status   varchar(10) CHECK (status = 'valid' or status ='expired'),
    
    create_at datetime ,
    PRIMARY KEY(id)
 
);

#- alter table orders_products to add forging Key------------------
<DDL>

ALTER TABLE orders_products 
ADD FOREIGN KEY (product_id) REFERENCES products(id)
#-----------------------------------------------------------(insert)

<DML>

INSERT INTO `countries`(`code`, `name`, `contintent`) VALUES (1,"Bothainah","----")
INSERT INTO `users`(`id`, `full_name`, `email`, `gender`, `date_of_brith`, `created_at`, `country_code`) 
VALUES (1,"Bothainah_Ibrahim","BB@.com",'f',"17\4",'17-04-22 03:17:09 PM',1)
INSERT INTO `orders`(`id`, `user_id`, `status`, `created_at`) VALUES (1,1,"start",'17-04-22 03:19:09 PM')
INSERT INTO `products`(`id`, `name`, `price`, `status`, `create_at`) VALUES (1,"COFFEE_CUP",25,"expired",'17-04-22 03:21:09 PM')
INSERT INTO `orders_products`(`order_id`, `product_id`, `quantitay`) VALUES (1,1,3)
UPDATE `countries` SET `contintent`="UPDATE" WHERE name ="Bothainah"
DELETE FROM `products` WHERE status="price"=25
#----------------------------------------------------------------------------



--------------- DEVELOER BOTHAINAH -------------------