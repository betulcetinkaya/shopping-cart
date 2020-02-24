# Project Title

Shopping Cart

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

```
Docker
```

### Installing
You need to clone the repositories with submodules included.

```
git clone --recursive https://github.com/betulcetinkaya/trendyol-case.git
```

## Running the tests
Before running the tests you need to run assignment-db for repository tests (See deployment for notes on how to deploy a module). You need to move into the base package of the submodules(repositories) and then you can run the following command.

```
mvn clean test
```

## Deployment

To run all the services and platforms apply the following steps.

1. Move into "docker-deployment" folder.
2. Run "docker-compose up -d" command

To run a single service
1. Move into src/main/resources/docker folder of a specific submodule (repository).
2. Run "docker-compose up -d" command

## Sample Use Case

Before you start make sure that all the services registered to the service-registry.
1. Go to the service-registry ui via http://localhost:8761/
2. Following services should exist in the instance list. 
```
API-GATEWAY	
CART-SERVICE
DELIVERY-SERVICE
DISCOUNT-SERVICE
PRODUCT-SERVICE
```
3. Some initial data will be loaded in the MongoDB.(Initial products, categories, etc.) You can use shopping cart apis with initial data.
 
 Current shopping cart will be affected by the api calls and will be respond. 

### Add item to the shopping cart.
```
curl -X POST \
  http://localhost:8080/api/cart/shopping-carts/1/items \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
	"productId": 2,
	"quantity": 5
}'
```

### Add more item with another productId.
```
curl -X POST \
  http://localhost:8080/api/cart/shopping-carts/1/items \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
	"productId": 3,
	"quantity": 2
}'
```
### Apply a coupon.
```
curl -X PUT \
  http://localhost:8080/api/cart/shopping-carts/1/coupon/1 \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache'
```
### Calculate delivery cost and find it in the response body.
```
curl -X PUT \
  http://localhost:8080/api/cart/shopping-carts/1/delivery/2 \
  -H 'cache-control: no-cache'
```  
4. You can also create your own data with following apis.

### Create a product.
```
curl -X POST \
  http://localhost:8080/api/product/products \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
    "title": "Product 4",
    "category": {
      "id": 1
    },
    "price": 50.75
  }'
```  
### Create a category.
```
curl -X POST \
  http://localhost:8080/api/product/categories \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
    "title": "Category 3",
    "parentId": 1
}'
```
### Create a campaign.
```
curl -X POST \
  http://localhost:8080/api/discount/campaigns \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
    "categoryId": "1",
    "discount": 25,
    "minQuantity": 5,
    "discountType": "RATE"
}'
```
### Create a coupon.
```
curl -X POST \
  http://localhost:8080/api/discount/coupons \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
    "minAmount": 500,
    "discount": 100,
    "discountType": "AMOUNT"
}'
```
### Create a delivery.
```
curl -X POST \
  http://localhost:8080/api/delivery/deliveries \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
    "costPerDelivery": 5,
    "costPerProduct": 2,
    "fixedCost": 4
  }'
```

## Built With

* [Jdk11]
* [Docker]
* [Maven]
* [Spring]
* [MongoDB]

## Authors

* **Betül Çetinkaya** - *Initial work* - (https://github.com/betulcetinkaya)
