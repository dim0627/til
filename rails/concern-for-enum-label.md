# Syntax sugar method for labelable enum values.

Like below gems.

* [zmbacker/enum\_help: Help ActiveRecord::Enum feature to work fine with I18n and simple\_form\.](https://github.com/zmbacker/enum_help)
* [brainspec/enumerize: Enumerated attributes with I18n and ActiveRecord/Mongoid support](https://github.com/brainspec/enumerize)

## Implementation

Concern codes.

`app/models/concerns/enum_label.rb`

``` ruby
require 'active_support/concern'

module EnumLabel
  extend ActiveSupport::Concern

  module ClassMethods
    def enum_label(*column_names)
      column_names.each do |column_name|
        define_method("#{column_name}_label") do
          self.class.public_send("#{column_name}_label", public_send(column_name))
        end

        define_singleton_method("#{column_name}_label") do |key|
          ActionController::Base.helpers.t "enums.#{model_name.name.underscore}.#{column_name}.#{key}"
        end
      end
    end
  end
end```

Include to model.

``` ruby
class Article < ApplicationRecord
  include EnumLabel

  enum_label :category
end
```

Label definition.

``` yml
---
ja:
  enums:
    article:
      category:
        release: Release Info
        news: News
        column: Column
```

Call.

``` ruby
Article.category_label(:release)
Article.first.category_label
```
