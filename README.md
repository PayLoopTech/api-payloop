# Instant Payment Gateway API
The following methods are used to empower your service with PayLoop Payment Gateway features. You can request more features by contacting our developers team. PayLoop API is a white-label payment solution.

## Getting started
1. Contact us at support.payloop.tech to get the API keys;
2. Read the following documentation;
3. Open an issue if you have any questions;

API URL: ``` https://developer.payloop.tech ```

Enviroments for making requests: ``` test ``` or  ``` live ``` 

### Protocol
PayLoop API uses JSON-RPC 2.0 protocol.

Example request:
```JSON
{
   "id": "test",
   "method": "deposit",
   "phone_number": "254721000111",
   "amount": 350
}
```

Example response:
```JSON
{
   "isSuccessful": true,
   "msg": "The service request is processed successfully."
}
```

Id used is a custom ID generated at the client side to distinguish responses. You may use any value you want.

### Authentication

Authentication URL: ``` https://developer.payloop.tech/api/live/mpesa/generate/client_credentials ```

All requests must contain the following headers:
| Header      | Description |
| ----------- | ----------- |
| accessToken      | your access token       |

### Node.js authentication
Example of how to get access token:
```JavaScript
  const apiKey = "<API-KEY>";
  const secret = "<SECRET>";

  const accessToken = Buffer.from(`${apiKey}:${secret}`).toString('base64');

```

### Postman authentication
Here is a small guide how to properly sign transaction with postman:

1. Add new environment.

![New Environment](/images/newEnvironment.png "New Environment")

2. Add ```accessToken``` variable to the new environment.

![New Environment](/images/addVariable.png "New Environment")

3. Create new request. Being on the ```Headers``` tab add ```accessToken``` header. Use postman variable syntax for them in ```Value``` column. These variables will be updated for each request using the pre-request script.

![New Environment](/images/addHeader.png "New Environment")

4. Paste the following code to the ```Pre-request Script``` tab for the request. Fill up the apiKey and secret variables. Be very careful not to accidentally share your secret.

![New Environment](/images/addRequestScript.png "New Environment")

```JavaScript
  const apiKey = "<API-KEY>";
  const secret = "<SECRET>";

  const accessToken = Buffer.from(`${apiKey}:${secret}`).toString('base64');

  postman.setEnvironmentVariable("accessToken", accessToken);
```
### Deposit Request
Deposit URL: ``` https://developer.payloop.tech/api/live/mpesa/deposit ```
| Property      | Description |
| ----------- | ----------- |
| id      | Transaction ID. Could be used in getStatus method      |
| phoneNo      | This is the phone number initiating the C2B transaction.      |
| amount      | This is the amount being transacted. The parameter expected is a numeric value.       |
| callBackURL      | 	This is the URL to be specified in your request that will be used by PayLoop to send notification upon processing of the payment request.      |

Example request:
```JSON
{
    "id": "test",
    "phoneNo":"254721000111",
    "amount":1,
    "callBackURL":"http://developer.payloop.tech/api/live/withdraw/mpesa/response"
}
```
Example response:
```JSON
{
    "isSuccessful": true,
    "msg":"The service request is processed successfully."
}
```

### Withdraw Request
Deposit URL: ``` https://developer.payloop.tech/api/live/mpesa/withdraw ```
| Property      | Description |
| ----------- | ----------- |
| id      | Transaction ID. Could be used in getStatus method      |
| phoneNo      | This is the phone number initiating the C2B transaction.      |
| amount      | This is the amount being transacted. The parameter expected is a numeric value.       |
| resultURL      | 	This is the URL to be specified in your request that will be used by PayLoop to send notification upon processing of the payment request.      |
| queueTimeOutURL      | 	This is the URL to be specified in your request that will be used by API Proxy to send notification incase the payment request is timed out while awaiting processing in the queue.     |

Example request:
```JSON
{
    "id": "test",
    "phoneNo":"254721000111",
    "amount":1,
    "resultURL":"<RESULT-URL>",
    "queueTimeOutURL":"<TIMEOUT-URL>"
}
```
Example response:
```JSON
{
    "isSuccessful": true,
    "msg":"Withdraw request sent successfully"
}
```
### Balance Request
Deposit URL: ``` https://developer.payloop.tech/api/business/balance ```

Example request:
```JSON
{}
```
Example response:
```JSON
{
    "isSuccessful": true,
    "balance":24600
}
```

### Transacrtion History Request
Deposit URL: ``` https://developer.payloop.tech/api/business/transactions/history ```

Example request:
```JSON
{}
```
Example response:
```JSON
{
    "isSuccessful": true,
    "transactions":{}
}
```


### Support
Dedicated Support Line

Inform us in case a dedicated support line is needed. Feel free to request it at support@payloop.tech.
- You provide the first line support from your side and send your tickets directly to our dedicated email address. These tickets are forwarded strictly to our second level support team. It will be assigned the highest priority. Please don't make our email public.
