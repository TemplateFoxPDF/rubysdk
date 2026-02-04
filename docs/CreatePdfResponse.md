# TemplateFox::CreatePdfResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **url** | **String** | Signed URL to download the PDF (expires after specified time) |  |
| **filename** | **String** | Filename of the generated PDF |  |
| **credits_remaining** | **Integer** | Remaining credits after this request |  |
| **expires_in** | **Integer** | Seconds until URL expires |  |

## Example

```ruby
require 'templatefox'

instance = TemplateFox::CreatePdfResponse.new(
  url: null,
  filename: null,
  credits_remaining: null,
  expires_in: null
)
```

