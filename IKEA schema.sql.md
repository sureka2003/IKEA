SETUP IKEA DATABASE SCHEMA

DROP TABLE IF EXISTS inventory, sales, products, stores;

—Product Table

CREATE TABLE products  
(  
	product\_id VARCHAR(10) PRIMARY KEY,	  
	product\_name VARCHAR(35) ,  
	category	VARCHAR(20),  
	subcategory	VARCHAR(20),  
	unit\_pice FLOAT  
);

\-- Stores Table

CREATE TABLE stores  
(  
	store\_id	VARCHAR(10) PRIMARY KEY,  
	store\_name	VARCHAR(25),  
	city	VARCHAR(25),  
	country VARCHAR(25)  
);

\-- Sales Table

CREATE TABLE sales  
(  
	order\_id 	VARCHAR(10) PRIMARY KEY,  
	order\_date	DATE,  
	product\_id	VARCHAR(10) REFERENCES products(product\_id), \--FK  
	qty	INT,  
	discount\_percentage	FLOAT,  
	unit\_price FLOAT,	  
	store\_id VARCHAR(10) REFERENCES stores(store\_id) \--FK  
);

\-- Inventory Table  
CREATE TABLE inventory  
(  
	inventory\_id SERIAL PRIMARY KEY,  
	product\_id	VARCHAR(10) REFERENCES products(product\_id), \--FK  
	current\_stock 	INT,  
	reorder\_level INT  
);

SELECT 'All table created\!';

