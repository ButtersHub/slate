# Errors


WeTranscode uses conventional HTTP response codes to indicate the success or failure of an API request. In general, codes in the 2xx range indicate success, codes in the 4xx range indicate an error that failed given the information provided (e.g., a required parameter was omitted, a charge failed, etc.), and codes in the 5xx range indicate an error with WeTranscode's servers (these are rare).
Not all errors map cleanly onto HTTP response codes, however. When a request is valid but does not complete successfully, we return a 402 error code.

### Attributes
field | value
---------- | -------
Type | The type of error returned. Can be: api_connection_error, api_error, authentication_error, card_error, invalid_request_error, or rate_limit_error.
message (optional) | A human-readable message providing more details about the error. For card errors, these messages can be shown to your users.
code (optional) | For card errors, a short string from amongst those listed on the right describing the kind of card error that occurred.
param (optional) | The parameter the error relates to if the error is parameter-specific. You can use this to display a message near the correct form field, for example.


### HTTP status code summary

Error Code | Meaning
---------- | -------
200 - OK   | Everything worked as expected.
400 - Bad Request	| The request was unacceptable, often due to missing a required parameter.
401 - Unauthorized	| No valid API key provided.
402 - Request Failed	| The parameters were valid but the request failed.
404 - Not Found	| The requested resource doesn't exist.
409 - Conflict	| The request conflicts with another request (perhaps due to using the same idempotent key).
429 - Too Many Requests	| Too many requests hit the API too quickly. We recommend an exponential backoff of your requests.
500, 502, 503, 504 - Server Errors	| Something went wrong on Stripe's end. (These are rare.)


### handling Errors
Our API libraries raise exceptions for few reasons, such as a invalid parameter, authentication errors, and network unavailability. 
We recommend writing code that gracefully handles all possible API exceptions.

```java
try {
  // Use Stripe's library to make requests...
} catch (CardException e) {
  // Since it's a decline, CardException will be caught
  System.out.println("Status is: " + e.getCode());
  System.out.println("Message is: " + e.getMessage());
} catch (RateLimitException e) {
  // Too many requests made to the API too quickly
} catch (InvalidRequestException e) {
  // Invalid parameters were supplied to Stripe's API
} catch (AuthenticationException e) {
  // Authentication with Stripe's API failed
  // (maybe you changed API keys recently)
} catch (APIConnectionException e) {
  // Network communication with Stripe failed
} catch (StripeException e) {
  // Display a very generic error to the user, and maybe send
  // yourself an email
} catch (Exception e) {
  // Something else happened, completely unrelated to Stripe
}
```
