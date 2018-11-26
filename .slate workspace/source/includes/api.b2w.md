# B2W Marketplace

## Authentication and data format

### Authentication

All calls to services available on the SkyHub - API must be authenticated from the user 's email, access token and accountmanager. This information should be sent in the header (header) of each request, as follows:

* Authentication headers

* X-User-Email: user_user

* X-Api-Key: token_de_integracao

* X-Accountmanager-Key: token_account

Note: The X-Accountmanager-Key must be internal to your code, it is not necessary to request this information from your customer, since it is unique and already available with the test account.

If you do not already have this information, please contact our support.

### Data format

When exchanging messages with SkyHub - API, the JavaScript Object Notation (JSON) standard will be used. Therefore, each request must contain the appropriate values in the Accept and Content-Type (application / json) headers.

* Data format headers

* Accept: application / json

* Content-Type: application / json

### Encoding (charset)

The data sent (via POST or PUT) must conform to the UTF-8 charset.

If a different encoding is used, an unsupported data type error (HTTP Status 415) is returned.

IMPORTANT - Even if the "Accept" header indicates UTF-8 charset usage, if the body data is not in the correct encoding, HTTP 415 will also be returned.

## Return codes (HTTP status)

### SkyHub uses the default group of HTTP statuses to indicate whether a request was successful or not. In general:

HTTP 2xx Codes: Indicate that the request was successful.

HTTP Codes 4xx: indicate that the request contains some incorrect information - incorrect access data, absence of a required field, etc.

HTTP 5xx Codes: Indicates an error on SkyHub's servers. These are rare, and if you receive this code, you should contact our support.

### Errors

Whenever an error occurs, the API returns in the body of the message a JSON with an error message according to the format below:

{erro: "error message"};

### Status HTTP

The most commonly used HTTP statuses are:

