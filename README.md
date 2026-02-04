# TemplateFox Ruby SDK

Official Ruby SDK for [TemplateFox](https://pdftemplateapi.com) - Generate PDFs from HTML templates via API.

[![Gem Version](https://badge.fury.io/rb/templatefox.svg)](https://rubygems.org/gems/templatefox)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Installation

Add to your Gemfile:

```ruby
gem 'templatefox'
```

Then run:

```bash
bundle install
```

Or install directly:

```bash
gem install templatefox
```

## Quick Start

```ruby
require 'templatefox'

# Initialize the client
TemplateFox.configure do |config|
  config.api_key['ApiKeyAuth'] = 'your-api-key'
end

api = TemplateFox::PDFApi.new

# Generate a PDF
request = TemplateFox::CreatePdfRequest.new(
  template_id: 'YOUR_TEMPLATE_ID',
  data: {
    name: 'John Doe',
    invoice_number: 'INV-001',
    total_amount: 150.00
  }
)

begin
  response = api.create_pdf(request)
  puts "PDF URL: #{response.url}"
  puts "Credits remaining: #{response.credits_remaining}"
rescue TemplateFox::ApiError => e
  puts "Error: #{e.message}"
end
```

## Features

- **Template-based PDF generation** - Create templates with dynamic variables, generate PDFs with your data
- **Multiple export options** - Get a signed URL (default) or raw binary PDF
- **S3 integration** - Upload generated PDFs directly to your own S3-compatible storage
- **Ruby 2.7+** - Compatible with Ruby 2.7 and above

## API Methods

### PDF Generation

```ruby
request = TemplateFox::CreatePdfRequest.new(
  template_id: 'TEMPLATE_ID',
  data: { name: 'John Doe' },
  export_type: 'url',        # 'url' or 'binary'
  expiration: 86400,         # URL expiration in seconds
  filename: 'invoice-001'    # Custom filename
)

response = api.create_pdf(request)
```

### Templates

```ruby
templates_api = TemplateFox::TemplatesApi.new

# List all templates
templates = templates_api.list_templates
templates.templates.each do |template|
  puts "#{template.id}: #{template.name}"
end

# Get template fields
fields = templates_api.get_template_fields('TEMPLATE_ID')
fields.each do |field|
  puts "#{field.key}: #{field.type} (required: #{field.required})"
end
```

### Account

```ruby
account_api = TemplateFox::AccountApi.new

# Get account info
account = account_api.get_account
puts "Credits: #{account.credits}"
puts "Email: #{account.email}"

# List transactions
transactions = account_api.list_transactions(limit: 100, offset: 0)
transactions.transactions.each do |tx|
  puts "#{tx.transaction_type}: #{tx.credits} credits"
end
```

### S3 Integration

```ruby
integrations_api = TemplateFox::IntegrationsApi.new

# Save S3 configuration
s3_config = TemplateFox::S3ConfigRequest.new(
  endpoint_url: 'https://s3.amazonaws.com',
  access_key_id: 'AKIAIOSFODNN7EXAMPLE',
  secret_access_key: 'your-secret-key',
  bucket_name: 'my-pdf-bucket',
  default_prefix: 'generated/pdfs/'
)

integrations_api.save_s3_config(s3_config)

# Test connection
test = integrations_api.test_s3_connection
puts "Connection: #{test.success ? 'OK' : 'Failed'}"
```

## Configuration

```ruby
TemplateFox.configure do |config|
  config.host = 'https://api.pdftemplateapi.com'  # Default API URL
  config.api_key['ApiKeyAuth'] = ENV['TEMPLATEFOX_API_KEY']

  # Optional: Enable debugging
  config.debugging = true
end
```

## Error Handling

```ruby
begin
  response = api.create_pdf(request)
rescue TemplateFox::ApiError => e
  case e.code
  when 402
    puts 'Insufficient credits'
  when 403
    puts 'Access denied - check your API key'
  when 404
    puts 'Template not found'
  else
    puts "Error: #{e.message}"
  end
end
```

## Rails Integration

```ruby
# config/initializers/templatefox.rb
TemplateFox.configure do |config|
  config.api_key['ApiKeyAuth'] = Rails.application.credentials.templatefox_api_key
end

# app/services/pdf_generator.rb
class PdfGenerator
  def initialize
    @api = TemplateFox::PDFApi.new
  end

  def generate_invoice(invoice)
    request = TemplateFox::CreatePdfRequest.new(
      template_id: ENV['INVOICE_TEMPLATE_ID'],
      data: invoice.to_template_data
    )
    @api.create_pdf(request)
  end
end
```

## Documentation

- [API Documentation](https://pdftemplateapi.com/docs)
- [Swagger UI](https://api.pdftemplateapi.com/docs)
- [Dashboard](https://pdftemplateapi.com/dashboard)

## Support

- Email: support@pdftemplateapi.com
- Issues: [GitHub Issues](https://github.com/TemplateFoxPDF/rubysdk/issues)

## License

MIT License - see [LICENSE](LICENSE) for details.
