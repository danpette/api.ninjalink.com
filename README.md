#API 
Current version: 2
Endpoint: https://api.ninjalink.com/v2/

## Authenticate

###Authorize
This method will create a authorization token valid for 15 minutes, authorization token are required for for api calls.

Url: https://api.ninjalink.com/v2/auth/authorize

Accepted HTTP Methods: GET

Parameters:

String Api

String Email


###Unauthorize
This method will unvalidate the authorization token, use this when done using the api.

Url: https://api.ninjalink.com/v2/auth/unauthorize

HTTP Method: Get

Requires a valid authorization token in header field: AuthorizationToken


## Account

### Info
Url: https://api.ninjalink.com/v2/account/info

### Websites
Url: https://api.ninjalink.com/v2/account/websites

### Payments
Url: https://api.ninjalink.com/v2/account/payments

## Sales

### List all sales
Url: https://api.ninjalink.com/v2/sales/list

##Links

### Link
This method will convert a regular store link to affiliate link.

Calling this method will count as a click on the link, do not use this is combination with the redirect method. 

Url: https://api.ninjalink.com/v2/links/link

HTTP Method: Get

Parameters:

String Url (url must be encoded)

String Api 

Example:

```php
$affiliate_link = file_get_contents('https://api.ninjalink.com/v2/links/link?Api=ffffffffffffffffffffff&Url='. url_encode('http://someurl.com'));

//Your logging and logic here.

header('location:' . $affiliate_link);
```

### Redirect
Url: https://api.ninjalink.com/v2/links/redirect

## Website

### Validate website implementation
Url: https://api.ninjalink.com/v2/website/validate

## Stores

### List all stores
Url: https://api.ninjalink.com/v2/stores/list

## Market

### List all markets
Url: https://api.ninjalink.com/v2/markets/list

## Reports

### Clicks
Url: https://api.ninjalink.com/v2/repport/clicks

## Product

### Search
Url: https://api.ninjalink.com/v2/products/search

### Fetch
Url: https://api.ninjalink.com/v2/products/fetch/:ID

### Categories
Url: https://api.ninjalink.com/v2/products/categories
