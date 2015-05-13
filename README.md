#API 
Current version: 2

Endpoint: https://api.ninjalink.com/v2/

## Authenticate

###Authorize
This method will create a authorization token valid for 15 minutes, authorization token are required for for api calls. The token is bound to the ip that performed the authroize request.

GET/ https://api.ninjalink.com/v2/auth/authorize

Parameters:
* String api, your personal api key.
* String email, the email associated with the api key.

Response type
* JSON String

Response codes:
* 200 - OK, se data field for token.
* 400 - Bad request, missing get values "api" and/or "email".
* 405 - Method not allowed, this method only accepts GET requests.
* 500 - Internal Server Error.
* 504 - Unauthorized, invalid combination of email and api key.

###Unauthorize
This method will unvalidate the authorization token, use this when done using the api.

GET/ https://api.ninjalink.com/v2/auth/unauthorize

Requires a valid authorization token in header field: AuthorizationToken

## Account

### Info

Account inforamtion, not all account data is available.

GET/ https://api.ninjalink.com/v2/account/info

### Websites

List all your websites and their status

GET/ https://api.ninjalink.com/v2/account/websites

### Payments

List a summary of all payments.

GET/ https://api.ninjalink.com/v2/account/payments

Example response:
```php
{"code":200,"data":[{"ID":1,"Date":"31.012.2015","Commission": "423.21", "Currency": "NOK", "Status": "Payed", "Account": "1234.56.78901"}]}
```

##Link

### Click
This method will convert a regular store link to affiliate link.

Calling this method will count as a click on the link, do not use this is combination with the redirect method. 

GET/ https://api.ninjalink.com/v2/link/click

Parameters:

* String url, url must be encoded
* String key, your personal api key.

Response type
* JSON String

Response fields
* integer code, 200 if success, else se error codes.
* string data, monitized url
 
Response codes:
* 200 - OK (se data field for url)
* 204 - No content, Link not modified, no such merchant (se data field for url)
* 400 - Bad request, missing get values "api" or invalid key
* 405 - Method not allowed, this method only accepts POST requests.
* 500 - Internal server error

Example:

```php
$affiliate_link = file_get_contents('https://api.ninjalink.com/v2/link/click?url=AAAAAAAAAAAAAAAAAAAAA&Url='. url_encode('http://someurl.com'));

$data = json_decode(affiliate_link);

header('location:' . $data->data);
```

## Website

### Validate website implementation

This method will validate if you combination of token and website id is correct.

GET/ https://api.ninjalink.com/v2/website/validate

## Stores

### List all stores

This method lists all stores and their url's. stores can be filtered by markets (se markets api for valid options)

POST/ https://api.ninjalink.com/v2/stores/list

Requires a valid authorization token in header field: AuthorizationToken

## Market

### List all markets

Returns a list off all available markets

GET/  https://api.ninjalink.com/v2/markets/list

Example response:

```php
{"code":200,"data":[{"ID":1,"Name":"Norway"},{"ID":2,"Name":"Sweden"}]}
```

## Reports

### Overview

Lists statistics for clicks, sale and commission for either today, yesterday, this month, last month, this year.

POST/ https://api.ninjalink.com/v2/repport/overview

**Requires a valid authorization token in header field: AuthorizationToken**

### Sales

Returns a list of your sales.

POST/ https://api.ninjalink.com/v2/repport/sales

**Requires a valid authorization token in header field: AuthorizationToken**

## Product

### Search

Search for a product by name, category or store.

GET/ https://api.ninjalink.com/v2/products/search

### Fetch

Fetch a product set by filters, like search all results from this method are paged and max 100 products can be retrived per request. Abuse of this method will get your API access suspended.

GET/ https://api.ninjalink.com/v2/products/fetch/

### Categories

List all categories for a market.

GET/ https://api.ninjalink.com/v2/products/categories

# 2xx Http codes
* 200 - OK

# 4xx Http codes
* 405 - Method not allowed
* 400 - Bad request
 
# 5xx Http codes
* 500 - Interal server error
* 504 - Unauthorized
