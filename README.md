
<h1 align="center">nestjs microservices amqp</h1>
<p align="center">backend containerized</p>
<p align="center">
    <img src="https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=fff&style=for-the-badge" alt="TypeScript Badge">
    <img src="https://img.shields.io/badge/AMQP-0D597F?logo=rabbitmq&logoColor=fff&style=for-the-badge" alt="AMQP Badge">
    <img src="https://img.shields.io/badge/PostgreSQL-336791?logo=postgresql&logoColor=fff&style=for-the-badge" alt="PostgreSQL Badge">
    <img src="https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=fff&style=for-the-badge" alt="Docker Badge">
</p>



## Dependencies
```
** Ensure you have nodejs installed

Install pnpm
$ npm install -g pnpm
$ pnpm install
```

## amqp
Create a free server here:
[Link amqp platform](https://customer.cloudamqp.com/instance/)
where you will be able to get an URL, example (amqps://username:password-QQ@hostname/vhost)

## Container
```
Go to the Docker folder and build all the images and start the containers, we used simple passwords for semplcity
$  (cd Docker && docker-compose up --build)
$  docker-compose -f docker/docker-compose.yml up --build
```


## **Configure Environment Variables**  
   Create a `.env` file at the root of each microservice project and add the following environment variables:

    ```
    RABBITMQ_URL=amqps://username:password-QQ@hostname/vhost
    SERVICE_NAME=

    DATABASE_HOST=
    DATABASE_USERNAME=
    DATABASE_PASSWORD=
    DATABASE_NAME=
    DATABASE_PORT=5432
    ```


## Database:
You *must* manually add books and customers to the book and customer databases, respectively.
Execute this 'SQL scripts', here the path:

   - For books:
     ```sql
     cd ./books/book/init/init.book.sql
     ```
   - For customers:
     ```sql
     cd ./customers/customer/init/init.customer.sql
     ```




## Endpoints
Now you are able to performs this 'curls'

```
curl -X 'POST' \
  'http://localhost:3001/order' \
  -H 'accept: */*' \
  -H 'Content-Type: application/json' \
  -d '{
  "bookId": "02044837-b360-4d6b-97a6-334eef93fdcd",
  "customerId": "01f4acc3-dd65-46ce-8c5a-ef3ca363cb6d",
  "quantity": 5,
  "totalPrice": 100
}'
```

```
### Get single order

curl -X 'GET' \
  'http://localhost:3001/order/d4da6139-2960-458d-9cd3-6e7c0a4e3037' \
  -H 'accept: */*'
```

```
### Increase stock by quantity

curl -X 'PATCH' \
  'http://localhost:3002/book/02044837-b360-4d6b-97a6-334eef93fdcd' \
  -H 'accept: */*' \
  -H 'Content-Type: application/json' \
  -d '{
  "quantity": 5
}'
```

```
### Delete a single order

curl -X 'DELETE' \
  'http://localhost:3001/order/d453848b-a093-4c2f-96bb-0e13d80140b8' \
  -H 'accept: */*'
```

**Swagger endpoints**

```
Swaggers combined:
http://localhost:4000/docs/#/
```


```
order:
http://localhost:3001/api#/
http://localhost:3001/api-json
```

```
book:
http://localhost:3002/api#/
http://localhost:3002/api-json
```

```
customer:
http://localhost:3004/api#/
http://localhost:3004/api-json
```

