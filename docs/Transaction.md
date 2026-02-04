# TemplateFox::Transaction

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **transaction_ref** | **String** | Unique transaction reference (UUID) |  |
| **transaction_type** | **String** | Transaction type: PDFGEN, PURCHASE, REFUND, BONUS |  |
| **template_id** | **String** |  | [optional] |
| **exec_tm** | **Integer** |  | [optional] |
| **credits** | **Integer** | Credits consumed (positive) or added (negative) |  |
| **created_at** | **String** | ISO 8601 timestamp |  |

## Example

```ruby
require 'templatefox'

instance = TemplateFox::Transaction.new(
  transaction_ref: null,
  transaction_type: null,
  template_id: null,
  exec_tm: null,
  credits: null,
  created_at: null
)
```

