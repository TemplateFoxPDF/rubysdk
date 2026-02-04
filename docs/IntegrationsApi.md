# TemplateFox::IntegrationsApi

All URIs are relative to *https://api.pdftemplateapi.com*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**delete_s3_config**](IntegrationsApi.md#delete_s3_config) | **DELETE** /v1/integrations/s3 | Delete S3 configuration |
| [**get_s3_config**](IntegrationsApi.md#get_s3_config) | **GET** /v1/integrations/s3 | Get S3 configuration |
| [**save_s3_config**](IntegrationsApi.md#save_s3_config) | **POST** /v1/integrations/s3 | Save S3 configuration |
| [**test_s3_connection**](IntegrationsApi.md#test_s3_connection) | **POST** /v1/integrations/s3/test | Test S3 connection |


## delete_s3_config

> <S3SuccessResponse> delete_s3_config

Delete S3 configuration

Delete S3 storage configuration.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Remove your S3 integration. Generated PDFs will use the default CDN storage after deletion.  **Warning:** This action is irreversible. You'll need to reconfigure S3 to use it again.  **No credits consumed:** This is a configuration endpoint.

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

api_instance = TemplateFox::IntegrationsApi.new

begin
  # Delete S3 configuration
  result = api_instance.delete_s3_config
  p result
rescue TemplateFox::ApiError => e
  puts "Error when calling IntegrationsApi->delete_s3_config: #{e}"
end
```

#### Using the delete_s3_config_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<S3SuccessResponse>, Integer, Hash)> delete_s3_config_with_http_info

```ruby
begin
  # Delete S3 configuration
  data, status_code, headers = api_instance.delete_s3_config_with_http_info
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <S3SuccessResponse>
rescue TemplateFox::ApiError => e
  puts "Error when calling IntegrationsApi->delete_s3_config_with_http_info: #{e}"
end
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**S3SuccessResponse**](S3SuccessResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_s3_config

> <S3ConfigResponse> get_s3_config

Get S3 configuration

Get current S3 storage configuration.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Retrieve your S3 integration settings. Secret access key is masked for security.  **Returns 404** if S3 is not configured.  **No credits consumed:** This is a read-only endpoint.

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

api_instance = TemplateFox::IntegrationsApi.new

begin
  # Get S3 configuration
  result = api_instance.get_s3_config
  p result
rescue TemplateFox::ApiError => e
  puts "Error when calling IntegrationsApi->get_s3_config: #{e}"
end
```

#### Using the get_s3_config_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<S3ConfigResponse>, Integer, Hash)> get_s3_config_with_http_info

```ruby
begin
  # Get S3 configuration
  data, status_code, headers = api_instance.get_s3_config_with_http_info
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <S3ConfigResponse>
rescue TemplateFox::ApiError => e
  puts "Error when calling IntegrationsApi->get_s3_config_with_http_info: #{e}"
end
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**S3ConfigResponse**](S3ConfigResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## save_s3_config

> <S3SuccessResponse> save_s3_config(s3_config_request)

Save S3 configuration

Save or update S3-compatible storage configuration.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Configure your S3-compatible storage to receive generated PDFs directly in your own bucket instead of the default CDN.  **Supported providers:** - Amazon S3 - DigitalOcean Spaces - Cloudflare R2 - MinIO - Any S3-compatible storage  **Secret key behavior:** - For new configuration: `secret_access_key` is required - For updates: Omit `secret_access_key` to keep existing value  **No credits consumed:** This is a configuration endpoint.

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

api_instance = TemplateFox::IntegrationsApi.new
s3_config_request = TemplateFox::S3ConfigRequest.new({endpoint_url: 'endpoint_url_example', access_key_id: 'access_key_id_example', bucket_name: 'bucket_name_example'}) # S3ConfigRequest | 

begin
  # Save S3 configuration
  result = api_instance.save_s3_config(s3_config_request)
  p result
rescue TemplateFox::ApiError => e
  puts "Error when calling IntegrationsApi->save_s3_config: #{e}"
end
```

#### Using the save_s3_config_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<S3SuccessResponse>, Integer, Hash)> save_s3_config_with_http_info(s3_config_request)

```ruby
begin
  # Save S3 configuration
  data, status_code, headers = api_instance.save_s3_config_with_http_info(s3_config_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <S3SuccessResponse>
rescue TemplateFox::ApiError => e
  puts "Error when calling IntegrationsApi->save_s3_config_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **s3_config_request** | [**S3ConfigRequest**](S3ConfigRequest.md) |  |  |

### Return type

[**S3SuccessResponse**](S3SuccessResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## test_s3_connection

> <S3TestResponse> test_s3_connection

Test S3 connection

Test S3 connection with stored credentials.  **Authentication:** API Key required (`x-api-key` header) with admin privileges  **Usage:** Verify your S3 configuration is working correctly. The test will: 1. Connect to the endpoint 2. Verify bucket access 3. Check write permissions by uploading a small test file  **Prerequisite:** S3 must be configured first using `POST /v1/integrations/s3`  **No credits consumed:** This is a diagnostic endpoint.

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

api_instance = TemplateFox::IntegrationsApi.new

begin
  # Test S3 connection
  result = api_instance.test_s3_connection
  p result
rescue TemplateFox::ApiError => e
  puts "Error when calling IntegrationsApi->test_s3_connection: #{e}"
end
```

#### Using the test_s3_connection_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<S3TestResponse>, Integer, Hash)> test_s3_connection_with_http_info

```ruby
begin
  # Test S3 connection
  data, status_code, headers = api_instance.test_s3_connection_with_http_info
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <S3TestResponse>
rescue TemplateFox::ApiError => e
  puts "Error when calling IntegrationsApi->test_s3_connection_with_http_info: #{e}"
end
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**S3TestResponse**](S3TestResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

