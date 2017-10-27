# How to use Fontawesome on Rails with AWS CloudFront CDN

Install rack-cors.

``` gemfile
gem 'rack-cors', require: 'rack/cors'
```

Or using `ActionDispatch::Static`.

## Make `config/initializers/cors.rb`

For example.

```
Rails.application.config.middleware.insert_before 0, Rack::Cors do
  allow do
    origins Settings.http.host # Your domain.
    resource '/packs/**/*', headers: :any, methods: [:get, :head]
  end
end
```

I think should have more strict settings.

## Thru Origin headers via CloudFront

```
CloudFront -> Behaviors -> Cache Based on Selected Request Headers -> Whitelist
```

Add `Origin`.
