# TemplateFox::S3ConfigRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **endpoint_url** | **String** | S3-compatible endpoint URL. Must start with https:// |  |
| **access_key_id** | **String** | Access key ID for S3 authentication |  |
| **secret_access_key** | **String** |  | [optional] |
| **bucket_name** | **String** | S3 bucket name. Must follow S3 naming conventions (lowercase, no underscores) |  |
| **default_prefix** | **String** | Default path prefix for uploaded files. Can include slashes for folder structure | [optional][default to &#39;&#39;] |

## Example

```ruby
require 'templatefox'

instance = TemplateFox::S3ConfigRequest.new(
  endpoint_url: null,
  access_key_id: null,
  secret_access_key: null,
  bucket_name: null,
  default_prefix: null
)
```

