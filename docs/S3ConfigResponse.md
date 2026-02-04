# TemplateFox::S3ConfigResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **configured** | **Boolean** | Whether S3 is configured |  |
| **endpoint_url** | **String** | S3-compatible endpoint URL |  |
| **access_key_id** | **String** | Access key ID |  |
| **secret_access_key_masked** | **String** | Masked secret access key (shows first 4 and last 4 characters) |  |
| **bucket_name** | **String** | S3 bucket name |  |
| **default_prefix** | **String** | Default path prefix for uploads |  |

## Example

```ruby
require 'templatefox'

instance = TemplateFox::S3ConfigResponse.new(
  configured: null,
  endpoint_url: null,
  access_key_id: null,
  secret_access_key_masked: null,
  bucket_name: null,
  default_prefix: null
)
```

