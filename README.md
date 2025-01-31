
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
$ pnpm add @nestjs/microservices amqplib amqp-connection-manager @nestjs/typeorm typeorm pg axios
```
## amqp
Create a free server here:
[Link amqp platform](https://customer.cloudamqp.com/instance/)

## Container
```
$  (cd Docker && docker-compose up --build)
$  docker-compose -f docker/docker-compose.yml up --build
```

## Swagger

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



## **Configure Environment Variables**  
   Create a `.env` file at the root of each project and add the following environment variables:

    ```
    RABBITMQ_URL=
    DATABASE_HOST=
    DATABASE_USERNAME=
    DATABASE_PASSWORD=
    DATABASE_NAME=
    DATABASE_PORT=
    ```

## Endpoints
```
POST http://localhost:3001/order

You must provide the following data in the request body:

```json
{
  "bookId": "book ID",
  "customerId": "customer ID",
  "quantity": 2,
  "totalPrice": 4000
}

```
Note:
- You must manually add books and customers to the book and customer databases, respectively.
- Then, collect the IDs of the created books and customers to use in the request body.
- The bookId parameter corresponds to the ID of the book you want to order, the customerId parameter corresponds to the ID of the customer for whom you are placing the order, and the quantity and totalPrice parameters indicate the quantity and total price of the ordered book.

```
DELETE http://localhost:3001/order/:id
```