# Authentication

Authenticate your account when using the API by including your secret API key in the request. 
You can manage your API keys in the Dashboard. Your API keys carry many privileges, so be sure to keep them secret! 
Do not share your secret API keys in publicly accessible areas such GitHub, client-side code, and so forth.
To use your API key, you need only call  with your key. 
The library will then automatically send this key in each request.
All API requests must be made over [HTTPS] (https://en.wikipedia.org/wiki/HTTPS). Calls made over plain HTTP will fail. API requests without authentication will also fail.


> To authenticate, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```PHP
\Wetranscode\Wetranscode::setApiKey("asdfwer9i9adf9asdf00asdf");
```

```java
require 'kittn'
api = Kittn::APIClient.authorize!('meowmeowmeow');
```
