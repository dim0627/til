# How to solve shadowing heroku domain when using custom domain.

## Structure

Using custom domain.

```
Client -> CloudFlare(not orange cloud, strict ssl) -> Heroku
```

## Problem

There is two domain.

* [your custom domain]
* [app name].herokuapp.com

This is not good for SEO(duplicate content).
But could not remove Heroku default domain it's using from CloudFlare strict ssl.

## Solution

`config/environments/production.rb`

``` ruby
Rails.application.configure do
  config.action_controller.default_url_options = {
    protocol: Settings.http.protocol,
    host: Settings.http.host
  }
end

set_meta_taags canonical: url_for(only_path: false)
```
