# RevTap: Full-stack Developer

* Create a [Feathers](https://feathersjs.com/) server.
* Create CRUD [service](https://docs.feathersjs.com/api/services.html) for `customers` and `orders` using [MongoDB](https://www.mongodb.com/) and [Mongoose](https://github.com/feathersjs-ecosystem/feathers-mongoose).
* Use the following schema for the models.

```javascript
// customers
{
  firstName: String,
  lastName: String,
  email: String,
  created: Date,
}

// orders
{
  customer: ObjectId,  // foreign-key to customers._id
  product: String,  // product-name
  quantity: Number,
  price: Number,
}

```

* Create a [hook](https://docs.feathersjs.com/api/hooks.html) on `customers` service to populate all the related orders.
```javascript
// GET /customers
// for each customer
{
  firstName: '...',
  lastName: '...',
  email: '...',
  created: '...',
  orders: [/* all the orders for this customer */]
}
```

* Create a new service, `analytics` which [aggregates](https://docs.mongodb.com/manual/aggregation/) data on orders collection to find total orders count and total order price for each day of orders.

* You can use [$dayOfMonth](https://docs.mongodb.com/manual/reference/operator/aggregation/dayOfMonth/) with [$group](https://docs.mongodb.com/manual/reference/operator/aggregation/group/) to get this. A sample response from the `analytics` service:

```javascript
// GET /analytics
[
  {
    day: 1,
    ordersCount: 10,
    totalPrice: 123.45,
  }
  ...
  {
    day: 30,
    ordersCount: 30,
    totalPrice: 1337,
   }
 ]
```

* Create a simple [React](https://reactjs.org/) application to list all the customers, orders and analytics in a paginated table.
* Create and share a GitHub repository for the server and app.

Listing the data is enough for the React application. Feel free to use any third-party libraries for the React application.
