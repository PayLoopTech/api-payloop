# Instant Payment Gateway API
The following methods are used to empower your service with PayLoop Payment Gateway features. You can request more features by contacting our developers team. PayLoop API is a white-label payment solution.

## Postman authentication
Here is a small guide how to properly sign transaction with postman:

1. Add new environment.
2. Add sign and api-key variables to the new environment.
3. Create new request. Being on the Headers tab add sign and api-key headers. Use postman variable syntax for them in Value column. These variables will be updated for each request using the pre-request script.
3. Paste the following code to the ~~~ Pre-request Script ~~~ tab for the request. Fill up the apiKey and secret variables. Be very careful not to accidentally share your secret.