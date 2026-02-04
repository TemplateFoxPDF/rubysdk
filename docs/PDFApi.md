# TemplateFox::PDFApi

All URIs are relative to *https://api.pdftemplateapi.com*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_pdf**](PDFApi.md#create_pdf) | **POST** /v1/pdf/create | Generate PDF from template |


## create_pdf

> <CreatePdfResponse> create_pdf(create_pdf_request)

Generate PDF from template

Generate a PDF from a saved template with dynamic data.  **Authentication:** API Key required (`x-api-key` header)  ## Request Body  | Field | Type | Required | Description | |-------|------|----------|-------------| | `template_id` | string | ✅ Yes | Template short ID (12 characters) | | `data` | object | ✅ Yes | Key-value data to render in template | | `export_type` | string | No | `url` (default) or `binary` | | `expiration` | integer | No | URL expiration in seconds (60-604800, default: 86400) |  ## Export Types - `url` (default): PDF is uploaded to CDN, returns JSON with URL - `binary`: Returns raw PDF bytes directly  **Credits:** 1 credit deducted per successful generation.

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

api_instance = TemplateFox::PDFApi.new
create_pdf_request = TemplateFox::CreatePdfRequest.new({template_id: 'template_id_example', data: { key: 3.56}}) # CreatePdfRequest | 

begin
  # Generate PDF from template
  result = api_instance.create_pdf(create_pdf_request)
  p result
rescue TemplateFox::ApiError => e
  puts "Error when calling PDFApi->create_pdf: #{e}"
end
```

#### Using the create_pdf_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CreatePdfResponse>, Integer, Hash)> create_pdf_with_http_info(create_pdf_request)

```ruby
begin
  # Generate PDF from template
  data, status_code, headers = api_instance.create_pdf_with_http_info(create_pdf_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CreatePdfResponse>
rescue TemplateFox::ApiError => e
  puts "Error when calling PDFApi->create_pdf_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **create_pdf_request** | [**CreatePdfRequest**](CreatePdfRequest.md) |  |  |

### Return type

[**CreatePdfResponse**](CreatePdfResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json, application/pdf

