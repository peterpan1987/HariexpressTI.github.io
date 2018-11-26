# Mercado Livre

## Public & Private resources

First off, there are somethings we should know about how Mercado Livre API data are structured.

Mercado Livre divides data in two categories, which are "public resources" and "private resources".

Public resources are the ones that anyone can request with the proper URL. For example, request a list of countries that Mercado Livre acts in, request a public user info using a target user Id, such as name, last name, join date, country, city and etc.

Private resources are data that needs to be ocult from the majority. User data is a matter of secure and that leads us to next API subjects, which are Authentication & Authorization.

## Creating an Application

In order to interact with users, we need to create a single application for stabilising a channel to interact with users.
Applications acts like simple channels from where request will be authenticated from.

An App is created directly from a Mercado Livre account, such as a built-in account feature.
Everything we need is access the [Mercado Livre Application Manager](http://applications.mercadolibre.com/) and forward the proper information to sync it to a Mercado Livre user profile.

When creating a new app, we need to select a country, it also means that each created app can only be used by users by the same country app was created from. Mercado Livre encourages developers to create multiple apps in case they need to interact with more than a single country users.

<img src="./images/mercadolivre/app-manager.png" title="Application Manager creating panel" />

<strong>Application Data</strong>

There are three groups of information in this form: Basic Application Info, Authentication & Security and Notification Settings. 


<strong>Basic application info</strong>

Name                | Description
--------------------|---------------------------------------------------------------------------------------------------------
**ID**              | This is your client_id. It must be used to retrieve an access token.
**Secret Key**      | This is used to retrieve an access token, too. Don’t share this secret with anyone.
**Name**            | Name of your application. It must be unique.
**Short Name**      | Name that Mercado Livre uses to generate your application’s URL.
**Description**     | This description (up to 150 characters) will be shown when the application requests an authorization.


<strong>Authentication & security</strong>

Name                | Description
--------------------|---------------------------------------------------------------------------------------------------------
**Callback URL**    | Redirect URI. URL to return users to your app after they grant access.
**Domains**         | Authorized Javascript Origins. Comma-separated list of fully-qualified domain name of all pages that will use the client-side authentication. Only needed if using Javascript API. Don’t include protocol, port or “localhost”. Both of these attributes are further explained in the authentication and authorization guide.

<strong>Scopes</strong>

Name                | Description
--------------------|---------------------------------------------------------------------------------------------------------
**Read**            | Allows to use API GET HTTP methods.
**Write**           | Allows to use API PUT, POST and DELETE HTTP methods.
**Offline Access**  | Allows to make request server side and refresh token.


<strong>Notes</strong>:

A mandatory requirement for the creation of an application in the Application Manager is to use HTTPS protocol in your redirect URI to ensure that the message is sent encrypted and to people with reading permission only.

If you are still using HTTP and want to make changes, set up the new URL with HTTPS.


### [GET] Get information from a created APP

>This request returns a JSON text containing information from a created application.

```json
{
    "id": 9005017978365352,
    "site_id": "MLB",
    "name": "TestPostman",
    "description": "Aplicação de teste.",
    "thumbnail": null,
    "owner_id": 164964808,
    "catalog_product_id": null,
    "item_id": null,
    "price": null,
    "currency_id": null,
    "need_authorization": true,
    "short_name": "tpost",
    "url": "http://apps.mercadolivre.com.br/tpost",
    "callback_url": "https://teste.com/",
    "sandbox_mode": true,
    "is_public": true,
    "project_id": 0,
    "active": true,
    "max_requests_per_hour": 18000,
    "scopes": [
        "read",
        "offline_access",
        "write"
    ],
    "domains": [],
    "certification_status": "not_certified"
}
```
<aside class="notice">https://api.mercadolibre.com/applications/{app_id}?{access_token}</aside>

Returns information from a created application.
**Note**: Requires access_token.

Path Parameters         | Required  | Type          | Description
------------------------|-----------|---------------|--------------------------------------------------------------------------
**app_id**              | true      | number        | Application ID
**access_token**        | false     | string        | OAuth 2.0 Access Token


<aside class="success">
Request example:
https://api.mercadolibre.com/applications/9005017978365352?APP_USR-9005017978365352-111709-0027e3b0cc335af2ef7b88d2bb19fe8d-164964808​
</aside>

### [GET] Get an application notification history

>This request returns a JSON text containing informations of an application notification history.
>Note: As we can see, that's an array of notifications. Sadly, there're no more extra info than that from Mercado Livre docs.

```json
{
    "messages": []
}
```

<aside class="notice">https://api.mercadolibre.com/myfeeds?app_id={app_id}</aside>

Gets an array of an application notification history.

Path Parameters         | Required  | Type          | Description
------------------------|-----------|---------------|--------------------------------------------------------------------------
**app_id**              | true      | number        | Application ID

<aside class="success">
Request example:
https://api.mercadolibre.com/myfeeds?app_id=9005017978365352
</aside>


## Authentication & Authorization

Authentication is the act or process to confirm something or someone as real. The authentication of a person consists in a verification of his identity based on some factors, granting that the sent data are correct.

Currently, Mercado Livre authenticates clients based on their account info, such as user & password.

Authorization, different than authentication, is the act or process to determine if something or someone has access to determined resource. Mercado Livre uses the "OAuth 2.0" protocol for authorizating requests. Inside this protocol exists 4 different ways of authorizating an object, they are also known as "Grant Types":

* The Authorization Code Grant Type (Server Side)
* The Implicit Grant Type (Client Side)
* The Password Credentials Grant Type
* The Client Credentials Grant Type

Though both of ways of authorizating an object has its own finalities depending on the system demand, Mercado Livre uses only the first two Grant Types.

Client side authorization is the most appropriate when applications execute codes directly from client side, for example, javascript, ajax, angular or mobiles applications (read more on Client Side Authorization).

Server side authorization is the most appropriate when applications execute codes directly from server side, for example, java, grails, go, between others server-applications types (read more on Server Side Authorization).

### Getting an access token

In order to get a valid access token, we need to create a Mercado Livre Application. Each APP has its id and that's how Mercado Livre grant access to our requests.

Mercado Livre says:

*"To register an application, you must go to our [Application Manager](http://applications.mercadolibre.com/), choose your country and Login. Since an application only works for the country when the user is registered, you need to have an user and an app for each country where you want to work. Once you Login, you’ll be asked to fill in some details about your application and after it, you’ll get a Client_Id and a Secret_Key that will be needed to authenticate with our API."*

Once your APP is created, you'll need to retrieve your access token through a [Mercado Livre Developer Tool](https://developers.mercadolibre.com/en_us/products-authentication-authorization/#token). Just fill up the "Enter your application ID" field and confirm the "Show my information".

<img src="./images/mercadolivre/auth-manager.png" title="Mercado Livre Developer Tool" />

### Authorization error codes reference

Error               | Description | Possible solution
--------------------|-------------|-------------------------------------
**invalid_client**  | Invalid client_id and/or client_secret provided. | Check your application info and verify parameters 
**invalid_grant**   | To create an access token the user must have an active session, or your application should request authorization for offline_access scope. The provided authorization grant is invalid, expired, revoked, or does not match the redirection URI used in the authorization request. | Verify the parameter redirect_uri is the same configured in your application (App Manager), if this not solve, do a new request to obtain a new code.
**invalid_grant**   | Error validating grant. Your authorization code or refresh token may have expired or it has already been used. | Make a new request to obtain one new code or refresh_token.
**invalid_grant**   | The client_id does not match the original. | The parameter client_id wasn’t found, to get your client_id, consult your application (App Manager).
**invalid_grant**   | The redirect_uri does not match the original. | The parameter redirect_uri is not the same configured in you application, to get your a redirect_uri, consult your application (App Manager)
**invalid_scope**   | The requested scope is invalid, unknown, or malformed. | The values allowed for parameter scope are:“offline_access”,”write”,”read”.
**invalid_request** | The request is missing a required parameter, includes an unsupported parameter or parameter value or is otherwise malformed. | Verify that the parameters sent are valid and are not duplicated.
**unsupported_grant_type** | The authorization grant type is not supported by the authorization server. | The values allowed for parameter grant_type are“authorization_code” or “refresh_token”.
**forbidden**   | The caller is not authorized to access this resource. | It is using the token of another user.

## Users

### [GET] Get user id

>This request returns JSON text containing a public user info (including its id) from a given user nickname.
>Note: Mercado Livre API says that consulting an user information through this request return two differents JSONs in case header contains the access token.
>Since access token would grant request to return private user data inside JSON text.
>However, it doesn't happen, both JSONs become the same with/without a given access token.

```json
{
    "site_id": "MLB",
    "seller": {
        "id": 164964808,
        "seller_reputation": {
            "power_seller_status": null
        },
        "real_estate_agency": false,
        "car_dealer": false,
        "tags": []
    },
    "paging": {
        "total": 0,
        "offset": 0,
        "limit": 50,
        "primary_results": 0
    },
    "results": [],
    "secondary_results": [],
    "related_results": [],
    "sort": {
        "id": "relevance",
        "name": "More relevant"
    },
    "available_sorts": [
        {
            "id": "price_asc",
            "name": "Lower price"
        },
        {
            "id": "price_desc",
            "name": "Higher price"
        }
    ],
    "filters": [],
    "available_filters": []
}
```

<aside class="notice">https://api.mercadolibre.com/sites/{site_id}/search?nickname={nickname}</aside>

Gets a public user info (including its user_id) from a given user nickname.

Path Parameters         | Required  | Type          | Description
------------------------|-----------|---------------|--------------------------------------------------------------------------
**site_id**             | true      | string        | Region from where user will be filtered from.
**nickname**            | true      | string        | The user nickname.

Header Parameters       | Required  | Type          | Description
------------------------|-----------|---------------|--------------------------------------------------------------------------
**access_token**        | false     | string        | OAuth 2.0 Access Token


<aside class="success">
Request example:
https://api.mercadolibre.com/sites/MLB/search?nickname=ALAL997069
</aside>

### [GET] Get public info

>This requests returns a JSON text containing the user profile public information.
>Note: Mercado Livre API says that consulting an user information through this request return two differents JSONs in case header contains the access token.
>Since access token would grant request to return private user data inside JSON text.
>However, it doesn't happen, both JSONs become the same with/without a given access token.

```json
{
    "id": 241461054,    //用户ID**
    "nickname": "MEGAHARIBABA",    //用户昵称**
    "registration_date": "2017-01-20T13:41:52.000-04:00",    //账号创建时间**
    "country_id": "BR",    //账户所在国家**
    "address": {    //账户地址
        "city": "São Paulo",    //账户所在城市**
        "state": "BR-SP"    //账户所在省份**
    },
    "user_type": "normal",//账户类型（普通，官方旗舰店）**
    "tags": [    //标签**
        "normal",    //普通类型**
        "credits_profile",
        "eshop"
    ],
    "logo": null,
    "points": 5192,    //作为买家积分**    
    "site_id": "MLB",
    "permalink": "http://perfil.mercadolivre.com.br/MEGAHARIBABA",    //卖家或买家的基本信息页地址**
    "seller_reputation": {    //作为卖家的信誉**
        "level_id": "1_red",    //信誉等级，共5级**
        "power_seller_status": null,
        "transactions": {    //订单处理数量**
            "canceled": 193,    //取消的订单数**
            "completed": 11267,    //完成的订单数**
            "period": "historic",
            "ratings": {    //买家评价**
                "negative": 0.02,    //买家的好评比例**
                "neutral": 0.02,    //买家的中评比例**
                "positive": 0.96    //买家的好评比例**
            },
            "total": 11460    //总的订单数**
        }
    },
    "buyer_reputation": {    //作为买家的信誉
        "tags": [
            ""
        ]
    },
    "status": {    //账号状态**
        "site_status": "active"    //激活状态**
    }
}
```

<aside class="notice">https://api.mercadolibre.com/users/{user_id}</aside>

Gets public Mercado Livre's user info by its user_id.

Path Parameters         | Required  | Type          | Description
------------------------|-----------|---------------|--------------------------------------------------------------------------
**user_id**             | true      | number        | Mercado Livre's user ID

Header Parameters       | Required  | Type          | Description
------------------------|-----------|---------------|--------------------------------------------------------------------------
**access_token**        | false     | string        | OAuth 2.0 Access Token

<aside class="success">
Request example:
https://api.mercadolibre.com/users/164964808
</aside>

### [GET] Get user address

>This request returns a JSON text containing user address info.

```json
[
    {
        "id": 1012486875,
        "user_id": 164964808,
        "contact": null,
        "phone": null,
        "address_line": "Rua Vinte e Cinco de Março - de 551 ao fim - lado ímpar 467",
        "floor": null,
        "apartment": null,
        "street_number": "467",
        "street_name": "Rua Vinte e Cinco de Março - de 551 ao fim - lado ímpar",
        "zip_code": "01021200",
        "city": {
            "id": "BR-SP-44",
            "name": "São Paulo"
        },
        "state": {
            "id": "BR-SP",
            "name": "São Paulo"
        },
        "country": {
            "id": "BR",
            "name": "Brasil"
        },
        "neighborhood": {
            "id": null,
            "name": "Centro"
        },
        "municipality": {
            "id": null,
            "name": null
        },
        "search_location": {
            "state": {
                "id": "TUxCUFNBT085N2E4",
                "name": "São Paulo"
            },
            "city": {
                "id": "TUxCQ1NQLTk0MDc",
                "name": "São Paulo Centro"
            },
            "neighborhood": {
                "id": "TUxCQkNFTjUwNzE",
                "name": "Centro"
            }
        },
        "types": [
            "billing",
            "default_selling_address",
            "shipping"
        ],
        "comment": null,
        "between": null,
        "references": null,
        "aditional_info": null,
        "geolocation_type": "ROOFTOP",
        "latitude": -23.5457207,
        "longitude": -46.6324684,
        "status": "active",
        "date_created": "2018-11-05T08:45:20.000-04:00",
        "normalized": true,
        "open_hours": null
    }
]
```

<aside class="notice">https://api.mercadolibre.com/users/{user_id}/addresses?access_token={access_token}</aside>

Gets an user address based on its user_id.
**Note**: Requires access_token.

Path Parameters         | Required  | Type          | Description
------------------------|-----------|---------------|--------------------------------------------------------------------------
**user_id**             | true      | number        | Mercado Livre's user ID
**access_token**        | true      | string        | OAuth 2.0 Access Token

<aside class="success">
Request example:
https://api.mercadolibre.com/users/164964808/addresses?access_token=APP_USR-9005017978365352-111709-0027e3b0cc335af2ef7b88d2bb19fe8d-164964808
</aside>

### [GET] Get user payment methods

>This request returns a JSON text containing the informations about which payment method current user accepts.

```json
[
    {
        "id": "visa",
        "name": "Visa",
        "payment_type_id": "credit_card",
        "thumbnail": "http://img.mlstatic.com/org-img/MP3/API/logos/visa.gif",
        "secure_thumbnail": "https://www.mercadopago.com/org-img/MP3/API/logos/visa.gif"
    },
    {
        "id": "master",
        "name": "Mastercard",
        "payment_type_id": "credit_card",
        "thumbnail": "http://img.mlstatic.com/org-img/MP3/API/logos/master.gif",
        "secure_thumbnail": "https://www.mercadopago.com/org-img/MP3/API/logos/master.gif"
    },
    {
        "id": "hipercard",
        "name": "Hipercard",
        "payment_type_id": "credit_card",
        "thumbnail": "http://img.mlstatic.com/org-img/MP3/API/logos/hipercard.gif",
        "secure_thumbnail": "https://www.mercadopago.com/org-img/MP3/API/logos/hipercard.gif"
    },
    {
        "id": "amex",
        "name": "American Express",
        "payment_type_id": "credit_card",
        "thumbnail": "http://img.mlstatic.com/org-img/MP3/API/logos/amex.gif",
        "secure_thumbnail": "https://www.mercadopago.com/org-img/MP3/API/logos/amex.gif"
    },
    {
        "id": "diners",
        "name": "Diners",
        "payment_type_id": "credit_card",
        "thumbnail": "http://img.mlstatic.com/org-img/MP3/API/logos/diners.gif",
        "secure_thumbnail": "https://www.mercadopago.com/org-img/MP3/API/logos/diners.gif"
    },
    {
        "id": "elo",
        "name": "Elo",
        "payment_type_id": "credit_card",
        "thumbnail": "http://img.mlstatic.com/org-img/MP3/API/logos/elo.gif",
        "secure_thumbnail": "https://www.mercadopago.com/org-img/MP3/API/logos/elo.gif"
    },
    {
        "id": "giftcard",
        "name": "Vale-Presente Mercado Livre",
        "payment_type_id": "digital_currency",
        "thumbnail": "http://img.mlstatic.com/org-img/MP3/API/logos/giftcard.gif",
        "secure_thumbnail": "https://www.mercadopago.com/org-img/MP3/API/logos/giftcard.gif"
    },
    {
        "id": "bolbradesco",
        "name": "Boleto",
        "payment_type_id": "ticket",
        "thumbnail": "http://img.mlstatic.com/org-img/MP3/API/logos/2006.gif",
        "secure_thumbnail": "https://www.mercadopago.com/org-img/MP3/API/logos/2006.gif"
    },
    {
        "id": "account_money",
        "name": "Dinheiro na minha conta do MercadoPago",
        "payment_type_id": "account_money",
        "thumbnail": "http://img.mlstatic.com/org-img/MP3/API/logos/2007.gif",
        "secure_thumbnail": "https://www.mercadopago.com/org-img/MP3/API/logos/2007.gif"
    },
    {
        "id": "consumer_credits",
        "name": "Mercado Crédito",
        "payment_type_id": "digital_currency",
        "thumbnail": "http://img.mlstatic.com/org-img/MP3/API/logos/consumer_credits.gif",
        "secure_thumbnail": "https://www.mercadopago.com/org-img/MP3/API/logos/consumer_credits.gif"
    }
]
```

<aside class="notice">https://api.mercadolibre.com/users/{user_id}/accepted_payment_methods?access_token={access_token}</aside>

Gets the payment methods accepted by the user filtered by user_id.
**Note**: Requires access_token.

Path Parameters         | Required  | Type          | Description
------------------------|-----------|---------------|--------------------------------------------------------------------------
**user_id**             | true      | number        | Mercado Livre's user ID
**access_token**        | true      | string        | OAuth 2.0 Access Token

<aside class="success">
Request example:
https://api.mercadolibre.com/users/164964808/accepted_payment_methods?access_token=APP_USR-9005017978365352-111709-0027e3b0cc335af2ef7b88d2bb19fe8d-164964808
</aside>

### [POST] Resfresh user access token

<aside class="notice">https://api.mercadolibre.com/oauth/token?grant_type=refresh_token&client_id={client_id}&client_secret={client_secret}&refresh_token={refresh_token}</aside>

Path Parameters         | Required  | Type          | Description
------------------------|-----------|---------------|--------------------------------------------------------------------------
**client_id**           | true      | number        | client_id
**client_secret**       | true      | string        | client_secret
**refresh_token**       | true      | string        | refresh_token

<aside class="success">
Request example:
https://api.mercadolibre.com/oauth/token?grant_type=refresh_token&client_id=3807745542587699&client_secret=2bonhFyfUHrhruW9utcFvHgZAO381ozY&refresh_token=TG-5b7ed7c1e4b0b68588c95061-241461054
</aside>

##