# Order

~~~js
// POST /orders

{
  products: [{
    productId: 'abc',
    title: 'Foobar',
    quantity: 3,
    price: 12.56
  }, {
    productId: 'xyz',
    title: 'Foobaz',
    quantity: 1,
    price: 7.99
  }]
}
~~~

# Catalog

~~~js
// GET /products

{
  products: [{
    productId: 'abc',
    title: 'Foobar',
    price: 12.56
  }, {
    productId: 'xyz',
    title: 'Foobaz',
    price: 7.99
  }]
}
~~~

# Cart

~~~js
// POST /carts{/:cartId}

// Request:
{
  products: [{
    productId: 'abc',
    quantity: 1,
    title: 'Foobar',
    price: 12.56 
  }]
}

// Response:
{
  cartId: '375cffch9g8w4hz',
  products: [{
    productId: 'abc',
    quantity: 1,
    title: 'Foobar',
    price: 12.56 
  }]
}
~~~
