# cassandra

docker run --name cassandra --network cassandra -d cassandra:latest
#docker run -it --network cassandra --rm cassandra cqlsh cassandra
docker exec -it cassandra bash

docker network create cassandra

-- Create a keyspace
CREATE KEYSPACE IF NOT EXISTS store WITH REPLICATION = { 'class' : 'SimpleStrategy', 'replication_factor' : '1' };

-- Create a table
CREATE TABLE IF NOT EXISTS store.shopping_cart (
userid text PRIMARY KEY,
item_count int,
last_update_timestamp timestamp
);

-- Insert some data
INSERT INTO store.shopping_cart
(userid, item_count, last_update_timestamp)
VALUES ('9876', 2, toTimeStamp(now()));
INSERT INTO store.shopping_cart
(userid, item_count, last_update_timestamp)
VALUES ('1234', 5, toTimeStamp(now()));

 SELECT * FROM store.shopping_cart;