Status              | Description 
--------------------|------------------------------------------------
**200**             | Success - the request has been processed successfully.
**201**             | Created - the request was successfully processed and resulted in a new feature created.
**204**             | No content - the request has been successfully processed and there is no additional content in the response.
**400**             | Malformed request - the request does not conform to the expected format. Check the JSON (body) being sent.
**401**             | Not authenticated - Authentication data is incorrect. Check the header of the request for the e-mail and the token.
**403**             | Unauthorized - you are trying to access a resource that is not allowed.
**404**             | Not found - you are trying to access a resource that does not exist does not exist on SkyHub.
**406**             | Format Not Accepted - SkyHub does not support the data format specified in the header (Accept).
**415**             | Media format not supported - SkyHub can not process the uploaded data by its format. Be sure to use the UTF-8 charset (both in the "Content-Type" header and in the request's own body).
**422**             | Semantic error - although the format of the request is correct, the data hurt some business rule (for example: invalid transition from request status).
**429**             | Exceeded request limit - you have made more requests than allowed in a given resource.
**500 or 502**      | Internal Error - An error occurred on the SkyHub server when attempting to process the request.
**503**             | Service Unavailable - The SkyHub API is temporarily down.
**504**             | Timeout - The request took a long time and can not be processed.

## Requisition limit

To ensure good API performance, integrations will be subject to a throttling threshold.

The request limit on Skyhub is per endpoint and per API, so each API has the following limit:

Products = 9 Request per Second

Orders = 9 Request per Second

The other endpoints have a limit of 1 request per second.

If the integration exceeds this limit, HTTP error 429 will be returned.

It is important that when you receive the first HTTP 429 error your integration will wait for a new request window to avoid incurring the same error.

## Attributes

### [POST] Create an attribute

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/attributes' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \ 
--data {
  "attribute": {
    "name": "att_name", #Internal attribute identifier
    "label": "Atributo Exemplo", #Attribute Label. This is the string that will be displayed on the SkyHub portal.
    "options": [ #Optional field. Lists the options of the attribute, if it is of type "select". Example, ["red", "blue", "white"] for a "Color" attribute.
      "foo",
      "foo",
      "foo"
    ]
  }
}

```

<aside class="notice">https://api.skyhub.com.br/attributes</aside>

Creater a new product attribute.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [PUT] Update an attribute

```shell

curl --request PUT \ 
--url 'https://api.skyhub.com.br/attributes/att_name' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \ 
--data {
  "attribute": {
    "name": "att_name", #Internal attribute identifier
    "label": "Atributo Exemplo", #Attribute Label. This is the string that will be displayed on the SkyHub portal.
    "options": [ #Optional field. Lists the options of the attribute, if it is of type "select". Example, ["red", "blue", "white"] for a "Color" attribute.
      "foo",
      "foo",
      "foo"
    ]
  }
}

```

<aside class="notice">https://api.skyhub.com.br/atributes/{name}</aside>

Updates an existing attribute.

Path Parameters         | Type      | Required          | Description                           | Example
------------------------|-----------|-------------------|---------------------------------------|----------------------
**name**                | string    | required          | Attribute internal name (code)        | attribute_name

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

## Categories

### [GET] List Categories

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/categories' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/categories</aside>

Lists all categories registered on SkyHub.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [POST] Create a category

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/categories' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "category": {
    "code": "category001", #Internal Category Identification Code
    "name": "eletrónicos > celulares > fone de ouvido" #Category name. The category name in skyhub should be the joining of all hierarchy category names separated by a ">". Example, "Shoes> Women> Low top trainers"
  }
}

```

<aside class="notice">https://api.skyhub.com.br/categories</aside>

Creates a category on SkyHub.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [PUT] Update Category

```shell

curl --request PUT \ 
--url 'https://api.skyhub.com.br/categories/category001' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \ 
--data {
  "category": {
    "code": "category001",
    "name": "eletrónicos > celulares > fone de ouvido" #Category name. The category name in skyhub should be the joining of all hierarchy category names separated by a ">". Example, "Shoes> Women> Low top trainers"
  }
}

```

<aside class="notice">https://api.skyhub.com.br/categories/{code}</aside>

Updates only one category on SkyHub by the category code.

Path Parameters         | Type      | Required          | Description                           | Example
------------------------|-----------|-------------------|---------------------------------------|----------------------
**code**                | string    | required          | Category code to update               | category001

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [DEL] Delete Category

```shell

curl --request DELETE \ 
--url 'https://api.skyhub.com.br/categories/category001' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "category": {
    "code": "category001",
    "name": "eletrónicos > celulares > fone de ouvido"
  }
}

```

<aside class="notice">https://api.skyhub.com.br/categories/{code}</aside>

Deletes only one category on SkyHub by the category code.

Path Parameters         | Type      | Required          | Description                           | Example
------------------------|-----------|-------------------|---------------------------------------|----------------------
**code**                | string    | required          | Category code to remove               | category001

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

## Freights

### [GET] Return the freights history

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/freights' \ 
--header 'accept: application/json' \
--header 'content-type: application/json' \
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/freights</aside>

Lists all freights.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

## Orders

### [GET] List orders

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/orders?per_page=100&page=2' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/orders</aside>

Lists all orders registered on SkyHub.

Query Parameters            | Type       | Required          | Description                                          | Example
----------------------------|------------|-------------------|------------------------------------------------------|----------------------
**page**                    | integer    | optional          | Request requisition page                             | 1
**per_page**                | integer    | optional          | Number of orders per page (maximum = 100)            | 30
**filters(sale_systems)[]** | string     | optional          | Filter for marketplace of origin of orders           | marketplace
**filters(statuses)[]**     | string     | optional          | Filter for order status (status identification code) | pending

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [GET] Returns a specific order

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/orders/Lojas Americanas-266580617301' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/orders/{code}</aside>

Returns only one order.

Path Parameters         | Type      | Required          | Description                           | Example
------------------------|-----------|-------------------|---------------------------------------|----------------------
**code**                | string    | required          | Identification code of the order. The order ID may contain space. It is important to ensure that the final URL will encode the spaces correctly. Example, an order with code "Lojas Americanas-001" should have the url in the format: GET / orders / Lojas% 20Americanas-001        | Marketplace-000000001

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [POST] Invoice

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/invoice' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "status": "payment_received", #Status identification code. If not specified, the order status will not change
  "invoice": { #NFe Information
    "key": "99999999999999999999999999999999999999999999" #NFe Key
  }
}

```

<aside class="notice">https://api.skyhub.com.br/orders/{code}/invoice</aside>

Updates an order with invoice information.

Path Parameters         | Type      | Required          | Description                           | Example
------------------------|-----------|-------------------|---------------------------------------|----------------------
**code**                | string    | required          | Identification code of the order. The order ID may contain space. It is important to ensure that the final URL will encode the spaces correctly. Example, an order with code "Lojas Americanas-001" should have the url in the format: POST / orders / Lojas% 20Americanas-001 / invoice        | Marketplace-000000001

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [POST] Cancel an order

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/cancel' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "status": "order_canceled"
}

```

