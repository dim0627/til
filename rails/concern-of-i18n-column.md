# Concern of table have i18n column.

For example.

* articles # table
  * title
  * title_en
  * title_cn
  * title_tw

``` ruby
module Translatable
  extend ActiveSupport::Concern

  module ClassMethods
    def translatable_column(*column_names)
      column_names.each do |column_name|
        define_method("#{column_name}_i18n") do
          if I18n.locale == I18n.default_locale
            public_send(column_name)
          else
            public_send("#{column_name}_#{I18n.locale}").presence || public_send(column_name)
          end
        end
      end
    end
  end
end
```

Including in model.

``` ruby
class Article < ApplicationRecord
  include Translatable

  translatable_column :title
```

Usage.

``` ruby
Article.first.title_i18n
```
