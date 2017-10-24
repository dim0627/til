# How to use foreign key constraint with nullable column.

If there is a two model `blog` and `article`.

``` ruby
has_many :articles, dependent: :nullify
```
