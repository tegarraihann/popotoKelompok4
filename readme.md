#Factual

This example is a complete application using a restaurant dataset sample provided with courtesy of [Factual](https://www.factual.com/) modeled as a graph in [Neo4j](https://neo4j.com/) hosted on [GrapheneDB](https://www.graphenedb.com/) and shows most of the features available in [Popoto.js](http://popotojs.com/).

[![Main screenshot](https://nhogs.github.io/popoto-examples/factual/screen/main.png "Main screenshot")](https://nhogs.github.io/popoto-examples/factual/index.html)



*File csv bisa diunduh didalam folder csvnya

Silahkan ikuti perintah berikut untuk load file csv kedalam neo4jnya, dan membuat relasi dari Label Coffeshop(cs) ke Label Alamat(a) dan dipisahkan dengan query merge. Yang dimana relasinya adalaha Coffe Shop yang BERADA_DI Alamat:

1. Load CSV 
LOAD CSV WITH HEADERS FROM "file:///coffee_shop.csv" AS row
MERGE (cs:Coffee {id_cs: row.id_cs})
ON CREATE SET cs.name = row.name,
              cs.rating = row.rating,
              cs.review_date = row.review_date,
              cs.review = row.review,
              cs.price = row.price,
              cs.long = row.long,
              cs.lat = row.lat
MERGE (a:Alamat {alamat: row.alamat})
MERGE (cs)-[r:BERADA_DI]->(a);



