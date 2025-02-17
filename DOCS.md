# E-Commerce API

<!--- If we have only one group/collection, then no need for the "ungrouped" heading -->

## Endpoints

- [Categories](#categories)
  1. [Create Category](#1-create-category)
     - [Error Response](#i-example-request-error-response)
     - [Successful Response](#ii-example-request-successful-response)
     - [Duplicate name value](#iii-example-request-duplicate-name-value)
  1. [Get Categories](#2-get-categories)
     - [Successful response](#i-example-request-successful-response)
  1. [Get Single Category](#3-get-single-category)
     - [Successful Response](#i-example-request-successful-response-1)
     - [Wrong ID](#ii-example-request-wrong-id)
  1. [Update Category](#4-update-category)
     - [Succsessful Response](#i-example-request-succsessful-response)
     - [Wrong ID](#ii-example-request-wrong-id-1)
  1. [Delete Category](#5-delete-category)
     - [Wrong ID](#i-example-request-wrong-id)
     - [Successful Response](#ii-example-request-successful-response-1)
- [Products](#products)
  1. [Upload Image](#1-upload-image)
     - [Successful Response](#i-example-request-successful-response-2)
     - [Uploaded File is not an image](#ii-example-request-uploaded-file-is-not-an-image)
     - [No File Uploaded Response](#iii-example-request-no-file-uploaded-response)
  1. [Create Product](#2-create-product)
     - [Successful Response](#i-example-request-successful-response-3)
     - [Default Values (Price, Discount, Image, Stock)](#ii-example-request-default-values-price-discount-image-stock)
     - [Empty Request/ Error Response](#iii-example-request-empty-request-error-response)
  1. [Get Products](#3-get-products)
     - [Successful Response](#i-example-request-successful-response-4)
  1. [Get Single Product](#4-get-single-product)
     - [Wrong ID](#i-example-request-wrong-id-1)
     - [Successful Response](#ii-example-request-successful-response-2)
  1. [Update Product](#5-update-product)
     - [Wrong ID](#i-example-request-wrong-id-2)
     - [Successful Response](#ii-example-request-successful-response-3)
  1. [Delete Product](#6-delete-product)
     - [Successful Response](#i-example-request-successful-response-5)
     - [Wrong ID](#ii-example-request-wrong-id-2)

---

## Categories

### 1. Create Category

**_Endpoint:_**

```bash
Method: POST
Type: RAW
URL: http://localhost:5000/api/v1/categories
```

**_Body:_**

```js
{
    "name": "Others"
}

```

**_More example Requests/Responses:_**

#### I. Example Request: Error Response

**_Body:_**

```js
{
}
```

#### I. Example Response: Error Response

```js
{
    "msg": "Please provide category name"
}
```

**_Status Code:_** 400

<br>

#### II. Example Request: Successful Response

**_Body:_**

```js
{
    "name":"Mobiles"
}
```

#### II. Example Response: Successful Response

```js
{
    "category": {
        "name": "Mobiles",
        "_id": "62a32ad155ae64dcf7d80b7c",
        "createdAt": "2022-06-10T11:28:17.469Z",
        "updatedAt": "2022-06-10T11:28:17.469Z",
        "__v": 0
    }
}
```

**_Status Code:_** 201

<br>

#### III. Example Request: Duplicate name value

**_Body:_**

```js
{
    "name": "Mobiles"
}

```

#### III. Example Response: Duplicate name value

```js
{
    "msg": "Duplicate value entered for name field, please choose another value"
}
```

**_Status Code:_** 400

<br>

### 2. Get Categories

**_Endpoint:_**

```bash
Method: GET
Type:
URL: http://localhost:5000/api/v1/categories
```

**_More example Requests/Responses:_**

#### I. Example Request: Successful response

**_Body: None_**

#### I. Example Response: Successful response

```js
{
    "categories": [
        {
            "_id": "62a32dad0e8281e47780986f",
            "name": "Mobiles",
            "createdAt": "2022-06-10T11:40:29.834Z",
            "updatedAt": "2022-06-10T11:40:29.834Z",
            "__v": 0
        },
        {
            "_id": "62a32dfb0e8281e477809873",
            "name": "Others",
            "createdAt": "2022-06-10T11:41:47.449Z",
            "updatedAt": "2022-06-10T11:41:47.449Z",
            "__v": 0
        }
    ],
    "count": 2
}
```

**_Status Code:_** 200

<br>

### 3. Get Single Category

**_Endpoint:_**

```bash
Method: GET
Type:
URL: http://localhost:5000/api/v1/categories/:id
```

**_URL variables:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a28bab5f4b07296885c78a |             |

**_More example Requests/Responses:_**

#### I. Example Request: Successful Response

**_Query:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a32dad0e8281e47780986f |             |

**_Body: None_**

#### I. Example Response: Successful Response

```js
{
    "category": {
        "_id": "62a32dad0e8281e47780986f",
        "name": "Mobiles",
        "createdAt": "2022-06-10T11:40:29.834Z",
        "updatedAt": "2022-06-10T11:40:29.834Z",
        "__v": 0
    }
}
```

**_Status Code:_** 200

<br>

#### II. Example Request: Wrong ID

**_Query:_**

| Key | Value | Description |
| --- | ----- | ----------- |
| id  | 1     |             |

**_Body: None_**

#### II. Example Response: Wrong ID

```js
{
    "msg": "No item found with id : 1"
}
```

**_Status Code:_** 404

<br>

### 4. Update Category

**_Endpoint:_**

```bash
Method: PATCH
Type: RAW
URL: http://localhost:5000/api/v1/categories/:id
```

**_URL variables:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a28bab5f4b07296885c78a |             |

**_Body:_**

```js
{
    "name":"Mobile Phones"
}
```

**_More example Requests/Responses:_**

#### I. Example Request: Succsessful Response

**_Query:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a32dad0e8281e47780986f |             |

**_Body:_**

```js
{
    "name":"Mobile Phones"
}
```

#### I. Example Response: Succsessful Response

```js
{
    "category": {
        "_id": "62a32dad0e8281e47780986f",
        "name": "Mobile Phones",
        "createdAt": "2022-06-10T11:40:29.834Z",
        "updatedAt": "2022-06-10T11:44:40.584Z",
        "__v": 0
    }
}
```

**_Status Code:_** 200

<br>

#### II. Example Request: Wrong ID

**_Query:_**

| Key | Value | Description |
| --- | ----- | ----------- |
| id  | 1     |             |

**_Body:_**

```js
{
    "name":"Mobile Phones"
}
```

#### II. Example Response: Wrong ID

```js
{
    "msg": "No item found with id : 1"
}
```

**_Status Code:_** 404

<br>

### 5. Delete Category

**_Endpoint:_**

```bash
Method: DELETE
Type:
URL: http://localhost:5000/api/v1/categories/:id
```

**_URL variables:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a28bab5f4b07296885c78a |             |

**_More example Requests/Responses:_**

#### I. Example Request: Wrong ID

**_Query:_**

| Key | Value | Description |
| --- | ----- | ----------- |
| id  | 1     |             |

**_Body: None_**

#### I. Example Response: Wrong ID

```js
{
    "msg": "No item found with id : 1"
}
```

**_Status Code:_** 404

<br>

#### II. Example Request: Successful Response

**_Query:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a32dad0e8281e47780986f |             |

**_Body: None_**

#### II. Example Response: Successful Response

```js
{
    "msg": "Category is deleted"
}
```

**_Status Code:_** 200

<br>

## Products

### 1. Upload Image

**_Endpoint:_**

```bash
Method: POST
Type: FORMDATA
URL: http://localhost:5000/api/v1/products/uploadImage
```

**_Body:_**

| Key   | Value | Description |
| ----- | ----- | ----------- |
| image |       |             |

**_More example Requests/Responses:_**

#### I. Example Request: Successful Response

**_Body:_**

| Key   | Value | Description |
| ----- | ----- | ----------- |
| image |       |             |

#### I. Example Response: Successful Response

```js
{
    "image": "/images/iphone-13-pro-family-hero.png"
}
```

**_Status Code:_** 200

<br>

#### II. Example Request: Uploaded File is not an image

**_Body:_**

| Key   | Value | Description |
| ----- | ----- | ----------- |
| image |       |             |

#### II. Example Response: Uploaded File is not an image

```js
{
    "msg": "Please upload an image"
}
```

**_Status Code:_** 400

<br>

#### III. Example Request: No File Uploaded Response

#### III. Example Response: No File Uploaded Response

```js
{
    "msg": "No file uploaded"
}
```

**_Status Code:_** 400

<br>

### 2. Create Product

**_Endpoint:_**

```bash
Method: POST
Type: RAW
URL: http://localhost:5000/api/v1/products
```

**_Body:_**

```js
    {
        "name": "Samsung S22",
        "description": "Lorem Ipsum is Lorem Ipsum but it is Lorem Ipsum",
        "category": "62a3358dfa70c8308b31810b"
    }
```

**_More example Requests/Responses:_**

#### I. Example Request: Successful Response

**_Body:_**

```js
    {
        "name": "Iphone",
        "description": "Lorem Ipsum is Lorem Ipsum but it is Lorem Ipsum",
        "price": 15000,
        "discount": 0,
        "gallery": [
            "/images/iphone-13-pro-family-hero.png"
        ],
        "stock": 100,
        "category": "62a3358dfa70c8308b31810b"
    }
```

#### I. Example Response: Successful Response

```js
{
    "product": {
        "name": "Iphone",
        "description": "Lorem Ipsum is Lorem Ipsum but it is Lorem Ipsum",
        "price": 15000,
        "discount": 0,
        "gallery": [
            "/images/iphone-13-pro-family-hero.png"
        ],
        "stock": 100,
        "category": "62a3358dfa70c8308b31810b",
        "_id": "62a335b9fa70c8308b31810d",
        "createdAt": "2022-06-10T12:14:49.641Z",
        "updatedAt": "2022-06-10T12:14:49.641Z",
        "__v": 0
    }
}
```

**_Status Code:_** 201

<br>

#### II. Example Request: Default Values (Price, Discount, Image, Stock)

**_Body:_**

```js
    {
        "name": "Samsung S22",
        "description": "Lorem Ipsum is Lorem Ipsum but it is Lorem Ipsum",
        "category": "62a3358dfa70c8308b31810b"
    }
```

#### II. Example Response: Default Values (Price, Discount, Image, Stock)

```js
{
    "product": {
        "name": "Samsung S22",
        "description": "Lorem Ipsum is Lorem Ipsum but it is Lorem Ipsum",
        "price": 0,
        "discount": 0,
        "gallery": [
            "/images/default-product-image.png"
        ],
        "stock": 20,
        "category": "62a3358dfa70c8308b31810b",
        "_id": "62a3368efa70c8308b318111",
        "createdAt": "2022-06-10T12:18:22.776Z",
        "updatedAt": "2022-06-10T12:18:22.776Z",
        "__v": 0
    }
}
```

**_Status Code:_** 201

<br>

#### III. Example Request: Empty Request/ Error Response

**_Body:_**

```js
{
}
```

#### III. Example Response: Empty Request/ Error Response

```js
{
    "msg": "Please provide product category,Please provide description,Please provide product name"
}
```

**_Status Code:_** 400

<br>

### 3. Get Products

**_Endpoint:_**

```bash
Method: GET
Type:
URL: http://localhost:5000/api/v1/products
```

**_More example Requests/Responses:_**

#### I. Example Request: Successful Response

**_Body: None_**

#### I. Example Response: Successful Response

```js
{
    "products": [
        {
            "_id": "62a335b9fa70c8308b31810d",
            "name": "Iphone",
            "description": "Lorem Ipsum is Lorem Ipsum but it is Lorem Ipsum",
            "price": 15000,
            "discount": 0,
            "gallery": [
                "/images/iphone-13-pro-family-hero.png"
            ],
            "stock": 100,
            "category": "62a3358dfa70c8308b31810b",
            "createdAt": "2022-06-10T12:14:49.641Z",
            "updatedAt": "2022-06-10T12:14:49.641Z",
            "__v": 0
        },
        {
            "_id": "62a3368efa70c8308b318111",
            "name": "Samsung S22",
            "description": "Lorem Ipsum is Lorem Ipsum but it is Lorem Ipsum",
            "price": 0,
            "discount": 0,
            "gallery": [
                "/images/default-product-image.png"
            ],
            "stock": 20,
            "category": "62a3358dfa70c8308b31810b",
            "createdAt": "2022-06-10T12:18:22.776Z",
            "updatedAt": "2022-06-10T12:18:22.776Z",
            "__v": 0
        }
    ],
    "count": 2
}
```

**_Status Code:_** 200

<br>

### 4. Get Single Product

**_Endpoint:_**

```bash
Method: GET
Type:
URL: http://localhost:5000/api/v1/products/:id
```

**_URL variables:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a3368efa70c8308b318111 |             |

**_More example Requests/Responses:_**

#### I. Example Request: Wrong ID

**_Query:_**

| Key | Value | Description |
| --- | ----- | ----------- |
| id  | 1     |             |

**_Body: None_**

#### I. Example Response: Wrong ID

```js
{
    "msg": "No item found with id : 1"
}
```

**_Status Code:_** 404

<br>

#### II. Example Request: Successful Response

**_Query:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a335b9fa70c8308b31810d |             |

**_Body: None_**

#### II. Example Response: Successful Response

```js
{
    "product": {
        "_id": "62a335b9fa70c8308b31810d",
        "name": "Iphone",
        "description": "Lorem Ipsum is Lorem Ipsum but it is Lorem Ipsum",
        "price": 15000,
        "discount": 0,
        "gallery": [
            "/images/iphone-13-pro-family-hero.png"
        ],
        "stock": 100,
        "category": "62a3358dfa70c8308b31810b",
        "createdAt": "2022-06-10T12:14:49.641Z",
        "updatedAt": "2022-06-10T12:14:49.641Z",
        "__v": 0
    }
}
```

**_Status Code:_** 200

<br>

### 5. Update Product

**_Endpoint:_**

```bash
Method: PATCH
Type: RAW
URL: http://localhost:5000/api/v1/products/:id
```

**_URL variables:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a3368efa70c8308b318111 |             |

**_Body:_**

```js
{
    "price": 14000
}
```

**_More example Requests/Responses:_**

#### I. Example Request: Wrong ID

**_Query:_**

| Key | Value | Description |
| --- | ----- | ----------- |
| id  | 1     |             |

**_Body:_**

```js
{
    "price": 14000
}
```

#### I. Example Response: Wrong ID

```js
{
    "msg": "No item found with id : 1"
}
```

**_Status Code:_** 404

<br>

#### II. Example Request: Successful Response

**_Query:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a335b9fa70c8308b31810d |             |

**_Body:_**

```js
{
    "price": 14000
}
```

#### II. Example Response: Successful Response

```js
{
    "product": {
        "_id": "62a335b9fa70c8308b31810d",
        "name": "Iphone",
        "description": "Lorem Ipsum is Lorem Ipsum but it is Lorem Ipsum",
        "price": 14000,
        "discount": 0,
        "gallery": [
            "/images/iphone-13-pro-family-hero.png"
        ],
        "stock": 100,
        "category": "62a3358dfa70c8308b31810b",
        "createdAt": "2022-06-10T12:14:49.641Z",
        "updatedAt": "2022-06-10T12:23:41.704Z",
        "__v": 0
    }
}
```

**_Status Code:_** 200

<br>

### 6. Delete Product

**_Endpoint:_**

```bash
Method: DELETE
Type:
URL: http://localhost:5000/api/v1/products/:id
```

**_URL variables:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a3368efa70c8308b318111 |             |

**_More example Requests/Responses:_**

#### I. Example Request: Successful Response

**_Query:_**

| Key | Value                    | Description |
| --- | ------------------------ | ----------- |
| id  | 62a335b9fa70c8308b31810d |             |

**_Body: None_**

#### I. Example Response: Successful Response

```js
{
    "msg": "Product removed"
}
```

**_Status Code:_** 200

<br>

#### II. Example Request: Wrong ID

**_Query:_**

| Key | Value | Description |
| --- | ----- | ----------- |
| id  | 1     |             |

**_Body: None_**

#### II. Example Response: Wrong ID

```js
{
    "msg": "No item found with id : 1"
}
```

**_Status Code:_** 404

<br>

---

[Back to top](#e-commerce-api)

> Generated at 2022-06-10 14:54:58 by [docgen](https://github.com/thedevsaddam/docgen)
