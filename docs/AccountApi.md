# TemplateFox::AccountApi

All URIs are relative to *https://api.pdftemplateapi.com*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_account**](AccountApi.md#get_account) | **GET** /v1/account | Get account info |
| [**list_transactions**](AccountApi.md#list_transactions) | **GET** /v1/account/transactions | List transactions |


## get_account

> <AccountInfoResponse> get_account

Get account info

Get account information including remaining credits.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Usage:** Check credit balance before performing operations.  **No credits consumed:** This is a read-only endpoint.

### Examples

```ruby
require 'time'
require 'templatefox'
# setup authorization
TemplateFox.configure do |config|
  # Configure API key authorization: ApiKeyAuth
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'
end

api_instance = TemplateFox::AccountApi.new

begin
  # Get account info
  result = api_instance.get_account
  p result
rescue TemplateFox::ApiError => e
  puts "Error when calling AccountApi->get_account: #{e}"
end
```

#### Using the get_account_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<AccountInfoResponse>, Integer, Hash)> get_account_with_http_info

```ruby
begin
  # Get account info
  data, status_code, headers = api_instance.get_account_with_http_info
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <AccountInfoResponse>
rescue TemplateFox::ApiError => e
  puts "Error when calling AccountApi->get_account_with_http_info: #{e}"
end
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**AccountInfoResponse**](AccountInfoResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_transactions

> <TransactionsResponse> list_transactions(opts)

List transactions

List transaction history for the authenticated user.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Pagination:** Use `limit` and `offset` query parameters.  **Transaction types:** - `PDFGEN`: PDF generation (consumes credits) - `REFUND`: Credit refund (on failed generation) - `PURCHASE`: Credit purchase - `BONUS`: Bonus credits  **Credits field:** - Positive value = credits consumed - Negative value = credits added  **No credits consumed:** This is a read-only endpoint.

### Examples

```ruby
require 'time'
require 'templatefox'
# setup authorization
TemplateFox.configure do |config|
  # Configure API key authorization: ApiKeyAuth
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'
end

api_instance = TemplateFox::AccountApi.new
opts = {
  limit: 56, # Integer | Number of records to return
  offset: 56 # Integer | Number of records to skip
}

begin
  # List transactions
  result = api_instance.list_transactions(opts)
  p result
rescue TemplateFox::ApiError => e
  puts "Error when calling AccountApi->list_transactions: #{e}"
end
```

#### Using the list_transactions_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<TransactionsResponse>, Integer, Hash)> list_transactions_with_http_info(opts)

```ruby
begin
  # List transactions
  data, status_code, headers = api_instance.list_transactions_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <TransactionsResponse>
rescue TemplateFox::ApiError => e
  puts "Error when calling AccountApi->list_transactions_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **limit** | **Integer** | Number of records to return | [optional][default to 300] |
| **offset** | **Integer** | Number of records to skip | [optional][default to 0] |

### Return type

[**TransactionsResponse**](TransactionsResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

