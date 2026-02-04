# TemplateFox::TemplatesApi

All URIs are relative to *https://api.pdftemplateapi.com*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_template_fields**](TemplatesApi.md#get_template_fields) | **GET** /v1/templates/{template_id}/fields | Get template fields |
| [**list_templates**](TemplatesApi.md#list_templates) | **GET** /v1/templates | List templates |


## get_template_fields

> <Array<TemplateField>> get_template_fields(template_id)

Get template fields

Get the dynamic fields for a template.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Usage:** This endpoint is designed for Zapier Dynamic Fields integration. It returns an array of field definitions that Zapier uses to dynamically generate input forms.  **Response format:** Array of objects compatible with Zapier InputFieldsSchema. Each field has: `key`, `label`, `type`, `required`, and optional `helpText`.  **Field types:** - `string`: Text input (also used for JSON arrays/objects) - `integer`: Integer number - `number`: Decimal number - `boolean`: True/False checkbox  **Arrays and objects:** Complex types are returned as `string` type with a `helpText` showing the expected JSON format.  **No credits consumed:** This is a read-only endpoint.

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

api_instance = TemplateFox::TemplatesApi.new
template_id = 'template_id_example' # String | 

begin
  # Get template fields
  result = api_instance.get_template_fields(template_id)
  p result
rescue TemplateFox::ApiError => e
  puts "Error when calling TemplatesApi->get_template_fields: #{e}"
end
```

#### Using the get_template_fields_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<TemplateField>>, Integer, Hash)> get_template_fields_with_http_info(template_id)

```ruby
begin
  # Get template fields
  data, status_code, headers = api_instance.get_template_fields_with_http_info(template_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<TemplateField>>
rescue TemplateFox::ApiError => e
  puts "Error when calling TemplatesApi->get_template_fields_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **template_id** | **String** |  |  |

### Return type

[**Array&lt;TemplateField&gt;**](TemplateField.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_templates

> <TemplatesListResponse> list_templates

List templates

List all templates for the authenticated user.  **Authentication:** API Key required (`x-api-key` header) or JWT token  **Usage:** This endpoint is designed for no-code tools (Zapier, Make, n8n) to populate template selection dropdowns.  **No credits consumed:** This is a read-only endpoint.

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

api_instance = TemplateFox::TemplatesApi.new

begin
  # List templates
  result = api_instance.list_templates
  p result
rescue TemplateFox::ApiError => e
  puts "Error when calling TemplatesApi->list_templates: #{e}"
end
```

#### Using the list_templates_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<TemplatesListResponse>, Integer, Hash)> list_templates_with_http_info

```ruby
begin
  # List templates
  data, status_code, headers = api_instance.list_templates_with_http_info
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <TemplatesListResponse>
rescue TemplateFox::ApiError => e
  puts "Error when calling TemplatesApi->list_templates_with_http_info: #{e}"
end
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**TemplatesListResponse**](TemplatesListResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