<aside class="notice">https://api.skyhub.com.br/orders/{code}/cancel</aside>

Updates an order with the cancelation data.

Path Parameters         | Type      | Required          | Description                           | Example
------------------------|-----------|-------------------|---------------------------------------|----------------------
**code**                | string    | required          | Identification code of the order. The order ID may contain space. It is important to ensure that the final URL will encode the spaces correctly. Example, an order with code "Lojas Americanas-001" should have the url in the format: POST / orders / Lojas% 20Americanas-001 / cancel        | Marketplace-000000001

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [POST] Confirm Delivery

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/delivery' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "status": "complete"
}

```

<aside class="notice">https://api.skyhub.com.br/orders/{code}/delivery</aside>

Updates an order as delivered on SkyHub.

Path Parameters         | Type      | Required          | Description                           | Example
------------------------|-----------|-------------------|---------------------------------------|----------------------
**code**                | string    | required          | Identification code of the order. The order ID may contain space. It is important to ensure that the final URL will encode the spaces correctly. Example, an order with code "Lojas Americanas-001" should have the url in the format: POST / orders / Lojas% 20Americanas-001 / delivery        | Marketplace-000000001

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [POST] Send delivery data

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/shipments' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "status": "order_shipped",
  "shipment": {
    "code": "Lojas Americanas-266065081401",
    "items": [
      {
        "sku": "foo",
        "qty": 1
      }
    ],
    "track": {
      "code": "BR1321830198302DR",
      "carrier": "Correios",
      "method": "SEDEX",
      "url": "www.correios.com.br"
    }
  }
}

```

<aside class="notice">https://api.skyhub.com.br/orders/{code}/shipments</aside>

Updates an order with the tracking code data and the method of shipping of the transporter (B2W accepts at maximum 200 characters in the URL of tracking).

Path Parameters         | Type      | Required          | Description                           | Example
------------------------|-----------|-------------------|---------------------------------------|----------------------
**code**                | string    | required          | Identification code of the order. The order ID may contain space. It is important to ensure that the final URL will encode the spaces correctly. Example, an order with code "Lojas Americanas-001" should have the url in the format: POST / orders / Lojas% 20Americanas-001 / shipments        | Marketplace-000000001

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [GET] Gets shipping label

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/shipment_labels' \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/orders/{code}/shipments_labels</aside>

Obtains the label of an order that had the freight calculated via B2W deliveries.

Path Parameters         | Type      | Required          | Description                           | Example
------------------------|-----------|-------------------|---------------------------------------|----------------------
**code**                | string    | required          | Identification code of the order. The order ID may contain space. It is important to ensure that the final URL will encode the spaces correctly. Example, an order with code "Lojas Americanas-001" should have the url in the format: GET / orders / Lojas% 20Americanas-001        | Marketplace-000000001

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/pdf
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [POST] Transport exception

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/orders/Lojas Americanas-266065081401/shipment_exception' \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "shipment_exception": {
    "occurrence_date": "2012-10-06T04:13:00-03:00",
    "observation": "Observação da Exceção de transporte"
  }
}

```

<aside class="notice">https://api.skyhub.com.br/orders/{code}/shipments_exception</aside>

Transport exception.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/pdf
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

## PLP

### [GET] List PLP’s

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/shipments/b2w/' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/shipments/b2w</aside>

Function that allows to check in the API all grouped PLPs. In the return it will be possible to verify the id of the PLP and the inserted orders in each group.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [POST] Grouping Orders in a PLP

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/shipments/b2w/' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "order_remote_codes": [
    "265358194401",
    "265358194401",
    "265358194401"
  ]
}

```

<aside class="notice">https://api.skyhub.com.br/shipments/b2w</aside>

Return orders to group, just 20 orders for page.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [DEL] Ungroup PLP

```shell

curl --request DELETE \ 
--url 'https://api.skyhub.com.br/shipments/b2w/' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "plp_id": "14"
}

```

<aside class="notice">https://api.skyhub.com.br/shipments/b2w</aside>

Basically the opposite of that last operation.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [GET] Recover PLP PDF

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/shipments/b2w/view?plp_id=14' \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/shipments/b2w/view?plp_id={CODE}</aside>

