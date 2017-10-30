# How to use gzip compress to html response

Conclusion.

``` gemfile
group :production do
  gem 'heroku-deflater'
end
```

## Why not Rack::Deflater?

`Rack::Deflater` is rack middleware for gzip compress.
But this gem is compressing binary file such as image too.

Most good solution is mime type based compress.

[Configuration options for Rack::Deflate by jakubpawlowicz · Pull Request \#457 · rack/rack](https://github.com/rack/rack/pull/457)

`heroku-deflater` is configured by based on whitelist.

```
    WHITELIST = [
      %r{^text/},
      'application/javascript',
      %r{^application/.*?json},
      %r{^application/.*?xml},
      'application/x-font-ttf',
      'font/opentype',
      'image/svg+xml'
    ].freeze
```

[heroku\-deflater/skip\_binary\.rb at master · romanbsd/heroku\-deflater](https://github.com/romanbsd/heroku-deflater/blob/master/lib/heroku-deflater/skip_binary.rb)
