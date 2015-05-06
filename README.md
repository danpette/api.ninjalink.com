#API 
Current version: 2
Endpoint: https://api.ninjalink.com/v2/

## Authenticate

###Authorize
This method will create a authorization token valid for 15 minutes, authorization token are required for for api calls.

GET/ https://api.ninjalink.com/v2/auth/authorize

Parameters:

* String Api, your personal api key.
* String Email, the email associated with the api key.


###Unauthorize
This method will unvalidate the authorization token, use this when done using the api.

GET/ https://api.ninjalink.com/v2/auth/unauthorize

Requires a valid authorization token in header field: AuthorizationToken

## Account

### Info
GET/ https://api.ninjalink.com/v2/account/info

### Websites
GET/ https://api.ninjalink.com/v2/account/websites

### Payments
GET/ https://api.ninjalink.com/v2/account/payments

##Links

### Link
This method will convert a regular store link to affiliate link.

Calling this method will count as a click on the link, do not use this is combination with the redirect method. 

GET/ https://api.ninjalink.com/v2/links/link

Parameters:

* String Url, url must be encoded
* String Api, your personal api key.

Example:

```php
$affiliate_link = file_get_contents('https://api.ninjalink.com/v2/links/link?Api=ffffffffffffffffffffff&Url='. url_encode('http://someurl.com'));

//Your logging and logic here.

header('location:' . $affiliate_link);
```

## Website

### Validate website implementation

This method will validate if you combination of token and website id is correct.

GET/ https://api.ninjalink.com/v2/website/validate

## Stores

### List all stores

This method lists all stores and their url's. stores can be filtered by markets (se markets api for valid options)

GET/ https://api.ninjalink.com/v2/stores/list

## Market

### List all markets
GET/  https://api.ninjalink.com/v2/markets/list

## Reports

### Overview

Lists statistics for clicks, sale and commission for either today, yesterday, this month, last month, this year.

GET/ https://api.ninjalink.com/v2/repport/overview

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