First you need to group the PLPs, you will receive a id and use it in this function. If you want to receive the datas in json format just use the Header Accept: application/pdf.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/pdf
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [GET] Order list apt for grouping

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/shipments/b2w/to_group' \ 
--header 'accept: application/pdf' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/shipments/b2w/to_group</aside>

Return the PLP ID, with the ID will be necessary recover the PLP.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/pdf
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

## Products 

### [GET] Returns the products registered in the skyhub

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/products?page=1&per_page=100' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/products</aside>

List all products registered on SkyHub.

Query Parameters            | Type       | Required          | Description                | Example
----------------------------|------------|-------------------|----------------------------|----------------------
**status**                  | string    | optional           |                            | foo

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [GET] Returns a specific product in the skyhub

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/products/0927@wangxx' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/products/{sku}</aside>

Get only one product according with the SKU ID.

Path Parameters            | Type       | Required          | Description                | Example
---------------------------|------------|-------------------|----------------------------|----------------------
**sku**                    | string     | required          |                            | 	sku123

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [POST] Create a product in the SkyHub

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/products' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \ 
--data {
  "product": {
            "sku": "15077",
            "name": "Fonte De Alimentação Digital Tipo Yihua - Yaxun Ps-1502dd - 130V",
            "description": "Ideal para a manutenção em equipamentos eletrônicos!<br/>Proporciona tranquilidade e precisão a seu usuário.<br/>Possui display duplo para controle de tensão e corrente Knob para ajuste da corrente de proteção.<br/>Um Knob com tensões pré-determinadas com cinco invariáveis e uma variável<br/>Proteção contra sobrecarga.<br/>Proteção contra inversão de polaridade.<br/>Refrigerado por dissipador.<br/>Sistema de segurança com corte de alimentação automático.<br/>Quando a corrente atinge seu pico, a fonte corta sua alimentação.<br/>A Fonte de Alimentação PS-1502DD é uma peça indispensável na bancada de quem deseja trabalhar corretamente sem necessidade de improvisos ou invenções na hora de reparar seus equipamentos.<br/>Além de ser um produto de alta precisão que fornece alimentação contínua, é também, muito leve e robusta, sendo muito prática e durável para os reparos do dia a dia.<br/>Conta ainda com sistema de segurança, um tipo de sistema que possibilita a fonte controlar a corrente máxima que deve fornecer, possibilitando ajustes entre 0.6 e 2A.<br/>uando o limite estipulado for alcançando a fonte corta automaticamente a alimentação para evitar a ocorrência de danos aos equipamentos que estão sendo testados.<br/>A fonte vem equipada com dois displays digitais de LED, o da esquerda indicada a corrente de proteção e a corrente de consumo, enquanto o da direita demonstra tensão ajustada.<br/>Para sua regulagem, ela conta com 4 Knobs de ajuste (potenciômetros) que lhe auxiliam no perfeito ajuste de tensão e corrente que circula até o seu equipamento.<br/>", #Product Sku
            "status": "enabled",
            "removed": false,
            "price": 255555,
            "promotional_price": 1690.90,
            "cost": null, #Product Cost
            "weight": 1.6,
            "height": 25,
            "width": 13,
            "length": 20,
            "brand": "Yaxun",
            "ean": null,
            "nbm": "84733011",
            "categories": [ #Categories
                {
                    "code": "MLB30167",
                    "name": "Agro, Indústria e Comércio > Agro, Indústria e Comércio > Indústria Agrícola > Matéria Prima > Mudas"
                }
            ],
            "images": [
                "http://loja.multtechinfo.com.br/imagenslw/SB1_1515243081944.jpg",
                "https://www.bluecell.com.br/image/cache/catalog/foun160-600x600.jpg",
                "https://static3.tcdn.com.br/img/img_prod/375576/carregador_fonte_parede_maxx_733_3_usb_pmcell_qualcomm_3_0_9622_2_20170908094039.jpg"
            ],
            "specifications": [ #Specifications
                {
                    "key": "VOLTAGEM",
                    "value": "220v"
                }
            ],
            "variations": [ #Variations
                {
                    "sku": "F0011-220",
                    "qty": 500,
                    "ean": "6959745160286",
                    "images": [
                      "http://loja.multtechinfo.com.br/imagenslw/SB1_1515243081944.jpg",
                "https://www.bluecell.com.br/image/cache/catalog/foun160-600x600.jpg",
                "https://static3.tcdn.com.br/img/img_prod/375576/carregador_fonte_parede_maxx_733_3_usb_pmcell_qualcomm_3_0_9622_2_20170908094039.jpg"
                    ],
                    "specifications": [ #Specifications
                        {
                            "key": "VOLTAGEM",
                            "value": "220v"
                        }
                    ]
                }
            ],
            "variation_attributes": [
              "VOLTAGEM"
            ]
  }
}

