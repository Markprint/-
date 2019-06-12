##### 电商项目建表语句

###### t_admin表

> create table t_admin(
> 
> id int(11) primary key auto_increment,
> 
> aname varchar(255),
> 
> apwd varchar(16)
> 
> );



t_category表

> create table t_category(
> 
> id int(11) primary key auto_increment,
> 
> name varchar(255),
> 
> descr varchar(255),
> 
> pid int(11),
> 
> leaf int(11),
> 
> grade int(11)
> 
> );



t_user表

> create table t_user(
> 
> id int(11) primary key auto_increment,
> 
> username varchar(40),
> 
> password varchar(16),
> 
> phone varchar(40),
> 
> addr varchar(255),
> 
> rdate timestamp
> 
> );



t_product表

> create table t_product(
> 
> id int(11) primary key auto_increment,
> 
> name varchar(40),
> 
> descr varchar(255),
> 
> normalprice double,
> 
> memberprice double,
> 
> pdate timestamp,
> 
> categoryid int(11) ,
> 
> constraint fk_product_category foreign key(categoryid) references t_category(id)
> 
> );



t_salesorder表

> create table t_salesorder(
> 
> id int(11) primary key auto_increment,
> 
> userid int(11),
> 
> addr varchar(255),
> 
> odate timestamp,
> 
> status int(11),
> 
> constraint fk_salesorder_user foreign key(userid) references t_user(id)
> 
> );



t_salesitem表

> create table t_salesitem(
> 
> id int(11) primary key auto_increment,
> 
> productid int(11),
> 
> unitprice double,
> 
> pcount int(11),
> 
> orderid int(11),
> 
> constraint fk_salesitem_product foreign key(productid) references t_product(id),
> 
> constraint fk_salesitem_salesorder foreign key(orderid) references t_salesorder(id)
> 
> );
