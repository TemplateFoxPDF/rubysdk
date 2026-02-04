# TemplateFox::TemplateField

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **key** | **String** | Field key/identifier |  |
| **label** | **String** | Human-readable label |  |
| **type** | **String** | Field type: string, integer, number, boolean | [optional][default to &#39;string&#39;] |
| **required** | **Boolean** | Whether the field is required | [optional][default to false] |
| **help_text** | **String** |  | [optional] |

## Example

```ruby
require 'templatefox'

instance = TemplateFox::TemplateField.new(
  key: null,
  label: null,
  type: null,
  required: null,
  help_text: null
)
```

