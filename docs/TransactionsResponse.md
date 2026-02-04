# TemplateFox::TransactionsResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **transactions** | [**Array&lt;Transaction&gt;**](Transaction.md) |  |  |
| **total** | **Integer** | Total number of transactions |  |
| **limit** | **Integer** | Number of records returned |  |
| **offset** | **Integer** | Number of records skipped |  |

## Example

```ruby
require 'templatefox'

instance = TemplateFox::TransactionsResponse.new(
  transactions: null,
  total: null,
  limit: null,
  offset: null
)
```

