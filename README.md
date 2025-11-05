## install dep 


```sh 
npm install 
```
## start server 
PORT=3000 npm start

## run postgers server

```sh 
docker compose up 
```


## install postgeres-client
```sh 
sudo apt-get install postgresql-client
```
## create database 
createdb study-sync   -h localhost  -U admin 
## connect to database 
```sh
psql postgresql://admin:admin123@localhost:5432/study-sync
```


## Create Schema
```sh
psql study-sync < db/sql/schema.sql -h localhost -U postgres
```
## Import Data
```sh
psql study-sync < db/sql/seed.sql -h localhost -U postgres
```

## Verify Data

```sh
psql postgresql://admin:admin123@localhost:5432/study-sync
```


# aws-create-web