```

<aside class="notice">https://api.skyhub.com.br/products</aside>

Creates a product, the details goes on the body (B2W accepts up to 25 characters in sku).

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [PUT] Update a product in the skyhub

```shell

curl --request PUT \ 
--url 'https://api.skyhub.com.br/products/B2W15233202767811' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \ 
--data {
    "product": {
        
        "status": "enabled",
        "removed": false,
        "price": 255555,
        "promotional_price": 1690.9,
        "cost": null,
        "weight": 1.6,
        "height": 25,
        "width": 13,
        "length": 20,
        "brand": "Yaxun",
        "ean": null,
        "nbm": "84733011",
        "categories": [
            {
                "code": "MLB30167",
                "name": "Agro, Indústria e Comércio > Agro, Indústria e Comércio > Indústria Agrícola > Matéria Prima > Mudas"
            }
        ],
        "images": [
            "http://loja.multtechinfo.com.br/imagenslw/SB1_1515243081944.jpg",
            "https://www.bluecell.com.br/image/cache/catalog/foun160-600x600.jpg",
            "https://static3.tcdn.com.br/img/img_prod/375576/carregador_fonte_parede_maxx_733_3_usb_pmcell_qualcomm_3_0_9622_2_20170908094039.jpg"
        ],
        "specifications": [
            {
                "key": "Model",
                "value": "110V"
            },
            {
                "key": "wang'x'x",
                "value": "test4"
            },
            {
                "key": "huba",
                "value": "huba"
            }
        ],
        "variations": [
            {
                "sku": "F0011-220",
                "qty": 500,
                "ean": "6959745160286",
                "images": [
                    "http://loja.multtechinfo.com.br/imagenslw/SB1_1515243081944.jpg",
                    "https://www.bluecell.com.br/image/cache/catalog/foun160-600x600.jpg",
                    "https://static3.tcdn.com.br/img/img_prod/375576/carregador_fonte_parede_maxx_733_3_usb_pmcell_qualcomm_3_0_9622_2_20170908094039.jpg"
                ],
                "specifications": [
                    {
                        "key": "Size",
                        "value": "220v"
                    },
                    {
                        "key": "Total",
                        "value": "220V"
                    }
                ]
            },
            {
                "sku": "F0011-110",
                "qty": 200,
                "ean": "6959745160286",
                "images": [
                    "http://loja.multtechinfo.com.br/imagenslw/SB1_1515243081944.jpg",
                    "https://www.bluecell.com.br/image/cache/catalog/foun160-600x600.jpg",
                    "https://static3.tcdn.com.br/img/img_prod/375576/carregador_fonte_parede_maxx_733_3_usb_pmcell_qualcomm_3_0_9622_2_20170908094039.jpg"
                ],
                "specifications": [
                    {
                        "key": "Size",
                        "value": "110v"
                    },
                    {
                        "key": "Total",
                        "value": "110V"
                    }
                ]
            }
        ],
        "variation_attributes": [
            "Size",
            "Total"
        ]
    }
}

```

<aside class="notice">https://api.skyhub.com.br/products/{sku}</aside>

Updates a product using the SKU ID.

Path Parameters            | Type       | Required          | Description                | Example
---------------------------|------------|-------------------|----------------------------|----------------------
**sku**                    | string     | required          |                            | 	sku123

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [DEL] Delete a product in the Skyhub

```shell

curl --request DELETE \ 
--url 'https://api.skyhub.com.br/products/15077' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/x-www-form-urlencoded' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/products/{sku}</aside>

Deletes a product on SkyHub using the SKU ID.

Path Parameters            | Type       | Required          | Description                | Example
---------------------------|------------|-------------------|----------------------------|----------------------
**sku**                    | string     | required          |                            | 	sku123

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [POST] Create product variation in the Skyhub

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/products/15077/variations' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/x-www-form-urlencoded' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "variation": {
    "sku": "9932",
    "qty": 10,
    "ean": "foo",
    "images": [
      "foo",
      "foo",
      "foo"
    ],
    "specifications": [
      {
        "key": "Tamanho",
        "value": "1.00 M"
      }
    ]
  }
}

