# Occured `syntax error, unexpected '}', expecting keyword_end`.

Below code is broken.

``` rb
define_method :some_method_name { "asdf" }
```

Curly brace block needs surrounded `()` at arguments.

``` rb
define_method(:some_method_name) { "asdf" }
```

[Bug \#13898: Block parsing regression \- Ruby trunk \- Ruby Issue Tracking System](https://bugs.ruby-lang.org/issues/13898)
[Bug \#13939: Ruby 2\.4\.2 has issue supporting Seattle\.rb style for define\_method \- Ruby trunk \- Ruby Issue Tracking System](https://bugs.ruby-lang.org/issues/13939)
[Seattle\.rb style no longer valid in Ruby 2\.4\.2 when curly braces are used\. · Issue \#4793 · bbatsov/rubocop](https://github.com/bbatsov/rubocop/issues/4793)
