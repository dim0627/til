# How to setting cache-control from rails5 public_file_server

`config/environments/production.rb`

```
config.public_file_server.headers = {
  'Cache-Control' => "max-age=#{1.year.seconds.to_i}"
}
```

`Cache-Control` should setting by web server(e.g. nginx) possible.

But could not set `Cache-Control` header environments(e.g. Heroku) use this setting.

## Expires or Cache-Control

Google says **Set either one**.

And recommends `Cache-Control`.
