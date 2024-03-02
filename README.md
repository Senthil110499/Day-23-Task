
# **_MongoDB Task_**

## **_MongoDB_**

+ MongoDB is a NoSQL, document-oriented database that provides a flexible and scalable way to store, retrieve, and manage data.
+ It is particularly well-suited for handling large amounts of unstructured or semi-structured data.
+ MongoDB stores data in flexible, JSON-like documents, allowing for easy modification and adaptation of the database schema.

## **_Key Features_**

+ Ad-hoc queries for optimized, real-time analytics
+ Indexing appropriately for better query executions
+ Replication for better data availability and stability
+ Sharding
+ Load balancing

## **_Technology Used_**

+ mongoDB

## To view the Document file :

- Click on the `MongoDB-Task.docx` file above to `Download` and view the file in which I've attached the `Screenshot` below each `Query` respectively.

## **_MongoDB 10 Questions & Queries_**

1. Find all the information about each products
> db.products.find();

2. Find the product price which are between 400 to 800
> db.products.find({product_price:{$ gt:400,$ lt:800}});

3. Find the product price which are not between 400 to 600
> db.products.find({product_price:{$ not:{$ gte:400,$ lte:600}}});

4. List the four product which are greater than 500 in price 
> db.products.find({product_price:{$ gte:500}}).limit(4);

5. Find the product name and product material of each products
> db.products.find({},{product_name:1,product_material:1});

6. Find the product with a row id of 10
> db.products.find({id:"10"});

7. Find only the product name and product material
> db.products.find({},{product_name:1,product_material:1,_id:0});

8. Find all products which contain the value of soft in product material
> db.products.find({product_material:'soft'});

9. Find products which contain product color indigo  and product price 492.00
> db.products.find({$or:[{product_color:'indigo'},{product_price:492}]});

10. Delete the products which product price value are same
> db.products.aggregate([{$ group:{_id:'$ product_price',count:{$ sum:1}}},{$ match:{count:{$ gt:1}}}])
.forEach((e)=>{db.products.deleteMany({product_price:e._id})});
