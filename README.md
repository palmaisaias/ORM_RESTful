
This project is a RESTful API built using Flask, Flask-SQLAlchemy, and Flask-Marshmallow. The API manages customers, orders, and products, implementing CRUD operations for each entity.

**Installation**

To install the necessary dependencies, run:
```
pip install -r requirements.txt
```

**Configuration**

The API uses a MySQL database. Update the database URI in the `app.py` file to match your database configuration:

```python
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql+mysqlconnector://root:@localhost/orm_db'
```

## Models

### Customer

A customer has the following fields:
- `id`: Primary key
- `customer_name`: String (200)
- `email`: String (300)
- `phone`: String (16)

### Orders

An order has the following fields:
- `id`: Primary key
- `order_date`: Date
- `customer_id`: Foreign key to Customer
- `customer`: Relationship to Customer
- `products`: Many-to-many relationship with Products through the `order_products` association table

### Products

A product has the following fields:
- `id`: Primary key
- `product_name`: String (200)
- `price`: Float
- `orders`: Many-to-many relationship with Orders through the `order_products` association table

## API Endpoints

### Customers

- **Get all customers**
  ```
  GET /customers
  ```

- **Get a specific customer by ID**
  ```
  GET /customers/<int:id>
  ```

- **Create a new customer**
  ```
  POST /customers
  ```

- **Update an existing customer by ID**
  ```
  PUT /customers/<int:id>
  ```

- **Delete a customer by ID**
  ```
  DELETE /customers/<int:id>
  ```

### Orders

- **Get all orders**
  ```
  GET /orders
  ```

- **Get a specific order by ID**
  ```
  GET /orders/<int:id>
  ```

- **Create a new order**
  ```
  POST /orders
  ```

- **Update an existing order by ID**
  ```
  PUT /orders/<int:id>
  ```

- **Delete an order by ID**
  ```
  DELETE /orders/<int:id>
  ```

### Products

- **Get all products**
  ```
  GET /products
  ```

- **Get a specific product by ID**
  ```
  GET /products/<int:id>
  ```

- **Create a new product**
  ```
  POST /products
  ```

- **Update an existing product by ID**
  ```
  PUT /products/<int:id>
  ```

- **Delete a product by ID**
  ```
  DELETE /products/<int:id>
  ```

## Running the Application

To run the application, execute:

```
python app.py
```

The application will be available at `http://localhost:5000`.
