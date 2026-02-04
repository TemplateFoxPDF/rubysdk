# TemplateFox::CreatePdfRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **template_id** | **String** | **Required.** Template short ID (12 characters) |  |
| **data** | **Hash&lt;String, Object&gt;** | **Required.** Key-value data to render in the template. Keys must match template variables. |  |
| **export_type** | [**ExportType**](ExportType.md) | Export format: &#x60;url&#x60; uploads to CDN and returns URL, &#x60;binary&#x60; returns raw PDF bytes | [optional] |
| **expiration** | **Integer** | URL expiration in seconds. Min: 60 (1 min), Max: 604800 (7 days). Only applies to &#x60;url&#x60; export type. | [optional][default to 86400] |
| **filename** | **String** |  | [optional] |
| **store_s3** | **Boolean** | Upload to your configured S3 bucket instead of CDN | [optional][default to false] |
| **s3_filepath** | **String** |  | [optional] |
| **s3_bucket** | **String** |  | [optional] |

## Example

```ruby
require 'templatefox'

instance = TemplateFox::CreatePdfRequest.new(
  template_id: null,
  data: null,
  export_type: null,
  expiration: null,
  filename: null,
  store_s3: null,
  s3_filepath: null,
  s3_bucket: null
)
```