```

<aside class="notice">https://api.skyhub.com.br/products/{sku}/variations</aside>

Creates products variation using the SKU ID.

Path Parameters            | Type       | Required          | Description                | Example
---------------------------|------------|-------------------|----------------------------|----------------------
**sku**                    | string     | required          | product code               | 	sku123

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [GET] Marketplaces URL

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/products/urls' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json ' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/products/urls</aside>

Returns the url of the products in the marketplaces (B2W AND Cnova).

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [POST] CREATE A PRODUCT WITH PRICE VARIATION IN THE SKU

```shell

curl --request POST \ 
--url 'https://api.skyhub.com.br/products' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \ 
--data {
  "product": {
    "sku": "Skyhub",
    "name": "CRIAR PRODUTO COM MAIS DE UMA VARIAÇÃO",
    "description": "CRIAR PRODUTO COM MAIS DE UMA VARIAÇÃO",
    "status": "enabled",
    "price": 0.0,
    "promotional_price": 255,
    "cost": 0.2,
    "weight": 1.1,
    "height": 20,
    "width": 30,
    "length": 20,
    "brand": "SKYHUB",
    "nbm": "98769898",
    "categories": [
      {
        "code": "01",
        "name": "SKYHUB HOMOLOGAÇÃO"
      }
    ],
    "images": [
      "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg",
      "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg",
      "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg"
    ],
    "specifications": [
      {
        "key": "Especicações do Produto PAI",
        "value": "Especificações do Produto PAI"
      }
    ],
    "variations": [
      {
        "sku": "301",
        "qty": 100,
        "ean": "9876543210987",
        "images": [
          "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg",
          "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg",
          "http://d26lpennugtm8s.cloudfront.net/stores/154/284/products/camiseta-lisa-verde-bandeira-algodo-p-ao-gg-pronta-entrega-355901-mlb20431777049_092015-o-07fadec89e5ed54705c1b9ab5411dec8-1024-1024.jpg"
        ],
        "specifications": [
          {
            "key": "price",
            "value": "15.00"
          }
        ]
      }
    ],
    "variation_attributes": [
      "foo",
      "foo",
      "foo"
    ]
  }
}

```

<aside class="notice">https://api.skyhub.com.br/products</aside>

Creates a product with price variation in the SKU.

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

## Queues 

### [GET] Receive a queue of orders

```shell

curl --request GET \ 
--url 'https://api.skyhub.com.br/queues/orders' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json ' \ 
--header 'x-accountmanager-key: pmcell@2017' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br'

```

<aside class="notice">https://api.skyhub.com.br/queues/orders</aside>

Retrieves the first available order in the integration queue. After processing the order, it must be removed from the integration queue within 5 minutes (or it will return to the beginning of the queue).

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

### [DEL] Remove a request from the queue

```shell

curl --request DELETE \ 
--url 'https://api.skyhub.com.br/queues/orders/Lojas Americanas-266065081401' \ 
--header 'accept: application/json' \ 
--header 'content-type: application/json ' \ 
--header 'x-accountmanager-key: pmcell@2017 ' \ 
--header 'x-api-key: 4NoZrnxsSckMWHi15syh' \ 
--header 'x-user-email: ti@hariexpress.com.br' \
--data {
  "shipment_exception": {
    "occurrence_date": "2012-10-06T04:13:00-03:00",
    "observation": "Observação da Exceção de transporte"
  }
}

```

<aside class="notice">https://api.skyhub.com.br/queues/orders/{code}</aside>

Removes an order from the integration queue.

Path Parameters         | Type      | Required      | Description                | Example
------------------------|-----------|---------------|----------------------------|----------------------
**code**                | string    | required      | request code               | foo

Header Parameters       | Type      | Required      | Description                               | Example
------------------------|-----------|---------------|-------------------------------------------|------------------------------
**accept**              | string    | required      |                                           | application/json
**content-type**        | string    | required      |                                           | application/json
**x-accountmanager-key**| string    | required      | Identifier your integration with a SkyHub | your account manager key here
**x-api-key**           | string    | required      |                                           | your api key here
**x-user-email**        | string    | required      |                                           | your user email here

