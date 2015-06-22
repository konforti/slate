# Introduction

> API Endpoint

```shell
http://localhost:3000/api/
```

The People API is organized around REST. Our API is designed to have predictable, resource-oriented URLs and to use HTTP response codes to indicate API errors.
 
We support cross-origin resource sharing to allow you to interact securely with our API from a client-side web application (though you should remember that you should never expose your secret API key in any public website's client-side code). 
 
JSON will be returned in all responses from the API, including errors .

Use your base url with /api/ and API version (currently v1 is available) as your endpoint. For example:

<code>http://example.com/api/v1/persons/</code>

# Authentication

> To authorize, use People app security key.
Example Request:

```shell
curl http://localhost:3000/api/v1/persons/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2:
```

You authenticate to the People API by providing your Secret keys in the request. You can manage your API keys from your account settings. Your API keys carry many privileges, so be sure to keep them secret!

Authentication to the API occurs via HTTP Basic Auth. Provide your Secret key as the basic auth username. You do not need to provide a password.

<aside class="notice">
Use your secret key from the settings page. CURL uses the -u flag to pass basic auth credentials (adding a colon after your API key will prevent it from asking you for a password).
</aside>
